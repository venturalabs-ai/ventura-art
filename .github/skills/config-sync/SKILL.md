---
name: config-sync
description: Keep Ventura Art platform system and prompt templates consistent when supported capabilities change. Use when adding editing or deprecating entries in repository configs or model templates. Do not use when adapting one user prompt without changing repository definitions.
---

# Config sync

- Inspect `config/plataformas.json` `config/sistemas.json` and matching files under `prompts/`.
- Change the canonical capability definition first.
- Update only templates affected by that capability.
- Remove stale references when a platform or model is deprecated.
- Keep unsupported controls out of templates.
- Check README examples and workflow steps for drift.
- Validate JSON syntax and repository checks before finishing.
