# Dolby, OEM audio and Windows audio interfaces

Reviewed 2026-11-08. **Hardware → driver → processing → user-facing behavior** are separate evidence layers. A Dolby package, running service or tuning file does not establish a licensed/selected Atmos renderer. No microphone, playback-loopback or personal audio was recorded; no audio settings were changed.

## What the machine exposes

The fresh November 8 filtered PnP/driver capture reconfirms the following hardware/driver names and versions; private November 5 and September 25 records preserve earlier topology. These are **AVAILABLE + CAPTURED**, rather than measurements of processing quality.

| Layer | Actual component | Capability / evidence boundary |
|---|---|---|
| Hardware / codec identity | Realtek ALC294 family in historical hardware evidence; current Realtek High Definition Audio driver **6.0.9956.1** | Codec/interface identity; does not prove current DAC format, jack routing or effects |
| Hardware / amplifier | Windows identifies **Cirrus Logic CS35L51 Speaker Amps**, ACPI family **CSC3551**; driver **17.54.59.438** | Keep the Windows identity; a public CS35L41 brochure is not evidence of this model's electrical limits |
| Platform audio | AMD Audio CoProcessor **7.0.3.57** | Separate platform/controller layer; exact running offload workload UNKNOWN |
| Display audio | AMD High Definition Audio **10.0.1.41** | HDMI/DisplayPort audio path; external receiver/display format support UNKNOWN |
| Function driver / OEM extension | Realtek audio stack and support application components | Base codec driver, extension, service, APO and user control are distinct packages |
| Host processing | Realtek Audio Effects **13.5229.2429.788** | APO component installed; selected effect chain UNKNOWN |
| Host processing | DolbyAPO SWC **3.30811.890.1**; Dolby HSA components **3.30803.830.0** | DSP/control components installed; no entitlement or active spatial-rendering proof |
| Host processing | intelliGo APO/service/HSA components **100.1.601.2862** | OEM enhancement infrastructure; algorithm location, current mode and benefit UNKNOWN |
| Host processing | Voice Clarity PnP component present OK; November 5 driver **1.0.4.7057** | Availability of component; not proof that every microphone application uses it |
| Application | Dolby Settings **3.31100.346.0** | Current-user package and launcher AVAILABLE; current options await UI evidence |
| Application | Dolby Access OEM **3.27.13540.0** | Package AVAILABLE; visible activation/license state UNKNOWN |
| Application / decoder | Dolby Digital Plus Decoder OEM **1.2.591.0** | Decoder package is distinct from headphone Atmos entitlement and speaker processing |
| Application | Realtek Audio Control **2.53.391.0** | Current-user package AVAILABLE; exposed jack/EQ options vary by OEM |
| Professional interface component | Realtek ASIO **1.0.13.1** | Component AVAILABLE; DAW enumeration, latency and functional ASIO operation UNKNOWN |
| Service state | Windows Audio, Audio Endpoint Builder, Dolby DAX API and intelliGo Audio Service Running | **OBSERVED service state + CAPTURED**; running services do not prove a given effect processed a stream |

Historical physical topology places the Cirrus amplifier on **I2CB** and the active ASUS Precision Touchpad on **I2CC**, separate AMD I2C controller instances. This is useful topology, not proof of a cause for interference or a statement of Linux bus numbering. The September record also describes a preliminary satisfying touchpad test during nonmaximum speaker playback; it was not a controlled stress/quality test.

## Dolby user experiences and entitlement

| Feature | Behavior | Requirements / restrictions | Evidence |
|---|---|---|---|
| Dolby Access | Setup, demos and controls for supported Dolby experiences | Windows app and appropriate endpoint; controls differ by OEM/consumer version | DOCUMENTED [Dolby headphones][headphones]; package AVAILABLE/CAPTURED |
| Dolby Atmos for Headphones | Spatial rendering through ordinary compatible stereo headphones | Requires trial, purchase or qualifying bundled activation; exact entitlement here UNKNOWN | DOCUMENTED [Dolby gaming][dolbygaming] |
| OEM laptop speaker processing | Model-tuned processing for internal speakers | Licensed OEM software/driver/tuning stack; does not imply headphone purchase rights | DOCUMENTED [Dolby PC support][pcsupport]; installed stack AVAILABLE |
| Atmos home theater | Deliver compatible spatial audio to an external receiver/soundbar/display chain | Correct HDMI path, compatible receiver, app/content and selected format | DOCUMENTED [Microsoft Spatial Sound][spatial]; actual external chain UNKNOWN |
| Atmos content versus ordinary stereo | Spatially authored objects/channel beds can be rendered for the selected output | An Atmos logo or selected preset does not prove source content contains spatial metadata | DOCUMENTED [Spatial Sound][spatial], [Dolby Atmos][atmos] |
| Windows Sonic for Headphones | Microsoft's platform headphone spatializer | Supported endpoint and explicit selection; separate from Dolby licensing | DOCUMENTED [Spatial Sound][spatial]; current selection UNKNOWN |
| DTS Headphone:X | Alternative provider in Windows spatial sound | Separate provider/app/license; no installation or entitlement inferred | DOCUMENTED [Spatial Sound][spatial]; machine UNKNOWN |
| Presets and custom EQ | Tune playback for different material / user preference | Exact preset names, EQ bands and available toggles depend on Dolby Settings/Access version and endpoint | OEM profile structure CAPTURED below; current visible UI UNKNOWN |
| Dialogue, leveling and virtualization controls | Possible processing categories in OEM tuning | Configuration entries do not prove an enabled setting, public UI control or audible result | Private structural evidence CAPTURED; runtime state UNKNOWN |
| OEM software portability | Model-specific tuning accompanies the OEM installation | Dolby directs users to the PC manufacturer for model-specific drivers; installed binaries/tuning are not public redistribution material | DOCUMENTED [Dolby PC support][pcsupport] |

