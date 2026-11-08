# Capability evidence and remaining gaps

Reconciled **2026-11-08**. This register preserves Windows behavior, interfaces, dependencies and evidence. Phase 3 has now started in a separate Linux test area; its results are tracked in [Linux validation](09-linux-validation.md). Windows collection statuses below remain distinct from Linux validation results; no Windows-to-Linux parity claim is made here.

Status definitions are in the [README](../README.md). `OBSERVED UI` means the control/selection was seen, not that the physical effect was measured. `UNAVAILABLE` always names its scope: a missing installed component, a disabled state or an explicit supported-hardware restriction is different from an unsupported physical capability.

## Coverage denominator

The defined domain denominator is the user's **seven requested families**, not every possible Windows feature. All seven have official-source coverage and relevant machine evidence. Inventories are compact grouped entries: one row can contain multiple related shortcuts or capabilities, so row counts must not be presented as a count of unique functions.

| Requested domain | Preserved coverage | Strongest actual-machine evidence | Remaining material gap |
|---|---|---|---|
| A. Shortcuts/interactions | Shell, editing, dialogs, Explorer, taskbar, Snap/desktops, capture, accessibility, gestures, app/RDP contexts and general ASUS OEM keys | Historical input topology; current MyASUS Fn/NumberPad UI; official family manual reference | Legacy Paint/Notepad source verification; most chords not exercised. Physical per-SKU keyboard mapping is outside this pass. |
| B. Windows system | Settings Home plus 11 main categories, shell, accounts, security, recovery, storage, gaming and developer surfaces | Current OS, power states, security, hardware and servicing inventory | Per-setting values outside supplied UI; physical peripherals/recovery behavior |
| C. Copilot/AI | Copilot app/Voice/Vision, Recall, Click to Do, semantic search, Studio Effects, captions, Paint/Photos/OCR and processing boundaries | NPU/current AI packages; fresh Studio Effects and Snipping UI; Recall component Enabled | Per-app models, entitlement, region/language and actual workloads; Paint/Photos deeper checks explicitly deferred |
| D. ASUS/OEM | Battery/fans/power, OLED/color, keyboard/NumberPad, audio, QoS, diagnostics/update, GlideX/ScreenXpert | Current driver/services/packages and user MyASUS screenshot sequence | Submenus not expanded; optical/acoustic/thermal/charging behavior |
| E. Dolby/audio | Hardware/driver/APO/DSP/app layers, presets/EQ, spatial sound, voice and APIs | Current component versions; Dolby UI with eight presets, 10-band EQ and effects On | Separate headphone/HDMI entitlement and actual rendering/audio-quality measurements |
| F. Android | Windows ↔ Android ecosystem: Phone Link, camera, notifications/messages/calls, clipboard/files/apps, hotspot, Quick Share, Bluetooth, USB/ADB and casting | Official feature-specific OEM/OS restrictions; current PC packages/radio interfaces and receiver installation state | End-to-end transfer/mirror tests unperformed; an assessment of the owner's phone is outside scope |
| G. Internals | Win32/WinRT/COM, CIM/PowerShell, PnP/ACPI/UEFI, security, power, graphics/media/audio, storage, networking, services/tasks and subsystems | Successful current read-only native queries and feature-state inventories | Workload-level proof, peripheral interoperability, detailed API contracts only where needed |

Every domain points to its numbered reference document. Sources were researched breadth first, then machine-specific ambiguities were reconciled. A cloud rollout, new app or future OEM update can introduce more capabilities after this capture.

## Evidence provenance

