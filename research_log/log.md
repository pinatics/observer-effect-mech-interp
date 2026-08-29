# Observer Effect — Research Log

## Research Question

Does prompting a language model to attend to or report its own internal state alter its internal representations and downstream behavior?

If a change occurs, is it specifically associated with introspection, or can it be explained by other factors introduced by the prompt?

## Initial Experimental Conditions

1. Control
2. Neutral
3. Silent
4. Report

These are the initial diagnostic conditions, not the final experimental set. Additional controls will be added based on the observed results.

## Phase 0

Status: Complete

### Current hypothesis

Introspection-prompted conditions may alter internal model representations and downstream behavior.

### Important caution

A difference in activations does not by itself establish that introspection caused the behavioral change.

Alternative explanations and causal interventions will need to be tested.

---

## Phase 1

Status: Complete

### Goal

Establish a reproducible environment in which we can:

- run the model,
- inspect tokens and logits,
- capture internal activations,
- identify layer and token positions,
- and verify our instrumentation with sanity checks.

### Experiment Log

Date: 2026-08-28

Model: Qwen/Qwen3-4B

GPU: NVIDIA RTX PRO 6000 Blackwell Server Edition

Prompt: The Eiffel Tower is in

Layer: 18

Token position: Final token position (-1), token = "Ġin"

Activation shape: [1, 7, 2560]; selected final-token activation shape = [2560]

Output: Top predicted next token = " Paris" (~79.78% probability)

Observations:
- Input shape was [1, 7].
- Forward-pass logits shape was [1, 7, 151936].
- Layer 18 activation was successfully captured with a forward hook.
- Layer 18 activation shape was [1, 7, 2560].
- Final-token activation L2 norm was approximately 50.4057.
- The no-op hook produced exactly the same logits as the original forward pass.
- Maximum absolute logit difference was 0.0.
- torch.allclose returned True.
- Original and hooked runs both predicted " Paris" as the top next token.

Unexpected results:
- Tokenizer length (151669), tokenizer vocab_size (151643), and model vocab_size (151936) were different. The reason has not yet been investigated.

Interpretation:
- The model forward pass and activation-capture pipeline are working.
- Internal representations can be observed at a specified transformer layer and token position.
- The observational hook did not perturb the model output in this sanity check.
- Activation differences alone would not establish a causal mechanism; causal interventions will be required later.

Next question:
Can the validated activation-capture pipeline detect systematic internal-state differences between the Control, Neutral, Silent, and Report experimental conditions?

## Phase 2 — Behavioral Exploration

Status: Complete

### What was tested

Exploratory binary decision tasks were evaluated under four prompting conditions:

- Control
- Neutral
- Silent self-directed attention
- Explicit Report

Qwen3-4B was run deterministically with `do_sample=False` and `enable_thinking=False`.

### Main behavioral observation

Across the three exploratory tasks, the final discrete A/B choice did not change across conditions.

However, next-token A-vs-B logit margins revealed differences that were not visible from the final answer alone.

In two of the three tasks, the Silent condition reduced absolute preference strength relative to both Control and Neutral.

### Candidate hypothesis for Phase 3

Self-directed attention may weaken an already strong response tendency, moving the model's A-vs-B next-token logit margin toward the decision boundary without necessarily changing the final discrete choice.

This is an exploratory hypothesis, not a causal conclusion.

Alternative explanations including prompt wording, prompt length, additional instruction effects, token-position differences, and attention changes remain unresolved and require matched controls.

### Next step

Phase 3 will lock the experimental protocol, prompt set, metrics, and matched controls before mechanistic activation analysis.
