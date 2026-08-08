---
name: prompt-compile
description: Convert a proven Ventura Art prompt workflow into a reusable repository template with stable variables and replay instructions. Use when a prompt has succeeded repeatedly and should stop being rebuilt from scratch. Do not use when the workflow is in first-time exploration or requirements are still changing rapidly.
---

# Prompt compile

- Start from a prompt workflow that has already produced an acceptable result.
- Separate stable instructions from user-supplied variables.
- Keep platform-specific controls in the corresponding platform template.
- Remove one-off context that does not affect repeatability.
- Define required inputs defaults and failure conditions.
- Add one worked example using non-sensitive placeholder values.
- Place the compiled artifact in the existing prompt or configuration structure rather than creating a parallel format.
