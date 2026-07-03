# tfjs-wasm v1

WASM backend binaries for `@tensorflow/tfjs-backend-wasm@4.22.0`, mirrored here so the Figma
plugin's iframe (which can only reach domains listed in `manifest.json`) never needs a second CDN
origin beyond `cdn.jsdelivr.net` for the WebGL-unavailable fallback path.

- `tfjs-backend-wasm.wasm` — baseline (no SIMD, no threads).
- `tfjs-backend-wasm-simd.wasm` — SIMD-accelerated.
- `tfjs-backend-wasm-threaded-simd.wasm` — SIMD + multi-threaded (requires cross-origin isolation,
  unlikely available inside the Figma iframe — kept for completeness/future use).

Copied verbatim from `node_modules/@tensorflow/tfjs-backend-wasm/dist/` in the
[Veris](https://github.com/aryanramaniwork-arch/Veris) repo at that package version. License:
Apache-2.0 (see `LICENSE`).
