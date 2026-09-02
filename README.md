# Observer Effect in Language Models

## Research Question

Does directing a language model's attention toward its own current response tendency alter its internal representations and downstream behavior?

If a change occurs, can it be specifically associated with the self-directed manipulation, or can it be explained by simpler alternatives such as prompt wording, additional instructions, attention redistribution, or explicit reporting?

## Why This Question Matters

I became interested in a simple problem: when we ask a language model to inspect or report its own response tendency, we often treat the answer as if we are simply measuring something that was already there.

But the instruction to inspect that tendency is itself an input to the model. It could change the computation we are trying to observe.

That raises the mechanistic question behind this project:

**When a model is asked to attend to its own current response tendency, where does its internal computation begin to change, and do those changes contribute to the final response?**

I do not want to stop at showing that two prompts produce different outputs or activations. Different prompts naturally do that. I want to test whether self-directed attention produces a measurable behavioral change, locate where any corresponding internal change appears, and then test whether that internal change plays a causal role in the behavior.

> **We may not be passively observing a model's response tendency. Asking the model to observe it may itself change the computation.**

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
- [x] Phase 1 — Environment, model inference, and activation access
- [x] Phase 2 — Behavioral experiments
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
