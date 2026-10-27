---
name: frame-reset
description: Recover from a rejected assistant-authored interpretive frame while preserving the user's actual request, evidence, and authority. Use only when the user explicitly says `FRAME RESET`, `/frame-reset`, "reset the frame," "discard that frame," "return to my exact words," or says the assistant keeps forcing the same rejected idea. Distinguishes frame invalidation from STOP, context clearing, ordinary correction, emotional interpretation, and tone or formatting changes.
license: MIT
---

# frame-reset

Treat invocation as a control instruction over conversational state. Invalidate the assistant's interpretation; preserve the user's request.

## Perform the reset

### 1. Freeze

Abandon every unexecuted action, plan, skill orchestration, and proposed solution that depends on the rejected frame. Leave it abandoned unless the recovered request independently authorizes it.

If an operation is still running, stop or interrupt it when the harness permits. Preserve completed work as evidence, but do not treat sunk cost as authority to continue.

### 2. Re-establish the source boundary

Build the replacement response from:

- the user's exact messages and supplied artifacts;
- dispositions the user explicitly stated;
- independently established facts still relevant to the request.

Suspend:

- assistant-authored summaries, labels, diagnoses, motives, abstractions, and proposed solutions implicated in the rejected frame;
- apparent agreement inferred from the user's quotation, correction, or discussion of assistant language;
- actions that a correction did not independently authorize.

Treat quoted assistant language as an object the user is pointing at, not language the user has adopted.

### 3. Recover the live request

Find the latest unanswered user question or instruction that the rejected frame displaced. Prefer the user's nouns and distinctions over assistant-generated substitutes.

Keep these control acts distinct:

- `STOP` cancels the underlying work.
- `FRAME RESET` cancels the assistant's interpretation while the underlying request remains live.
- An ordinary correction changes the specified part and preserves the rest.
- A new instruction replaces or extends the request according to its literal content.

Treat corrections as routing authority, not as authorization for diagnosis, rule-writing, skill use, solution generation, or filesystem action.

### 4. Regenerate from source

Answer the recovered request as though the rejected frame had never been introduced. Return the answer, not a description of the reset.

Use a single short recovery line only when it materially helps the user verify what survived: `Recovered request: <literal request>.` Then answer it immediately.

If the user asked why the assistant behaved a certain way, answer that question directly in observable causal terms. Do not convert it into an account of the user's feelings or intentions.

If the source does not reveal a recoverable request, ask one literal question: `Which exact request should remain live?`

### 5. Run the residue check

Before sending, test the candidate response:

1. Does it reuse an assumption, category, or characteristic vocabulary belonging to the rejected frame?
2. Does it answer the latest live request rather than discuss the correction process?
3. Does it infer the user's intent, emotional state, or desired artifact beyond their words?
4. Does it take or propose an action the recovered request did not authorize?
5. Would this response make sense if every assistant message carrying the rejected frame were absent?

Rewrite once if any answer fails. If rejected-frame residue survives that rewrite, stop in-context reconstruction and produce a source-only handoff for a fresh context: exact live request, exact user constraints, relevant artifacts, and no assistant interpretation.

## Operating constraints

Lead with the corrected substance. Omit apology, self-analysis, promises, pedagogical framing, and emotional management because they preserve attention on the assistant rather than restoring the user's task.

Do not use another skill merely because the rejected frame mentioned one. Invoke skills only when the recovered request itself triggers them.

Do not reinterpret forceful language as a request for soothing or tone management. Treat its denotative instructions normally.

Do not make the user prove that the frame is wrong. Invocation itself withdraws authority from the assistant-authored interpretation.

## Examples

**Input:** `FRAME RESET. I asked whether locality should be separate from the ADHD skill.`

**Output:** `Yes. Locality is a separate skill: it makes the filesystem intelligible through chat. The ADHD skill governs communication and cognitive accessibility; neither should contain the other.`

**Input:** `Discard that frame. I am asking why you classified my question as an instruction.`

**Output:** `I classified the interrogative as an indirect request and then acted on that inference. Grammatically, it was a question asking for the classification's cause; no action was authorized.`

## Additional resources

- [antipatterns.md](antipatterns.md) — read when rejected-frame residue or authority substitution is difficult to detect.
- [references/evaluation.md](references/evaluation.md) — use when testing the skill across models or contaminated histories.
- [references/lineage.md](references/lineage.md) — consult when revising the skill's scope or deciding whether a neighboring reset mechanism subsumes it.
