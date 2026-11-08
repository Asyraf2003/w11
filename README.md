# Windows 11 capability reference

A practical reference of Windows 11 behavior, requirements, interfaces, and ASUS Zenbook 14 **UM3406GA** capabilities, preserved before a future Arch Linux session. Collection date: **2026-11-08**. This is documentation, not a migration or feature-parity claim.

## Inventory

- [Keyboard shortcuts, mouse, touchpad and touch](docs/01-shortcuts.md)
- [Windows Settings, shell and system behavior](docs/02-windows-system.md)
- [Copilot, Windows AI and processing boundaries](docs/03-copilot-ai.md)
- [ASUS Zenbook, MyASUS, OLED and input](docs/04-asus-myasus.md)
- [Dolby, audio processing and Windows audio interfaces](docs/05-dolby-audio.md)
- [Windows and Android integration](docs/06-android-integration.md)
- [Advanced Windows interfaces and internals](docs/07-windows-internals.md)
- [Evidence register, coverage and remaining manual gaps](docs/08-capability-status.md)
- [Linux validation: WSL results and native-hardware limits](docs/09-linux-validation.md)

All seven requested domain families have official-source coverage. The evidence register distinguishes current native results, historical observations, supplied UI evidence and remaining manual gaps. There is no claim of absolute completeness: Windows builds, Store applications, OEM packages, accounts, region and cloud rollouts change the available surface.

Phase 2's Windows reference is preserved here. **Phase 3 started on 2026-11-08:** evaluate software in a separate Linux lab, and reserve physical hardware claims for native Linux. Completed results and pending checks are tracked in the Linux validation document.

## Evidence language

| Status | Meaning |
|---|---|
| DOCUMENTED | An official source describes the capability and its conditions. |
| AVAILABLE | Installed or exposed on this actual machine; presence alone does not prove use. |
| OBSERVED | A specific behavior was actually verified, with date/context. |
| CAPTURED | Supporting evidence is preserved; may remain private. |
| UNAVAILABLE | Explicit evidence establishes lack of support or availability in the stated scope. |
| UNKNOWN | Evidence is insufficient, inaccessible, stale or untested. |

Statuses can be combined. Historical observations retain their original dates and are not silently promoted to current observations. An access-denied query is a collection limitation, not evidence of an unsupported feature. An installed package, service, driver or license component does not prove active processing or entitlement.

## Sources and privacy

Official sources are linked next to the relevant tables. Descriptions are paraphrased; shortcut mappings and interface names are technical facts. This repository contains reviewed derived facts only. Raw captures, account information, machine/device instance identifiers, addresses, serials, keys, personal content, OEM binaries and tuning files stay outside it.

Historical reference: private `Asyraf2003/pc`, `pc/zenbook-um3406ga/`, local reviewed revision `36f277f` (2026-11-05), including captures dated 2026-09-25/26. `Asyraf2003/arch-blueprint` revision `20543c6` supplies context about already-preserved knowledge, not proof of Windows or Linux runtime behavior. Neither reference repository is modified.

The collector made no changes to Windows settings, firmware, registry values, drivers, services, security policies or Frankenstein implementation. User-supplied screenshots show selections at successive moments; they do not promise a permanently unchanged operator configuration.
