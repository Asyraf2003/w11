# ASUS Zenbook 14 UM3406GA and MyASUS

Reviewed 2026-11-08. Generic ASUS documentation describes a feature family; only dated machine evidence establishes availability on this UM3406GA. Controls observed in an earlier session are not a claim that they remain enabled today.

## Evidence used

| Reference | Scope | What is preserved publicly |
|---|---|---|
| H1 | Private capability map and OEM baseline, captured 2026-09-25 | Derived descriptions of displayed controls, installed stack and recorded observations; no raw exports |
| H2 | Private OLED Care evidence, captured 2026-09-26 | Derived implementation boundaries; no proprietary executable, INF text or extracted strings |
| H3 | Private map's post-service revalidation, 2026-11-05 | MyASUS 4.0.81.0 and GlideX 4.1.2.0 current-user package metadata; current feature operation untested |
| H4 | Fresh read-only package/service/CIM/PnP/task capture, 2026-11-08 | Updated nonpersonal versions and interface states below; no settings changed |
| Official | ASUS sources linked beside capabilities; reviewed 2026-11-08 | Paraphrased behaviors and requirements |

`AVAILABLE (historical)` means the control/package/interface was exposed at the stated date. `OBSERVED` is limited to the recorded UI or behavior described. `CAPTURED` means supporting material remains privately preserved. Fresh runtime evidence belongs in [capability status](08-capability-status.md).