Microsoft Spatial Sound is a platform rendering API. The model-specific Dolby speaker APO path is a separate integration: a laptop's stereo OEM processing cannot automatically be described as an active `ISpatialAudioClient` object endpoint. The selected output provider must be verified independently. [Microsoft's endpoint and object-count boundary][spatial]

## Safely derived OEM tuning facts

The private OEM XML is preserved in the existing `pc/zenbook-um3406ga` evidence. Only structural technical facts are summarized here; no tuning coefficients, private activation/security fields or source XML are republished.

| Fact | Derived result | What it does not prove |
|---|---|---|
| Product/schema metadata | **DAX 3 Windows**, SKU label **DolbyAtmos**, XML version **3.7.1**, tuning version **10** | Current license, selected profile or complete algorithm implementation |
| Endpoint | `internal_speaker`, **48 kHz**, **2 front channels**, no subwoofer in this configuration | Speaker electrical rating, physical driver count beyond this configuration, every supported hardware format |
| Material profiles | `dynamic`, `movie`, `music`, `game`, `voice`, `voice_onlinecourse` | That every profile is currently visible/selectable in the installed UI |
| Personalization / off profiles | Three named user-profile slots and an `off` profile | That slots contain user settings or that off bypasses every hardware-protection stage |
| Processing categories | Equalization, dialogue, leveling/virtualization-related fields occur in the configuration | Whether a field is active, how its values map to controls, or how processing is scheduled |

These facts establish that a model-specific processing configuration was captured. They are not a recipe for proprietary DSP reproduction. The Windows capability harvest makes no Linux implementation or licensing claim.

## ASUS voice processing and routing

| Capability | Behavior | Conditions / boundary | Evidence |
|---|---|---|---|
| AI Noise-Cancelling Microphone | Reduce unwanted capture-side sound in supported modes | Correct input endpoint, microphone access, mode and app routing; processing location not inferred from NPU presence | DOCUMENTED [MyASUS][myasus]; historical UI AVAILABLE/OBSERVED/CAPTURED |
| AI Noise-Cancelling Speaker | Suppress nonvoice components on received/playback audio | Intended speech focus can remove music/background content; this alone is not evidence of codec failure | DOCUMENTED [ASUS speaker explanation][asusvoice]; historical UI AVAILABLE/OBSERVED/CAPTURED |
| Microphone pickup modes | Supported ASUS models can offer single/multiple-presenter, wide/360-degree or other voice modes | Generic menu is not proof of each UM3406GA mode; current menu UNKNOWN | DOCUMENTED [MyASUS][myasus] |
| App noise suppression / echo cancellation | Communications app can add its own processing | Can coexist/interact with OEM processing; no chain order inferred from multiple installed names | DOCUMENTED [audio modes][modes], [APO architecture][apo] |
| Windows communications category | App tags its stream as communications or another usage category | Driver-defined mode mapping determines supported processing; a media preset is not an application category | DOCUMENTED [audio modes][modes] |
| Microphone permissions | Control supported capture access | Desktop and packaged apps expose different permission granularity; permission is not an active-recording indicator | DOCUMENTED [Windows audio controls][audio] |
| NPU versus CPU/DSP | Several processors could participate in audio | No workload trace or vendor-specific runtime evidence establishes where this ASUS chain runs | UNKNOWN allocation; no unsupported acceleration claim |

## Windows APIs and processing architecture