| Evidence set | Date/scope | Preservation and limits |
|---|---|---|
| Historical private PC reference | September 25/26 captures; reviewed local `pc` revision **36f277f**, dated November 5 | Hardware/topology, MyASUS observations, OEM audio/XML, OLED evidence. Raw binaries/configuration remain private and unchanged. |
| Local post-service differential | November 5, hardware/OEM/AI/USB4/power | Reused rather than redumped blindly; never treated as a current app/build version where fresh evidence differs. |
| Initial restricted native batch | November 8, **21 named query groups** | Per-query UTC start/end, selected fields, error or native exit code, provenance and SHA-256 manifest stored locally outside this repo. Access-denied and null results preserved. |
| Unrestricted refresh | November 8, **13 additional query groups**, after user opened session permissions | Refreshed denied/null hardware, PnP/drivers/tasks/servicing/security/storage queries plus selected Win32 registration, radio and WinRE metadata. Original restricted captures unchanged. No Windows permission/security policy was changed. |
| Enumeration decoder | November 8, installed DISM module enum reflection | Captured mapping of capability/optional-feature numeric states to names, with supplemental hash; avoids guessing what serialized enum integers mean. |
| User screenshots | November 8 session, **16 initial frames S03–S18** | Visually reviewed originals; private filename/size/timestamp/SHA-256 manifest. File timestamps are not independent proof of when a screen was captured. Selected states are frame-specific. |
| User screenshot follow-up | November 8, **2 further frames S19–S20**; **18 total** | Current Studio Effects and Snipping start UI. Separate private provenance manifest; personal camera preview/desktop transcript not republished. |
| Official documentation | Reviewed November 8; direct URLs in domain chapters | DOCUMENTED functionality and requirements, paraphrased. Does not prove installation or successful operation. |
| Linux copy/read check | November 8, private removable-drive preservation folder | **64/64 source-file hashes and lengths match** when read from Arch WSL; **39 JSON** parsed and **18 PNG** signatures checked. This verifies preservation/readability, not Windows/Linux feature parity. |
| Focused NPU hardware-ID supplement | November 8, read-only ComputeAccelerator hardware-ID query | Exact **1022:17f0 revision 20** captured; original and removable-drive copy hashed. Pinned upstream device/revision match is documented in the AI chapter; no accelerator workload run. |

The initial batch's errors are historical collection results, not current unsupported-feature conclusions. The later successful refresh resolves those collection gaps; both records remain preserved.

## Current hardware and exposed-state register

| Capability | Actual evidence / date | Status | Boundary |
|---|---|---|---|
| Windows release | Registry **26H2 / 26300.9818**, CIM Windows 11 Home Single Language build 26300, WSL host-version corroboration | AVAILABLE, OBSERVED metadata, CAPTURED | Earlier November 5 build 26200 is historical; legacy ProductName Windows 10/2009 fields are not the current OS identity |
| CPU/memory | Ryzen AI 7 445, **6 cores / 12 logical**, **16 GiB class** physical memory; fresh CIM | AVAILABLE, CAPTURED | Exact reported physical total is below nominal 16 GiB due to platform reservation; no benchmark |
| NPU | Compute Accelerator present OK; driver **32.0.203.329**; hardware **AMD 1022:17f0 rev 20** | AVAILABLE, CAPTURED; DOCUMENTED exact Linux driver-table match | AMD documents up to **50 NPU TOPS**; Linux runtime/model execution and per-app NPU use remain UNKNOWN. Camera effects, local AI and noise cancellation are explicit validation priorities |
| Graphics/display | Radeon 840M **32.0.22042.11003**; current **1920×1200, 60 Hz**; active brightness provider | AVAILABLE, OBSERVED metadata, CAPTURED | Not maximum supported mode, HDR verification, color accuracy or flicker measurement |
| BIOS | **UM3406GA.305** | AVAILABLE, CAPTURED | No firmware image, UEFI variables or unique identity data published |
| Storage | Samsung NVMe approximately **1 TB**, high-level Healthy | AVAILABLE, CAPTURED | No endurance/SMART or restoration test |
| TPM | Present/ready/enabled/activated; manufacturer field MSFT | AVAILABLE, OBSERVED reported state, CAPTURED | No keys/protectors/biometrics exported; not old credential-recovery proof |
| Pluton | Present security processor | AVAILABLE, CAPTURED | Do not infer TPM implementation solely from this devnode or CPU family |
| Secure Boot | Native query **True** | AVAILABLE, OBSERVED reported state, CAPTURED | Does not establish trust of a future boot chain |
| VBS | Status **2**, hypervisor present | AVAILABLE, OBSERVED running report, CAPTURED | Memory integrity, Secure Launch and SMM measurement are reported running; no penetration/security certification claim |
| S0 sleep | **Network Disconnected** available; connected standby disabled by policy | AVAILABLE, CAPTURED | September connected-standby report superseded; no overnight drain/resume test |
| Hibernate/Fast Startup | Reported available | AVAILABLE, CAPTURED | Successful cycle not tested |
| S1/S2/S3 / Hybrid Sleep | Reported unavailable in current configuration | UNAVAILABLE in captured sleep-state report, CAPTURED | Reasons include firmware/S0/Device Guard/hypervisor constraints; no settings changed |
| RGB / IR camera | FHD and IR UVC devices present OK; Hello Face capability Installed | AVAILABLE, CAPTURED | Hello enrollment, ESS/anti-spoof quality and authentication not tested |
| Studio Effects | Camera and driver present OK; fresh S19 exposes framing, Standard eye contact and standard/portrait blur | AVAILABLE, OBSERVED UI, CAPTURED current controls | Actual effect execution, quality and workload acceleration separate |
| USB4 | Host/router/root and power-coordination nodes present OK | AVAILABLE, CAPTURED | Dock, external display, eGPU, PD and maximum throughput untested |
| Wi-Fi | MT7922/RZ616 **3.5.2.1383**; 2.4/5/6 GHz and 802.11ax advertised | AVAILABLE, CAPTURED | Regional/AP/connection restrictions apply; no SSIDs, addresses, profiles or keys published |
| Wi-Fi Direct | Device/GO/client and 5 GHz GO supported; 6 GHz GO not supported in report | AVAILABLE / UNAVAILABLE advertised roles as stated, CAPTURED | An advertised role is not successful peer connectivity |
| Legacy wireless modes | Hosted Network / Soft AP / monitor mode / IBSS reported unsupported | UNAVAILABLE as advertised driver modes, CAPTURED | This does not prove modern Mobile Hotspot unavailable; Wi-Fi Direct uses a different path |
| Miracast prerequisites | Wireless Display graphics and Wi-Fi flags Yes; sink capability advertised | AVAILABLE reported prerequisites, CAPTURED | Wireless Display receive capability NotPresent; no actual projection tested |
| Bluetooth | MediaTek adapter **1.1146.2.576**; profile components present | AVAILABLE, CAPTURED | Codec, LE Audio, calls/tethering and specific accessory quality unknown |
| ASUS input | SCI v3 **3.1.73.0**, Precision Touchpad/NumberPad filter **17.0.0.30** present | AVAILABLE, CAPTURED | Current UI unlocks both; full physical gesture/key execution untested |
| Sensors | AMD UMDF Sensor and Sensor Fusion Hub stack | AVAILABLE, CAPTURED | Ambient-light automation UI present; sensor readings, presence detection and rotation not proven |
| OLED / color | MyASUS_Splendid node; supplied OLED/Splendid/gamut controls | AVAILABLE, OBSERVED UI, CAPTURED | No luminance, PWM, calibration, panel compensation or burn-in prevention efficacy measurement |
| OEM audio | Realtek ALC294 family, Cirrus CS35L51, AMD ACP, Dolby/intelliGo/Voice Clarity components | AVAILABLE, CAPTURED | Active graph/order/processor and acoustic effect not inferred from installation |
| Dolby UI | Eight presets, intelligent EQ choices, Custom 3 10-band EQ, virtualizer/leveler On; master effects On in supplied frames | AVAILABLE, OBSERVED UI, CAPTURED | Separate headphone/HDMI license and actual spatial content rendering UNKNOWN |

