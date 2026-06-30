# vmulti-experiment

Transfer-only EWDK wrapper draft for `djpnewton/vmulti`.

This repo intentionally contains only wrapper/review files:

- `vmulti-ewdk.sln`
- `sys/vmulti.vcxproj`
- `source-inventory.md`

It does not contain vmulti source, ClinVision source, driver binaries, generated INF/CAT/SYS/PDB/OBJ artifacts, signing material, or install/load tooling.

Use only as a convenient transfer/review repo for the ClinVision vmulti lab. Do not build/sign/install/load from this repo without the separate ClinVision review gates.
