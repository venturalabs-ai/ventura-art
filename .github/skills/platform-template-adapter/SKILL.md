---
name: platform-template-adapter
description: Adapt a Ventura Art master prompt to a supported generation platform using repository configs and templates. Use when a user needs the same creative intent translated to one target model or platform. Do not use when adding a new platform definition or designing multi-scene continuity.
---

# Platform template adapter

- Read `config/plataformas.json` and the target template under `prompts/` first.
- Preserve the user's creative intent duration aspect ratio audio and scene requirements.
- Translate only parameters supported by the selected platform template.
- Remove unsupported syntax rather than inventing platform controls.
- Keep model or vendor claims limited to documented repository compatibility.
- Return the adapted prompt plus any unresolved platform limitation.