## Current component and servicing register

| Capability | Actual state | Classification and restriction |
|---|---|---|
| MyASUS / GlideX / ScreenXpert | **4.0.82.0 / 4.3.5.0 / 4.0.25.0** current-user packages and launchers | AVAILABLE, CAPTURED; model-specific MyASUS UI further OBSERVED; individual GlideX/ScreenXpert sessions UNKNOWN |
| Phone Link / CrossDevice | **1.26092.119.0 / 1.26101.77.0** | AVAILABLE, CAPTURED; phone pairing/eligibility unknown |
| Snipping / Paint / Photos / Camera | **11.2608.41.0 / 11.2609.401.0 / 2026.11090.22001.0 / 2025.2505.2.0** | AVAILABLE, CAPTURED; each AI menu/model/entitlement needs its own evidence |
| Copilot launcher | MicrosoftOfficeHub **156.0.4314.58** with launcher name Copilot | AVAILABLE, CAPTURED identity; not proof of consumer versus organizational entitlement |
| AI infrastructure | VitisAI **1.8.80.0**, AIX/CoreAI **1000.26100.9818.0**, AIFabric **1.6.955.100** | AVAILABLE, CAPTURED; no inference workload run |
| Recall | Optional feature **Enabled** | AVAILABLE installed/enabled component, CAPTURED; snapshot opt-in/saving/history and behavior UNKNOWN, deliberately not inspected |
| WSL / WSLg | CLI **3.0.3.0**, kernel **6.18.54.1-1**, WSLg **1.0.79** | AVAILABLE version surface, OBSERVED query operation, CAPTURED; no Linux feasibility task performed |
| Virtualization optional states | VirtualMachinePlatform Enabled; HypervisorPlatform Disabled; older Subsystem-Linux optional component Disabled | CAPTURED; these do not cancel the separate successful WSL package-version query |
| Windows Home edition restrictions | Full Hyper-V role, Windows Sandbox and incoming RDP host unsupported by Microsoft's supported-edition contract | DOCUMENTED restriction, UNAVAILABLE under this edition contract; WSL2 and RDP client are separate |
| Remote Desktop Connection | Client optional feature Enabled | AVAILABLE, CAPTURED; no remote connection opened |
| OpenSSH | Client Installed, server NotPresent | AVAILABLE client, UNAVAILABLE installed server in this snapshot; network/credential behavior untested |
| Wireless Display receiver | `App.WirelessDisplay.Connect` NotPresent | UNAVAILABLE installed optional receiver; not a universal Miracast hardware exclusion |
| Language features | English OCR/speech/TTS/handwriting installed; basic English/Chinese components present | AVAILABLE components, CAPTURED; no display-language entitlement or successful translation inference |
| Print/media/runtime | Print to PDF, Media Playback/Windows Media Player, print foundation/internet client, .NET4/WCF components Enabled | AVAILABLE configured components, CAPTURED; no printed/media/network workload |
| Legacy features | SMB1 client/server, Telnet/TFTP Disabled; NetFx3 payload removed | UNAVAILABLE as enabled features/payload in this scope; no security configuration was changed |
| WinRE | Registered Enabled; status query successful | AVAILABLE, CAPTURED; recovery boot untested |
| OEM tasks | Seven filtered entries include ASUS optimization/update/analysis/diagnosis plus cleanup/storage families; Ready states | AVAILABLE definitions, CAPTURED; private suffixes/actions/principals omitted; task success not inferred |

