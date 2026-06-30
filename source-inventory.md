# vmulti Source Inventory Baseline

Task: T-2026-06-25-001-windows-driver  
Basis: host analysis copy at `tasks/T-2026-06-25-001-windows-driver/inputs/vmulti`

This inventory is for wrapper review only. The wrapper draft must not change these files semantically.

## Old Build Metadata

`sys/sources` declares:

```text
TARGETNAME=vmulti
TARGETTYPE=DRIVER
KMDF_VERSION_MAJOR=1
TARGETLIBS=$(DDK_LIB_PATH)\hidclass.lib $(DDK_LIB_PATH)\ntstrsafe.lib
INCLUDES=..\inc
SOURCES=vmulti.c vmulti.rc
INF_NAME=vmulti
TARGET_DESTINATION=bin
ALLOW_DATE_TIME=1
```

## Required Review Inventory

| Path | Purpose |
| --- | --- |
| `README.md` | Upstream build/install notes. |
| `buildme.bat` | Old WDK 7.1 build wrapper; not used by modern EWDK draft. |
| `dirs` | Old WDK directory build list. |
| `sys\sources` | Authoritative old driver source/link/include metadata. |
| `sys\makefile.inc` | Old WDK make include. |
| `sys\vmulti.c` | Driver behavior implementation; must not be changed in wrapper slice. |
| `sys\vmulti.h` | HID descriptors, hardware IDs, driver declarations; must not be changed. |
| `sys\vmulti.rc` | Existing resource file; wrapper includes it as resource only. |
| `sys\vmulti.inx` | Old INF template; wrapper treats it as non-build content only. |
| `inc\vmulticommon.h` | VID/PID, report IDs, and report structs; must not be changed. |
| `inc\hidport.h` | Local HID/KMDF include used by source; include order must preserve local intent. |

## Intended Wrapper Additions Only

```text
vmulti-ewdk.sln
sys\vmulti.vcxproj
```

No `.sys`, `.inf`, `.cat`, `.pdb`, `.obj`, `.binlog`, generated package folder, signing material, or ClinVision repo file belongs in this wrapper-only draft.
