# vmulti-experiment

Transfer-only EWDK wrapper draft for `djpnewton/vmulti`.

This repo intentionally contains only wrapper/review files:

- `vmulti-ewdk.sln`
- `sys/vmulti.vcxproj`
- `source-inventory.md`

It does not contain vmulti source, ClinVision source, driver binaries, generated INF/CAT/SYS/PDB/OBJ artifacts, signing material, or install/load tooling.

Use only as a convenient transfer/review repo for the ClinVision vmulti lab. Do not build/sign/install/load from this repo without the separate ClinVision review gates.

## Caveat fix 2026-06-30

The wrapper now defaults build outputs outside the vmulti working copy:

```text
OutDir = C:\ClinVisionLab\vmulti-artifacts\modern-ewdk\package\
IntDir = C:\ClinVisionLab\vmulti-artifacts\modern-ewdk\obj\vmulti\$(Configuration)\$(Platform)\
```

Signing remains inactive by design: there are no certificate, SignTool, package-signing, deployment, post-build, StampInf, or Inf2Cat hooks in this wrapper. Before any build approval, the EWDK project should still be inspected/evaluated to prove no signing target is active. Do not add signing material or run signing commands in the wrapper slice.

## Signing-off fix 2026-06-30

The wrapper now explicitly disables WDK signing/test-sign behavior in the project file:

```text
SignMode = Off
EnableTestSign = false
EnableDeployment = false
```

This is still build-only preparation. Do not run SignTool, Inf2Cat, driver install/load, TESTSIGNING changes, or input/report-write tests until separately approved.