Full component details are in their domain chapters. Current-user Appx inventory is not an all-user, provisioned-package, portable-app or exhaustive Win32 inventory. The narrow Win32 registry filter is intentionally not used to declare broad app absence.

## What can be checked next without collecting personal content

| Gap | Minimum useful evidence | What it would establish |
|---|---|---|
| Remaining AI controls | Captions language menu, nonpersonal Snipping text-action controls and feature model metadata if a future decision needs them | Studio Effects and Snipping start controls already OBSERVED; model execution and entitlement remain separate |
| Deferred Paint/Photos depth | No further collection required in this pass, per explicit user direction; retain official descriptions and requirements | Deferred to later development, not UNAVAILABLE and not a Linux-equivalence claim |
| Copilot entitlement/keys | Nonpersonal settings/readout of key target and available Voice/Vision entry points, omitting chats/account identity | Current UX/option exposure; no conversation inspection needed |
| Future Android deployment eligibility | Consult the linked vendor matrix for whichever Android device/OS is later selected | No personal-phone inventory is required by this ecosystem reference; actual pairing remains untested |
| ASUS closed submenus | Gamut and timeout dropdown options, dedicated-memory choices, optional Quick Setting headings | Exact allowed menu values, without applying a setting |
| ASUS hotkey reference / touch scope | General ASUS documentation, UM3406 manual index and current Fn-mode UI are sufficient for this pass | No physical keyboard photo or full key test is pending. Touchscreen functionality still requires a digitizer and is not inferred from OLED. |
| Dolby entitlement | Activation information shown without account identity; selected endpoint/spatial-provider list | Distinguish OEM effects from separate headphone or home-theater entitlement |
| Physical behavior | Deliberate future battery/fan/ALS/OLED/audio/camera/dock/sleep checks only where useful | Actual measured behavior under stated conditions; a different evidence class from UI presence |

The MyASUS and Dolby screenshot batch resolved the broad OEM menu gap; follow-up screenshots resolved current Studio Effects and Snipping start-surface exposure. The user explicitly deferred deeper Paint/Photos AI inspection, chose general ASUS/UM3406 keyboard references, and scoped Android coverage to the ecosystem rather than a personal phone. No further physical-keyboard or personal-phone collection is pending for this pass. Remaining Windows gaps do not block the agreed selective Linux validation.

Linux validation prioritizes **audio/amplifier protection, charging, fan/thermal policy, suspend/power and NPU-backed AI goals**. Common shortcuts need documentation/mapping rather than individual runtime tests. Generic DSP and preservation checks are complete; actual native hardware remains untested. The [validation record](09-linux-validation.md) owns results, boot constraints and the remaining checks.

## Privacy and collection boundary

The public tree is reviewed Markdown and a restrictive ignore file. It contains no screenshots, raw system exports, OEM executables, driver packages, source tuning XML, activation/security fields, device instance paths, serials, UUIDs, addresses, account identities, messages, photos, clipboard contents, Recall snapshots or personal audio/video. Raw evidence and user originals remain local/private. The collector changed no Windows settings, driver, service, registry, firmware or security policy, and made no Frankenstein or reference-repository edits.

Remaining unknowns are explicit evidence limits rather than an invitation to reproduce proprietary processing or assume Linux support. The separate validation document now records Linux checks with their own environment and outcome; a Windows observation never becomes a Linux pass merely by being copied.