| Interface / layer | Useful capability | Limits / requirements | Evidence |
|---|---|---|---|
| MMDevice | Enumerate render/capture endpoints and default device roles | Endpoint ID is session/device metadata, not portable configuration; IDs stay private | DOCUMENTED [Core Audio][core] |
| WASAPI | Create audio streams and manage audio sessions | App, endpoint, format and scheduling contract | DOCUMENTED [WASAPI][wasapi] |
| Shared mode | Mix application streams in Windows audio engine | Engine format/resampling and applicable effects can affect the path | DOCUMENTED [WASAPI][wasapi] |
| Exclusive mode | App requests direct exclusive access through the supported endpoint contract | Device/app support and user policy; cannot assume every OEM stage disappears | DOCUMENTED [WASAPI][wasapi] |
| EndpointVolume / session volume | Distinguish endpoint gain/mute from individual application levels | Default role and per-app routing differ; apparent loudness can change at several layers | DOCUMENTED [Core Audio][core] |
| APOs | User-mode real-time DSP extensions supplied by OS/OEM/vendors | Registered/installed APO is not proof of the active stream graph | DOCUMENTED [APO architecture][apo] |
| Stream/mode/endpoint effects | Effects can apply at different points in the audio graph | Exact component placement is driver-defined; do not invent a Dolby→intelliGo→Realtek order | DOCUMENTED [APO architecture][apo] |
| Raw capture mode | Request capture without adaptive noise/echo/gain processing | Supported driver contract; Microsoft permits linear response-flattening EQ, so raw is not necessarily mathematically untouched | DOCUMENTED [audio modes][modes] |
| Hardware offload / DSP / smart amp | Some work can run below the host audio engine | Requires declared support; controller, codec, DSP and amplifier are distinct | DOCUMENTED [audio modules][modules] |
| Spatial Sound | Render static beds and dynamic 3D objects for selected provider | Selected supported output and provider; not equivalent to simply playing a multichannel file | DOCUMENTED [Spatial Sound][spatial] |
| WASAPI loopback | Capture supported shared-mode rendered mix | No physical Stereo Mix device required; protected content and stream scope affect capture; not exercised | DOCUMENTED [loopback][loopback] |
| Legacy wave / DirectSound clients | Compatibility APIs remain usable by applications | Their existence does not imply a separate physical sound card or bypass of the Windows stack | DOCUMENTED [Core Audio][core] |
| Media Foundation | Media playback/codec pipeline can feed supported spatial/audio rendering | Codec installation, content protection and app implementation matter | DOCUMENTED [Spatial Sound][spatial] |
| ASIO | Pro-audio applications can use vendor-supplied interfaces | Realtek component metadata is the only local evidence here; no claimed latency result | AVAILABLE component; actual operation UNKNOWN |

## Bluetooth and output-dependent behavior

| Capability | User-facing consequence | Dependency / restriction | Evidence |
|---|---|---|---|
| A2DP | Higher-quality stereo playback | Codec negotiation requires support on both sides; an advertised codec is not proof it was selected | DOCUMENTED [Bluetooth Classic][bluetooth] |
| HFP | Concurrent headset microphone and voice-oriented playback | Opening the microphone or a communications-category stream can switch Windows from A2DP to HFP, changing quality | DOCUMENTED [Bluetooth Classic][bluetooth] |
| AVRCP | Headset buttons and media/volume control | Supported operations and absolute-volume behavior vary | DOCUMENTED [Bluetooth accessory guidelines][btaccessory] |
| LE Audio | Different Bluetooth audio transport and supported hearing-device features | Needs compatible controller/driver/accessory; ordinary Bluetooth presence does not prove LE Audio | DOCUMENTED [LE Audio][leaudio]; actual support UNKNOWN |
| USB / HDMI / Bluetooth / analog outputs | Different endpoint, format and processing choices | A laptop-speaker preset is not automatically applied or desirable on another endpoint | DOCUMENTED [Core Audio][core], [Spatial Sound][spatial] |

The remaining high-value evidence is a nonpersonal readout of Dolby's selected endpoint, preset names, exposed EQ/effect controls and activation state. User assistance has been requested. Audio quality, microphone benefit, headphone spatial rendering, selected Bluetooth codec and amplifier behavior remain **UNKNOWN** until deliberately observed; none was tested through personal media or calls.

[headphones]: https://helix.dolby.com/experience/headphones/
[dolbygaming]: https://www.dolby.com/Gaming/
[pcsupport]: https://www.dolby.com/about/support/pc-or-tablet-for-home-use/
[atmos]: https://www.dolby.com/technologies/dolby-atmos/
[spatial]: https://learn.microsoft.com/en-us/windows/win32/coreaudio/spatial-sound
[core]: https://learn.microsoft.com/en-us/windows/win32/coreaudio/about-the-windows-core-audio-apis
[wasapi]: https://learn.microsoft.com/en-us/windows/win32/coreaudio/wasapi
[apo]: https://learn.microsoft.com/en-us/windows-hardware/drivers/audio/audio-processing-object-architecture
[modes]: https://learn.microsoft.com/en-us/windows-hardware/drivers/audio/audio-signal-processing-modes
[modules]: https://learn.microsoft.com/en-us/windows-hardware/drivers/audio/implementing-audio-module-communication
[loopback]: https://learn.microsoft.com/en-us/windows/win32/coreaudio/loopback-recording
[myasus]: https://www.asus.com/global/support/faq/1045651/
[asusvoice]: https://www.asus.com/us/support/faq/1046946/
[audio]: https://support.microsoft.com/en-us/windows/hardware/audio/fix-sound-or-audio-problems-in-windows
[bluetooth]: https://learn.microsoft.com/en-us/windows-hardware/drivers/bluetooth/bluetooth-classic-audio
[btaccessory]: https://learn.microsoft.com/en-us/windows-hardware/design/accessory-guidelines/bluetooth-accessory-guidelines/bluetooth-accessory-guidelines-classic-audio
[leaudio]: https://learn.microsoft.com/en-us/windows-hardware/drivers/bluetooth/bluetooth-low-energy-audio
