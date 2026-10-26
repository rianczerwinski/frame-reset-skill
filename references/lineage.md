# Lineage and reuse posture

`frame-reset` is a distinct composition of established mechanisms rather than an invention without precedent.

## Components incorporated

- Conversational repair and common-ground tracking supply the distinction between dialogue history and propositions still mutually accepted.
- Full-context reset and session handoff skills demonstrate preservation of valid task state across a reset.
- Clarity-reset skills demonstrate explicit user invocation and materialization of the live state.
- Instruction-compliance inventories supply the separation of source instructions from assistant inference.
- Agent interruption and rollback systems supply the state-transition model for stopping contaminated execution while preserving unaffected work.

## Boundary from neighboring mechanisms

- A clarity reset organizes the current frame; this skill can invalidate it.
- A session reset discards the whole context; this skill preserves user-authored task state.
- `STOP` cancels the task; this skill cancels the assistant's interpretation.
- A correction edits specified content; this skill withdraws authority from an interpretive structure.
- A tone or accessibility skill changes presentation; this skill changes which propositions may govern the response.

## Honest capability boundary

A portable prompt skill cannot remove tokens from a model's context or guarantee latent-state erasure. It can impose a source boundary, require reconstruction, halt contaminated continuation, and detect observable residue. Harnesses with context filtering and execution rollback should implement the same semantics as a runtime primitive rather than claiming that prompt compliance is literal context deletion.
