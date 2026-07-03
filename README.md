# veris-models

Model weights hosted for the [Veris](https://github.com/aryanramaniwork-arch/Veris) Figma plugin's
neural attention engine (Phase 2 of the attention-heatmap enhancement plan). Served via jsDelivr
CDN so the plugin's UI (which cannot bundle multi-MB binaries into its single-file HTML build) can
lazily fetch them at runtime.

Layout:
- `msi-net/v1/` — MSI-Net visual saliency model (Kroner et al. 2020), converted from the original
  Keras SavedModel to a float16-quantized TF.js graph model. MIT license (see `msi-net/v1/LICENSE`).
- `blazeface/v1/` — face detector for the attention engine's face channel (added when Phase 2 needs
  it). Apache-2.0 license.
- `tfjs-wasm/v1/` — WASM backend binaries for `@tensorflow/tfjs-backend-wasm`, mirrored here so the
  Figma iframe never needs a second CDN origin. Apache-2.0 license.

No design data, no user content — this repo only ever contains third-party model weights and their
upstream licenses.
