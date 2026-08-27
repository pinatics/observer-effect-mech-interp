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

Status: In progress

### Goal

Establish a reproducible environment in which we can:

- run the model,
- inspect tokens and logits,
- capture internal activations,
- identify layer and token positions,
- and verify our instrumentation with sanity checks.

### Experiment Log

Date:

Model:

GPU:

Prompt:

Layer:

Token position:

Activation shape:

Output:

Observations:

Unexpected results:

Interpretation:

Next question:
