# Observer Effect in Language Models

## Research Question

Does prompting a language model to attend to or report its own internal state alter its internal representations and downstream behavior?

If a change occurs, is it specifically associated with introspection, or can it be explained by other factors introduced by the prompting procedure?

## Motivation

Asking a language model to inspect or report its own internal state may itself alter the computation being measured.

This project investigates this potential observer effect using behavioral comparisons, internal activation measurements, controlled interventions, and falsification tests.

## Initial Experimental Conditions

The first diagnostic experiments compare four conditions:

1. **Control** — normal response with no additional introspective instruction.
2. **Neutral** — an additional instruction unrelated to introspection.
3. **Silent** — attend to the model's current response tendency without explicitly reporting it.
4. **Report** — attend to and explicitly report the current response tendency.

These conditions are an initial diagnostic set rather than a fixed final experiment set. Additional controls will be introduced based on observed results.

## Research Strategy

Behavioral difference
→ activation difference
→ localization
→ causal intervention
→ falsification / controls
→ interpretation

An activation difference alone will not be treated as evidence of a causal mechanism.

## Current Status

- [x] Phase 0 — Research question and experimental framing
- [ ] Phase 1 — Environment, model inference, and activation access
- [ ] Phase 2 — Behavioral experiments
- [ ] Phase 3 — Experimental protocol
- [ ] Phase 4 — Activation analysis
- [ ] Phase 5 — Causal interventions
- [ ] Phase 6 — Falsification and controls
- [ ] Phase 7 — Analysis
- [ ] Phase 8 — Research distillation

## Tools

Planned stack:

- PyTorch
- Hugging Face Transformers
- nnsight
- einops
- TransformerLens
- RunPod
- Jupyter
