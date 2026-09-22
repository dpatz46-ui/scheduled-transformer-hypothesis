# Planned confirmatory experiment

## Objective

Test whether modern pre-normalized transformer models exhibit reproducible **depth-indexed state regimes** that are richer than simple monotonic residual-norm growth.

The confirmatory program is designed to acquire broadly while claiming narrowly.

## Primary observable

For prompt/example \(i\), token position \(p\), and residual depth \(l\):

\[
r_{i,p,l}=\|x_{i,p,l}\|,
\]

\[
y_{i,p,l}=\log r_{i,p,l}.
\]

Primary analyses characterize the ordered sequence of layer-conditioned distributions rather than collapsing immediately to a single prompt-level trajectory.

## Dominant depth schedule

Estimate, by depth:

\[
\mu_l=E[y_l],\qquad \sigma_l=SD(y_l),
\]

along with distributional shape, overlap, contraction/expansion, and persistence/reorganization.

The existence of a dominant growth trend is not sufficient evidence for the novel claim. Analyses should therefore explicitly distinguish prior-art mean radial growth from additional schedule structure.

## Transition dynamics

Define

\[
d_l=y_{l+1}-y_l.
\]

Then

\[
\operatorname{Var}(y_{l+1})
=
\operatorname{Var}(y_l)
+
\operatorname{Var}(d_l)
+
2\operatorname{Cov}(y_l,d_l).
\]

A contractive transition satisfies

\[
\operatorname{Var}(y_{l+1})<\operatorname{Var}(y_l),
\]

which requires

\[
\operatorname{Cov}(y_l,d_l)<-\frac12\operatorname{Var}(d_l).
\]

This provides a concrete test for inherited-state-dependent radial transition structure rather than independent accumulation.

## Context-conditioned sub-schedules

A sub-schedule should not be defined by a mere slope difference.

One operational residualization is

\[
e_{i,l}=y_{i,l}-\mu_l-\alpha_i-\beta_i l.
\]

Candidate sub-schedules should show a structured contiguous excursion across depth, persistence over multiple layers, and potentially later reconvergence.

## Prompt regime

Current frozen design target:

### Suite 1 — dominant schedule and replication

260 prompts total:

- 100 recovered matched prompts from the prior Manson activation suite;
- 160 newly controlled prompts covering relational QA, paraphrase, coherence/nonsense controls, token-position/length effects, and output-length effects.

### Suite 2 — targeted departures

256 prompts total, including:

- flexible-generalization factorials;
- published arithmetic items;
- matched compact symbolic arithmetic;
- matched natural-language arithmetic;
- two-hop tasks;
- mixed-operation chains;
- explicit legacy arithmetic probes.

Principal planned harvest: **516 prompts**.

Additional H&T replication prompts and circuit-mediation experiments should remain separate from the main count and primary paper unless later evidence strongly justifies inclusion.

## Task success

For tasks with known answers, store both task identity and behavioral success:

- expected answer;
- generated answer;
- correctness;
- answer-prediction position(s).

This permits explicit separation between

\[
\text{task-evoked trajectory}
\]

and

\[
\text{successful task execution}.
\]

## Model sequence

1. Official base `meta-llama/Llama-3.2-3B` as the first clean modern reference.
2. Instruction-tuned counterpart where useful for successful task execution comparisons.
3. Additional architecture/model-family replications after the primary result is established.

## Falsification pressure

The hypothesis would be weakened if, after controlling for token position, lexical composition, prompt family, and simple mean growth, layer-conditioned radial distributions showed no reproducible regime structure; if apparent contractions/expansions failed replication; or if candidate context-conditioned departures reduced to smooth prompt-specific offsets/slopes or sampling noise.

A useful theory should survive such controls rather than define every depth effect as confirming evidence.
