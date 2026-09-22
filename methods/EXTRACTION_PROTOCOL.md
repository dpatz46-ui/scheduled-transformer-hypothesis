# Residual-state extraction protocol

## Primary reference model

Initial clean reference:

`meta-llama/Llama-3.2-3B` (base checkpoint)

Validated runtime configuration to date:

- 28 decoder blocks;
- hidden size 3072;
- FP16 on NVIDIA Tesla T4;
- eager attention implementation;
- no quantization;
- deterministic / greedy generation for generation-bearing tasks.

The base checkpoint remains the principal architectural object. Instruction-tuned variants may be used later as task-success replications where instruction-following behavior matters.

## Fundamental residual decomposition

For block \(l\), acquire:

\[
x_l^{pre}
\]

residual stream entering the block;

\[
\Delta_l^A
\]

attention write after output projection and immediately before residual addition;

\[
x_l^{mid}=x_l^{pre}+\Delta_l^A;
\]

\[
\Delta_l^M
\]

MLP write immediately before residual addition; and

\[
x_l^{out}=x_l^{mid}+\Delta_l^M.
\]

Adjacent blocks should satisfy

\[
x_l^{out}=x_{l+1}^{pre}.
\]

For a 28-block model, preserve 29 residual boundaries.

## Reconstruction validation

Before any large-scale harvest, verify:

\[
x_l^{mid}\approx x_l^{pre}+\Delta_l^A
\]

and

\[
x_l^{out}\approx x_l^{mid}+\Delta_l^M.
\]

Also verify exact or effectively exact continuity between adjacent captured residual boundaries.

The extraction pipeline should stop before a full run if these checks fail.

A prior smoke test on Llama 3.2 3B produced maximum branch reconstruction relative errors on the order of \(10^{-4}\), with exact captured continuity across adjacent block boundaries. This is consistent with FP16 arithmetic and supports the chosen hook locations.

## Token coverage

Preserve all token positions:

- prefill / input tokens;
- generated tokens;
- token IDs;
- decoded token strings;
- absolute positions;
- prefill/generated flags;
- special-token status where useful;
- task-specific token-role annotations.

Position zero / BOS should be retained and explicitly flagged rather than silently removed.

For generation-bearing prompts:

1. generate deterministically;
2. concatenate prompt and generated sequence;
3. run one full causal forward pass over the completed sequence;
4. capture the trajectory for every token.

Because causal masking prevents later tokens from changing earlier-token states, this yields a clean complete trajectory for both prefill and generated positions.

## Core stored tensors

Minimum vector archive:

\[
x_l,\quad \Delta_l^A,\quad x_l^{mid},\quad \Delta_l^M,\quad x_{l+1}.
\]

For Llama 3.2 3B this maps naturally to:

- `residual_stream`: `[29, tokens, 3072]`
- `attn_write`: `[28, tokens, 3072]`
- `post_attn_residual`: `[28, tokens, 3072]`
- `mlp_write`: `[28, tokens, 3072]`

Store FP16 tensors when FP16 is the execution dtype. Preserve inexpensive scalar summaries alongside them for convenience, while treating full vectors as authoritative.

## Normalization data

Where practical, also preserve enough information to reconstruct pre-RMSNorm behavior:

\[
q=x/RMS(x),\qquad y=\gamma\odot q.
\]

Desirable measurements include:

- RMS denominator;
- normalized state \(q\);
- gamma-scaled normalized state \(y\);
- gamma vectors once per checkpoint;
- final normalization state and logits where feasible.

These are broader than the narrow first-paper claim but reduce the need for later re-harvesting.

## Provenance metadata

Every run should preserve:

- exact checkpoint ID and revision/hash where obtainable;
- tokenizer and tokenizer version;
- library versions;
- execution dtype;
- attention implementation;
- exact prompt text;
- exact token IDs;
- special-token policy;
- generation parameters;
- task/token-role annotations;
- hook locations and tensor shapes;
- architecture boundary definitions;
- random seed;
- extraction-code version/hash.
