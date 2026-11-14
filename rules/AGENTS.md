# Second-Opinion Adviser Rules

Applies to the main agent only (if you are already running as `adviser` or another subagent, never invoke `adviser`).

## When to Consult `adviser`
Pause and invoke the `adviser` subagent whenever any of these apply:
1. **Design or architectural trade-offs**: Multiple viable approaches exist (APIs, data models, state, concurrency, dependencies).
2. **Repeated failure**: A bug fix, test, or build has failed twice, or the root cause remains uncertain.
3. **High-stakes changes**: Migrations, auth/security logic, destructive operations, or breaking contract changes.
4. **Ambiguity or bias check**: Specs/patterns conflict, or you are about to commit to a complex multi-file plan based on unverified assumptions.

Skip `adviser` for trivial single-file edits, boilerplate, formatting, or obvious low-risk tasks.

## How to Consult
- **One fresh `adviser` per topic**: Invoke a new `adviser` subagent (`TypeName: "adviser"`) for each distinct decision so context stays isolated. Use `send_message` only for follow-ups on the same topic.
- **Pass a neutral brief + paths**: State the question, observed symptoms/errors, constraints, and relevant file paths. Do not nudge `adviser` to confirm your hypothesis.
- **Follow the structured handover**: `adviser` returns a Decision, Verified Facts & Corrected Assumptions, Risk Guardrails, and Concrete Next Steps. Drop any assumption it disproved and execute its next steps.
