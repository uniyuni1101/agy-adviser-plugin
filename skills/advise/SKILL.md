---
name: advise
description: >-
  Consult the independent `adviser` subagent in an isolated context for an unbiased second opinion on design trade-offs, bugs, risky changes, or plans. Use when the user invokes /advise or asks for a second opinion or review.
---

# Consult the Adviser (`/advise`)

1. **Frame a neutral brief**: State the concrete question or decision, relevant file paths, observed errors/constraints, and any options under consideration without nudging toward a preferred answer.
2. **Invoke `adviser`**: Launch a fresh `adviser` subagent (`TypeName: "adviser"`) with the brief and wait for its response before making edits. (Use `send_message` only if following up on the exact same consultation.)
3. **Apply or report**: Share the adviser's key conclusions and any corrected assumptions with the user, and adjust your plan accordingly.
