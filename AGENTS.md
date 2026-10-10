# AGENTS.md

Instructions for AI coding agents working in or with `@three-ws/viewer-presets`.

## What this is

Tuned visual presets for three.ws avatar viewers — light rigs, floor reflection, bloom, and PBR material presets (chrome/gold/glass/…) with seeded variants.

## Use it

```bash
npm install @three-ws/viewer-presets
```

Full API reference: [README.md](README.md). Machine-readable summary: [llms.txt](llms.txt). Full text: [llms-full.txt](llms-full.txt).

## Work on it

- Node 20 or newer, ESM only.
- Run the tests with `npm test` before proposing a change.
- Keep runtime dependencies at their current count. Prefer a well-maintained library over new hand-rolled code, and say why in the pull request.
- No mocks, placeholders or TODO comments in committed code.
- Do not use em-dashes or en-dashes in code, comments or docs.

## Source of truth

This repository is exported from https://github.com/nirholas/three.ws/tree/main/packages/viewer-presets. Bug reports belong here; larger changes should be proposed against the monorepo path.
