# MSI-Net v1

Converted from [alexanderkroner/MSI-Net](https://huggingface.co/alexanderkroner/MSI-Net) (Keras
SavedModel) to a float16-quantized TF.js graph model for the Veris attention engine.

- Source: `saved_model.pb` + `variables/`, downloaded via `huggingface_hub.snapshot_download`.
- Conversion: `tensorflowjs.converters.tf_saved_model_conversion_v2.convert_tf_saved_model`,
  `signature_def='serving_default'`, `saved_model_tags='serve'`,
  `quantization_dtype_map={'float16': '*'}`.
- Result: ~24.93M parameters, 100% quantized to float16, ~48MB total across 12 shards.
- Input signature (verified via `saved_model_cli show --all`): `input_1`, shape `(-1,-1,-1,3)`
  float32 — fully convolutional, accepts any resolution. Output: `layer_from_saved_model`
  (`PartitionedCall:0`), shape `(-1,-1,-1,1)` float32, matching input spatial dims.
- Preprocessing (per the model card): resize preserving aspect ratio + symmetric pad to the
  target shape, raw 0–255 float32 pixel values — **no `/255` normalization** before feeding the
  model; any input scaling is baked into the graph itself.
- License: MIT (Kroner, Senden, Driessens, Goebel — see `LICENSE`).

Reproduce with `tools/model-pipeline/convert.py` in the
[Veris](https://github.com/aryanramaniwork-arch/Veris) repo.
