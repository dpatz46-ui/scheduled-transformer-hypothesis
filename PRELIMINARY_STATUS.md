# Preliminary empirical status

This document distinguishes what is presently proposed, what preliminary work indicates, and what remains to be established by the confirmatory program.

## Proposed

The **Scheduled Transformer hypothesis** proposes that pre-normalized transformer computation proceeds through a reproducible, ordered sequence of depth-indexed state regimes rather than through exchangeable repetitions of an otherwise homogeneous transformation.

The primary operational observable is token-level residual radius:

\[
r_{i,p,l}=\|x_{i,p,l}\|,\qquad y_{i,p,l}=\log r_{i,p,l}.
\]

The proposed empirical object is the full ordered sequence of layer-conditioned distributions and transitions, not merely their mean growth.

## Preliminary support

Primary activation analyses conducted prior to this release strongly indicate:

- reproducible depth dependence in residual-state distributions;
- layer-specific changes in radial distribution width and shape;
- repeated radial contraction and expansion across depth;
- inherited-state-dependent radial transitions inconsistent with a simple independent-increment picture;
- persistence and reorganization of relative state positions across depth;
- candidate context-conditioned departures from the dominant schedule.

These findings motivate the hypothesis and the confirmatory design.

## Not yet claimed as established

This release does **not** claim that the following have been comprehensively established:

- universality across transformer architectures;
- a unique causal mechanism producing the schedule;
- a general functional role for radius itself;
- a universal context-conditioned sub-schedule phenomenon;
- a relationship between the schedule and catastrophic forgetting, circuit formation, or broader intelligence theory;
- optimality or intentional regulation of the schedule.

These are later empirical or theoretical questions.

## Prior-work boundary

Depth-dependent residual norm growth and per-layer norm distributions have prior art. The present proposal does not claim those observations as novel in isolation.

The distinctive proposal is to treat the **ordered sequence of layer-conditioned state regimes and transitions** as the primary computational object and to test its distributional structure, transition dynamics, reorganization, and context-conditioned departures directly.