The [official UM3406 specifications](https://www.asus.com/us/laptops/for-home/zenbook/asus-zenbook-14-oled-um3406/techspec/) distinguish HA, KA and GA variants. GA lists Ryzen AI 7 445 and a 50-TOPS NPU. Display/touch/pen configurations vary by market/SKU; a family specification does not prove this unit's panel or input hardware. The [GA support page](https://www.asus.com/jp/laptops/for-home/zenbook/asus-zenbook-14-oled-um3406/helpdeskhelpdesk_download?model2Name=UM3406GA) specifies Windows 11 24H2+ driver compatibility.

## Control path and prerequisites

| Component | Role and condition | Machine evidence |
|---|---|---|
| MyASUS | User-facing settings, diagnosis and support portal. App presence alone does not expose every feature. | H1/H3: AVAILABLE, CAPTURED; November 5 package version above |
| ASUS System Control Interface v3 | OEM driver/interface supporting many settings and background integrations. This is distinct from the Store app. | H1: AVAILABLE, CAPTURED; exact present driver version needs runtime reconciliation |
| Model-specific display/input extensions | Splendid, OLED and NumberPad integration can depend on OEM extensions beyond the base SCI driver. | H1/H2: AVAILABLE, CAPTURED; package presence alone does not prove processing |

ASUS documents reduced functionality without a suitable [System Control Interface](https://www.asus.com/support/faq/1045676/) and the [installation prerequisites](https://www.asus.com/global/support/faq/1039718/). Installing MyASUS after a clean OS installation does not automatically restore all factory functions. No installation or repair was performed during this harvest.

## Power, battery and thermals

| Capability | Preserved behavior / conditions | Evidence status |
|---|---|---|
| Battery Care Mode | Charge-limit UI offered **80%**. Actual electrochemical longevity and precise recharge hysteresis were not measured. | H1: AVAILABLE, OBSERVED UI, CAPTURED; current state UNKNOWN |
| Instant Full-Charge | Temporarily permits **100%**; UI described return to Battery Care after **24 hours**. | H1: AVAILABLE, OBSERVED UI, CAPTURED; full 24-hour transition not independently timed |
| Fan profiles | **Performance, Standard, Whisper** were exposed. They represent thermal/performance policy, not a user-specified fixed RPM curve. | H1: AVAILABLE, OBSERVED UI, CAPTURED; fan RPM/temperature effects unmeasured |
| Power Mode synchronization | MyASUS offered coordination between fan policy and Windows power mode. | H1: AVAILABLE, OBSERVED UI, CAPTURED; exact transitions not freshly exercised |
| Sleep Assistant | Exposed standby policy intended to detect abnormal battery use/heat and move to hibernation where appropriate. | H1: AVAILABLE, OBSERVED UI, CAPTURED; overnight behavior UNKNOWN |
| GPU/shared memory allocation | Dedicated/shared-memory allocation controls were displayed. Values shown by Windows are not proof of firmware reservation or effective cross-OS allocation. | H1: AVAILABLE, OBSERVED UI, CAPTURED; allocation mechanism and current value UNKNOWN |

These feature families and per-model variation are [DOCUMENTED by ASUS](https://www.asus.com/global/support/faq/1045651/). The generic page also describes newer adaptive battery policy, full-speed profiles and separate AC/battery controls; those additions remain **UNKNOWN on this unit** unless its UI exposes them. Do not substitute older ASUS 60/80/100% schemes for the captured 80%/temporary-full-charge behavior.

## OLED, brightness and color

| Capability | Preserved behavior / boundary | Evidence status |
|---|---|---|
| OLED Care Pixel Refresh | MyASUS identified a special screen saver after more than 30 idle minutes; enabled UI was captured. This is the laptop's named feature, not proof of the six-minute panel-cleaning cycle described for some external ASUS monitors. | H2: AVAILABLE, OBSERVED UI, CAPTURED; actual idle transition not timed |
| OLED Care Pixel Shift | UI said permanently enabled on the captured stack. A dedicated ASUS userspace shifter was running; historical metadata/static inspection supports periodic window/display handling. | H2: AVAILABLE, OBSERVED process/UI, CAPTURED; exact shift geometry/cadence UNKNOWN |
| OLED Care screen-saver extension | Historical package evidence identifies a separate screen-saver installation path. It does not explain the entire Pixel Shift mechanism. | H2: AVAILABLE, CAPTURED |
| Taskbar protection | Auto-hide enabled; transparency had a separate control. | H2: AVAILABLE, OBSERVED UI, CAPTURED; current policy UNKNOWN |
| Flicker-Free Dimming | Separate OLED brightness/dimming control exposed. A brightness slider does not establish its waveform, PWM behavior or low-level interface. | H1/H2: AVAILABLE, OBSERVED UI, CAPTURED; optical measurements UNKNOWN |
| Splendid | Normal, Vivid, Manual color temperature and Eye Care controls recorded. | H1: AVAILABLE, OBSERVED UI, CAPTURED; calibration accuracy unmeasured |
| Electronic Reading | Grayscale/reading behavior recorded as a distinct display option. | H1: AVAILABLE, OBSERVED UI, CAPTURED |
| Color gamut | Gamut selection with Native recorded; privately preserved color profiles provide additional provenance. Do not redistribute the proprietary profile files. | H1: AVAILABLE, OBSERVED UI, CAPTURED; all alternate gamut labels/current selection UNKNOWN |
| Target Mode | Active window retains brightness while inactive screen areas dim. | H1: AVAILABLE, OBSERVED UI/behavior, CAPTURED; current enabled state UNKNOWN |

ASUS [documents OLED laptop precautions and OLED Care](https://www.asus.com/jp/support/faq/1045098/) and describes these software families in its [MyASUS reference](https://servers.asus.com/support/faq/detail/1050467). Generic gamut choices include sRGB, DCI-P3 and Display P3; Target Mode is described for the main OLED screen. Those generic descriptions do not prove every choice on this exact SKU. Splendid can also have display-topology restrictions; [ASUS's FAQ](https://www.asus.com/support/faq/1050467/) describes disabled behavior for some external-only/clone arrangements.

The preserved shifter evidence supports a Windows userspace contribution. It does **not** prove that every pixel shift is performed there or that panel/firmware protection is absent. No new binary analysis, DSP analysis or runtime manipulation was conducted. Removal of Windows/MyASUS cannot be assumed either to remove or to preserve every OLED protection.

## Keyboard, touchpad and sensors

| Capability | Behavior and condition | Evidence status |
|---|---|---|
| Fn mode | Shortcut-first versus ordinary F1–F12-first modes exposed in MyASUS. | H1: AVAILABLE, OBSERVED UI, CAPTURED; current selection UNKNOWN |
| Fn+Esc / hotkeys | ASUS documents Fn+Esc switching on supported models and synchronizing the MyASUS setting. Physical function-row mappings vary by model/key legends. | DOCUMENTED; exact UM3406GA physical mapping needs manual/model-manual proof. [Hotkeys guide](https://www.asus.com/sg/support/faq/1038312/) |
| Keyboard illumination | Manual brightness is separate from ambient automation and idle timeout. | H1: AVAILABLE, OBSERVED UI, CAPTURED; exact brightness steps UNKNOWN |
| Automatic keyboard backlight | Darker surroundings brighten/enable it; brighter surroundings dim/disable it using an ambient-light sensor. | H1: AVAILABLE, OBSERVED UI, CAPTURED; sensor readings not independently sampled |
| Backlight timeout | Sleep/idle-timeout policy with possible AC/battery differences exposed. | H1: AVAILABLE, OBSERVED UI, CAPTURED; exact selected intervals UNKNOWN |
| Precision Touchpad | ASUS I2C HID/Precision Touchpad path and touchpad lock/unlock control preserved. | H1: AVAILABLE, CAPTURED; gesture behavior depends on Windows settings |
| NumberPad | Integrated numeric input plus MyASUS lock control; ASUS NumberPad filter/service stack captured. | H1: AVAILABLE, OBSERVED UI/recorded behavior, CAPTURED; current activity UNKNOWN |
| NumberPad gestures | Generic ASUS guide describes one-second top-right activation, brightness selection and calculator launch gesture; cursor movement can coexist with number input. | DOCUMENTED; each exact gesture on this unit UNKNOWN. [NumberPad guide](https://www.asus.com/us/support/faq/1038283/) |
| Sensor stack | AMD UMDF Sensor and Sensor Fusion Hub recorded. Their presence does not identify every sensor exposed to an application. | H1: AVAILABLE, CAPTURED; exact ambient sensor API UNKNOWN |

The [Device Settings reference](https://www.asus.com/id/support/faq/1045651/) documents per-model support, low-battery restrictions on automatic illumination, and touchpad locking affecting NumberPad controls. Presence of a sensor package does not prove presence detection, automatic screen rotation or a touchscreen.

## Audio, connectivity and cross-device software

| Capability | Behavior / dependency | Evidence status |
|---|---|---|
| AI Noise-Cancelling Microphone | Captured MyASUS option for reducing unwanted microphone sound. Endpoints, mode and application routing determine what callers receive. | H1: AVAILABLE, OBSERVED UI, CAPTURED; signal-level effect UNKNOWN |
| AI Noise-Cancelling Speaker | Separate receive/playback-side speech/noise option. | H1: AVAILABLE, OBSERVED UI, CAPTURED; signal-level effect UNKNOWN |
| TaskFirst | Captured workload prioritization choices for communication/productivity, streaming, gaming and GlideX-related traffic. | H1: AVAILABLE, OBSERVED UI, CAPTURED; throughput/QoS effect unmeasured |
| WiFi SmartConnect | Captured UI describes selecting better known wireless connections and prioritizing remembered mobile hotspots. | H1: AVAILABLE, OBSERVED UI, CAPTURED; roaming not freshly tested |
| GlideX | Cross-device screen mirroring/extension, shared controls, file/URL sharing and supported communication/remote-access functions. Features depend on companion app, network/USB, permissions and edition. | DOCUMENTED; H3: AVAILABLE package, CAPTURED; individual functions UNKNOWN. [GlideX guide](https://www.asus.com/support/faq/1050468/) |
| ScreenXpert | Window switching, task groups, multi-display placement and quick controls. Zenbook DUO-specific gestures/layouts require those devices. | DOCUMENTED; H3's current-user filter was inconclusive; H4 records ScreenPadMaster package and running ScreenXpert Host Service. Component AVAILABLE/CAPTURED, individual functions UNKNOWN. [ScreenXpert guide](https://rog.asus.com/us/support/faq/1047764/) |

TaskFirst and WiFi SmartConnect are [documented separately from basic radio capability](https://www.asus.com/ch-de/support/faq/1045651/). Neither creates additional internet bandwidth. The [audio chapter](05-dolby-audio.md) separates ASUS/intelliGo processing from Realtek, amplifier hardware and Dolby licensing. The [Android chapter](06-android-integration.md) records transports and permissions without personal-content access.

## Diagnostics, updates and background components

| Capability | Behavior / boundary | Evidence status |
|---|---|---|
| System Diagnosis | Component/scenario checkups report findings and recommendations. Available checks vary by hardware. | DOCUMENTED; H1 diagnostic service AVAILABLE, CAPTURED; checkup outcomes UNKNOWN. [Diagnosis guide](https://www.asus.com/support/faq/1045716/) |
| System Update | Offers applicable BIOS/driver/firmware/software packages with critical/recommended/optional classifications and history. | DOCUMENTED; current applicable updates UNKNOWN; none installed. [Update guide](https://www.asus.com/support/faq/1051729/) |
| Update-discovery limits | Reinstalled systems with missing drivers may lack version comparisons and offered updates. No displayed updates is not proof of complete drivers. | DOCUMENTED; current condition UNKNOWN. [Version checks](https://www.asus.com/global/support/faq/1051439/) |
| ASUS Switch / recovery | Transfer/recovery entry points form part of the broader MyASUS portal. Reset/recovery actions are separate from collecting capability evidence. | DOCUMENTED; H1 ASUSSwitch service AVAILABLE, CAPTURED; transfer/recovery success UNKNOWN. [MyASUS introduction](https://www.asus.com/global/support/faq/1038301/) |
| Customer support / device portal | Product registration, repair/support and supported router/display controls depend on account and connected device. | DOCUMENTED; device/account availability UNKNOWN. [MyASUS introduction](https://www.asus.com/global/support/faq/1038301/) |
| Background services | ASUS App Service, Optimization, Software Manager, System Analysis, System Diagnosis, Switch and NumberPad service were recorded running in September. | H1: AVAILABLE, OBSERVED service state, CAPTURED; names/state do not prove a particular feature executes |
| Scheduled integrations | OEM optimization/update-check/diagnostic task families captured. | H1: AVAILABLE, CAPTURED; triggers running or completing successfully UNKNOWN |

## Documented families not proven on this unit

| Capability | Boundary | Status |
|---|---|---|
| Tru2Life video enhancement | ASUS explicitly excludes AMD processors. This is separate from Splendid's captured controls. | DOCUMENTED restriction; unavailable under ASUS's published AMD support policy. [ASUS software guide](https://www.asus.com/laptops/for-home/zenbook/zenbook-ux410/overview/asus-software/) |
| Adaptive Edge Brightness | Reviewed FAQ limits this named feature to selected ARM systems; it is not the same feature as AMD display power controls. | DOCUMENTED restriction; not established for AMD UM3406GA. [FAQ](https://servers.asus.com/support/faq/detail/1050467) |
| Presence Detection / Wi-Fi sensing | Walk-away lock/wake/gaze dimming require specific supported sensing hardware/software. | DOCUMENTED family; UM3406GA UNKNOWN. [Device Settings](https://zentalk.asus.com/t5/faq/myasus-device-settings/ta-p/408370) |
| Touchpad stylus / special smart gestures | Newer touchpads may expose additional edge gestures or pen support; Precision Touchpad alone does not imply these. | UNKNOWN on this unit; [Device Settings](https://www.asus.com/id/support/faq/1045651/) documents model variation |
| MUX / discrete-GPU mode / RGB / ScreenPad | Generic ASUS software includes controls for hardware configurations outside this evidence set. | UNKNOWN/not applicable without corresponding hardware evidence; never infer from the common app. [Device Settings](https://www.asus.com/global/support/faq/1045651/) |

## Fresh installed-stack reconciliation

| Interface/component | November 8 evidence | Boundary |
|---|---|---|
| MyASUS | Current-user package 4.0.82.0 | AVAILABLE + CAPTURED; current Device Settings selections UNKNOWN pending user UI evidence |
| ASUS System Control Interface v3 | Present PnP device OK; driver 3.1.73.0 | AVAILABLE + CAPTURED; does not prove every generic ASUS feature |
| Precision Touchpad | Present PnP device OK; driver 17.0.0.30; NumberPad service Running | AVAILABLE + CAPTURED; do not substitute the separate historical PTP filter branch |
| Splendid / OLED | MyASUS_Splendid monitor node OK | AVAILABLE + CAPTURED interface; selected gamut, actual transformations and current shifter activity UNKNOWN |
| Sensors / Studio camera | AMD UMDF Sensor, FHD/IR cameras and Studio Effects camera/driver present OK | AVAILABLE + CAPTURED; sensor-hub presence is not presence-sensing proof |
| GlideX | App 4.3.5.0; Win32 service-installer registration 4.1.2.0 | AVAILABLE + CAPTURED; different components have independent version numbers |
| ScreenXpert-related stack | ScreenPadMaster 4.0.25.0 package; ScreenXpert Host Service Running | AVAILABLE + CAPTURED components; no inference of physical ScreenPad/DUO hardware |
| Background services | App Service, Optimization, NumberPad, PTP, ScreenXpert Host, Software Manager, Switch, System Analysis and System Diagnosis Running | OBSERVED service state + CAPTURED; feature execution and update outcomes UNKNOWN |
| Scheduled tasks | OEM optimization, update checker, system analysis and driver-quality diagnosis registered Ready | AVAILABLE + CAPTURED definitions/state; machine-specific suffixes omitted, successful execution unproven |

For remaining GUI evidence, one nonpersonal batch can capture MyASUS About/Device Settings headings, selected power controls, display/OLED controls, input controls and connectivity headings. Automated GUI access was refused by the computer-use approval layer, so the user was asked for screenshots or a readout rather than repeatedly retrying. Physical ambient-light response, charge-limit cycling, fan/noise behavior and pixel-shift timing require deliberate observation beyond package discovery. Keep them UNKNOWN until measured; none blocks the broader inventory.
