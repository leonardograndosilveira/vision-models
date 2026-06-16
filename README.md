# allvision-models

Public model-weight bundle for the AllVision Windows zero-touch installer.

Source code lives in the private `allvision` repo. Only the inference weights
are published here so the Windows installer (`scripts/setup/fetch_models.ps1`)
can fetch them with built-in PowerShell `Invoke-WebRequest` — no `gh`, no auth,
no `zstd`.

## Assets

- `models-bundle.zip` (Release `models-v2`): the 17 files listed in the private
  repo's `models/bundle_manifest.json`, paths relative to `models/`. The
  installer extracts it into `models/` and verifies every file against that
  manifest (sha256 + size). TensorRT `.engine` files are excluded — they are
  GPU-specific and built locally.

Bundle provenance and checksums: private `allvision` repo,
`models/bundle_manifest.json`.
