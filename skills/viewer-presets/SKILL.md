---
name: viewer-presets
description: Apply tuned lighting rigs, floor reflection, bloom and PBR material presets (chrome, gold, glass and more) to a three.js avatar scene with @three-ws/viewer-presets. Use when a model needs a polished look quickly.
---

# Viewer presets with @three-ws/viewer-presets

Zero-dependency ESM presets for how a three.js avatar scene is lit and how its materials read. Reversible by design.

## Install

```
npm install @three-ws/viewer-presets
```

Node 18 or newer. `three` 0.150 or newer is an optional peer, and is passed in, never imported.

## Subpath modules

- `@three-ws/viewer-presets/lights`: `buildLightRig(THREE, overrides?)` returns `{ group, headTarget, shoeTarget }` (five spotlights). `LIGHT_CONFIG` holds the defaults.
- `@three-ws/viewer-presets/floor`: `floorReflectionConfig(props)` merges overrides over `FLOOR_REFLECTION_DEFAULTS`. `color` is required and should match the canvas background, or it throws.
- `@three-ws/viewer-presets/bloom`: `bloomConfig(overrides?)` over `BLOOM_DEFAULTS`.
- `@three-ws/viewer-presets/materials`: `MATERIAL_PRESETS`, `MATERIAL_PRESET_NAMES`, `materialPreset(idOrConfig, overrides?)`, `applyMaterialPreset(THREE, root, idOrConfig)` returning `{ restore(), count }`, and `materialVariants(base, { seed, count, hueSpread, jitter })`.

Preset ids include `chrome`, `gold`, `copper`, `brushedSteel`, `gunmetal`, `matte`, `glossy`, `rubber`, `ceramic`, `glass`, `realGlass`, `wood`, `stone`, `fabric`, `skin`, `carPaint`, `neon`, `holographic`. `realGlass` needs a `MeshPhysicalMaterial` and the transmission pass. Physical-only fields are skipped on plain Standard materials.

## Example

```js
import * as THREE from 'three';
import { buildLightRig } from '@three-ws/viewer-presets/lights';
import { applyMaterialPreset, materialVariants } from '@three-ws/viewer-presets/materials';

const { group } = buildLightRig(THREE, { keyLightIntensity: 1.2 });
scene.add(group);

const handle = applyMaterialPreset(THREE, gltf.scene, 'chrome');
handle.restore(); // put the original materials back

const variants = materialVariants('gold', { seed: 42, count: 6 }); // same seed, same set
```

`materialVariants` is pure and seeded, so a variant set can be shared by its seed number.
