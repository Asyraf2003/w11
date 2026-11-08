# Windows system, Settings and shell capabilities

Official documentation reviewed 2026-11-08. Every table entry is **DOCUMENTED**; actual installation state is **UNKNOWN** unless an explicitly dated machine note says otherwise. Settings URIs identify discoverable surfaces, not a guarantee that a page or feature is enabled. Build, edition, hardware, policy, region, account and Store versions gate individual controls.

The category denominator here is the standard Settings Home plus **11 major categories**: System, Bluetooth & devices, Network & internet, Personalization, Apps, Accounts, Time & language, Gaming, Accessibility, Privacy & security, Windows Update. Microsoft can reorganize subpages. [Category guide][settings], [official URI catalog][uris].

## System: display, sound, notifications, focus and windows

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Settings Home | Recommended controls and account/device cards | Cards vary by account, edition and managed state | [Settings][settings] |
| Display: resolution, scale, orientation | Size and arrange desktop content | Available modes come from display/driver; orientation lock requires suitable sensor | [URI catalog][uris] |
| Multiple displays | Duplicate/extend, choose primary, remember window positions | Actual monitor/dock/cable determines modes; disconnect behavior configurable | [Settings][settings] |
| Advanced display | Inspect active signal, refresh rate and display capabilities | A reported current mode is not every supported mode | [URI catalog][uris] |
| Dynamic refresh / variable refresh | Adapt refresh to workload / synchronize game frames | Different mechanisms; supported panel, driver, refresh range required | [Graphics][games] |
| HDR and SDR brightness | Render HDR content and balance SDR appearance | Supported selected display and driver; streaming support differs from HDR desktop support | [HDR][hdr] |
| HDR Calibration | Create per-display HDR calibration profile | Windows 11, HDR enabled and supported display; separate app | [Calibration][hdrcal] |
| Night light | Warm display color on schedule | Display/driver support; changes color appearance, not OLED protection | [Display settings][settings] |
| Color profile / automatic color management | Associate color profiles; manage supported app/display color | Profile, driver and app color path matter; not equivalent to ASUS Splendid gamut switching | [URI catalog][uris] |
| Graphics preferences | Per-app GPU choice and presentation options | Multiple GPUs needed for meaningful GPU selection; driver controls still apply | [Windowed games][games] |
| Sound: output and input | Choose endpoints, gain, mute and supported formats | Endpoint availability and driver properties differ | [Audio][audio] |
| Volume mixer | Per-app volume and routing | App must create an audio session; exclusive/protected paths differ | [Audio][audio] |
| Spatial sound / enhancements | Endpoint-specific rendering and effects | Provider, driver and licensing; see audio catalog | [Audio][audio] |
| Notifications | App permissions, banners, sounds, lock-screen visibility and do-not-disturb | App notification integration; focus rules can suppress banners | [Settings][settings] |
| Focus | Timed focus session and reduced distractions | Clock integration/version; not a CPU-performance mode | [Settings][settings] |
| Multitasking / Snap | Snap layouts/groups, suggested placements, Alt+Tab choices | Window resize support, display geometry and settings | [Snap][snap] |
| Virtual desktops | Separate window groupings and backgrounds | Desktops share applications/account; not isolated virtual machines | [Snap][snap], [shortcuts](01-shortcuts.md) |
| Clipboard history and sync | Retain selected copied items; optional cross-PC synchronization | Separate opt-ins, supported item formats, same Microsoft account for sync; not harvested | [URI catalog][uris] |
| Nearby sharing | Send supported files/links to nearby Windows PCs | Bluetooth discovery and Wi-Fi transfer support; different protocol from Google Quick Share | [Android catalog](06-android-integration.md) |
| Projecting to this PC | Receive supported wireless display connections | Wireless Display optional capability, Miracast-compatible hardware, consent/network rules | [URI catalog][uris] |
| Remote Desktop | Remote interactive Windows session | Hosting requires Pro/Enterprise/Education; Home can be a client | [RDP][rdp] |
| Quick Assist | Consent-based remote help | Network, app, helper sign-in; not persistent RDP hosting | [Settings][settings] |
| Shared experiences / cross-device surfaces | Continue supported linked app activities | Current replacement/rollout varies; see Android catalog | [Android catalog](06-android-integration.md) |
| Activation / About | Edition, version, activation and specification surfaces | No product keys or activation IDs collected | [URI catalog][uris] |

## Power, sleep and storage

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Power mode | Balance responsiveness and power draw | Available choices depend on platform/power plan; ASUS can synchronize fan policy | [Power mode][powermode] |
| Screen, sleep and hibernate timeouts | Independent idle actions, AC/battery policy | Firmware sleep states, hiberfile and policy determine support | [Power][power] |
| Energy saver | Reduce consumption and background activity | Threshold/manual controls; may affect notifications, apps and OEM automation | [Power][power] |
| Energy recommendations | Suggest more efficient configuration | Recommendations do not prove settings were applied | [Recommendations][energy] |
| Battery usage | Attribute recent energy use to applications | Historical estimates, not a calibrated capacity test | [Power][power] |
| Lid and power-button actions | Sleep/hibernate/shutdown or no action | Some controls remain in classic Control Panel; available states vary | [Power][power] |
| Modern Standby | Screen-off low-power S0 operation | Network-connected and disconnected policies differ; see machine note below | [Modern Standby][standby] |
| Hibernate | Save session to storage before power-off | Requires available hibernation path; not functionally exercised | [Power][power] |
| Fast Startup | Hybrid shutdown preserves kernel state | Not the same as Restart or full hibernate; platform/configuration dependent | [Power][power] |
| Presence sensing | Lock on leave/wake on approach, supported dimming | Dedicated presence hardware/driver and opt-in; camera/ALS alone does not prove support | [Presence][presence] |
| Storage categories | Show usage by apps, temporary and user files | Counts depend on selected drive/access | [Storage][storage] |
| Storage Sense / cleanup recommendations | Policy-driven temporary-file/recycle/cloud-local cleanup | Can remove data/local availability; no cleanup was run | [Storage][storage] |
| Disks and volumes | Inspect/manage disks, partitions, mount points | Some operations are destructive; this mission only documents surfaces | [Storage][storage] |
| Storage Spaces | Pool drives, optional resiliency | Appropriate physical disks/capacity; not a replacement for backup | [Storage][storage] |
| Advanced storage: content destinations | Choose default drive for supported new content | Existing files are not automatically migrated | [Storage][storage] |
| NTFS, exFAT and other filesystems | Permissions/journaling versus portable interchange | Capabilities depend on filesystem; see internals for compression, links, EFS and VSS | [Internals](07-windows-internals.md) |
| Dev Drive / ReFS | Developer-workload storage | Build/edition/storage requirements; not assumed available from SSD identity | [Dev Drive][devdrive] |
| Disk optimization | Storage-aware maintenance, including SSD trim | Scheduled/platform-specific; no maintenance triggered | [Storage][storage] |

## Bluetooth & devices; Network & internet

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Bluetooth devices | Pair/manage audio, input and other peripherals | Radio, driver, supported profile and explicit pairing | [Device categories][settings] |
| Bluetooth LE Audio / hearing devices | Supported efficient audio/hearing-device experience | Compatible PC radio, driver and accessory; classic Bluetooth presence is insufficient | [Accessibility][accessibility] |
| Printers and scanners | Queue/default management and scanning | Driver/IPP/network support; no print jobs or documents inspected | [URI catalog][uris] |
| Cameras | Per-camera controls and supported effects | Windows Studio Effects and OEM effects have separate requirements | [AI catalog](03-copilot-ai.md) |
| Mouse and touchpad | Buttons, pointer speed, scrolling, taps and gestures | Precision gesture support and OEM filters; see shortcuts | [Gestures][gestures] |
| Touch / Pen & Windows Ink | Touch gestures, pen shortcuts, inking | Digitizer/pen hardware required; actual touch model UNKNOWN | [Gestures][gestures] |
| AutoPlay | Default action for removable media/devices | File/device handlers; does not imply content was read | [URI catalog][uris] |
| USB / USB4 hubs and devices | Device notifications and supported USB4 topology surface | Compatible host/dock/cable; enumeration is not interoperability proof | [Internals](07-windows-internals.md) |
| Mobile devices | Link phones, connected camera, Explorer access | Link to Windows/version/consent; see Android catalog | [Android catalog](06-android-integration.md) |
| Wi-Fi | Join remembered networks; manage known-network policy | Bands, security and roaming depend on adapter, driver, AP and jurisdiction | [Networking][network] |
| Ethernet | Wired link and adapter configuration | Often requires USB adapter/dock on thin laptops | [Networking][network] |
| Network profile | Public/private discovery and sharing posture | A private profile alone does not create a share or open all firewall rules | [Networking][network] |
| IP / DNS configuration | DHCP/static addresses and supported encrypted DNS settings | Network/provider compatibility; no addresses harvested | [Networking][network] |
| VPN | Connect supported built-in/provider VPNs | Server, credentials, protocol, routes and policy | [Networking][network] |
| Proxy | Per-user/system/application-dependent HTTP proxy behavior | Apps can use different networking stacks; shell proxy failure is not proof all apps are offline | [Networking][network] |
| Airplane mode | Group radio state control | Radio-specific toggles and hardware policy | [Networking][network] |
| Mobile hotspot | Share PC internet over supported Wi-Fi/Bluetooth | Adapter/AP mode, upstream connection, power and policy | [Networking][network] |
| Cellular/eSIM | Mobile data, SIM and roaming controls | Actual WWAN modem/eSIM required; not inferred from Wi-Fi | [URI catalog][uris] |
| Metered connection / data usage | Mark cost-sensitive links and track usage | Changes app/update behavior; not a hard universal bandwidth cap | [Networking][network] |
| Advanced network / sharing | Adapter details, SMB discovery/shares, advanced options | Firewall, credentials, permissions and SMB policy | [Sharing][sharing] |

## Personalization, Start, taskbar and Explorer

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Background, themes, colors | Wallpaper/slideshow/Spotlight, light/dark, accent and transparency | Online content and activation/policy can affect choices | [Settings][settings] |
| Lock screen | Background, supported app status and screen timeout links | Account/policy/version; no personal lock-screen content captured | [URI catalog][uris] |
| Start | Pins, folders, recommendations, supported phone companion and layout options | Layout changes across builds; recommendations are not migration requirements | [Settings][settings] |
| Taskbar | Alignment, auto-hide, badges, tray icons and multi-monitor behavior | Some classic Win10 placements are not native Win11 options | [Settings][settings] |
| Widgets | Personalized information and supported widget providers | Web Experience Pack, network, account/region and provider | [Settings][settings] |
| Explorer tabs / Home / Gallery | Navigate tabs, pinned/recent entries and photo views | Build, index and cloud-provider integration | [Shortcuts](01-shortcuts.md) |
| Explorer details/preview/search | Metadata panes, preview handlers, filters and indexed search | File handler/index permissions; preview is not guaranteed for every format | [URI catalog][uris] |
| Explorer context menu / Share | Compact commands, legacy options and registered share targets | App registration; legacy menu via Shift+right-click/Show more options | [Shortcuts](01-shortcuts.md) |
| ZIP and modern archive support | Browse/extract supported archive types; newer builds add creation options | Format/encryption/create support differs by build; not every archive needs a third-party app | [Compression][archives] |
| Recycle Bin | Recover ordinary deleted local items | Bypass/size/location rules; not all deletes are recoverable | [Shortcuts](01-shortcuts.md) |
| Fonts / text input | Installed fonts, touch-keyboard theme and typing customization | Language packs and font licensing; no font binaries republished | [URI catalog][uris] |
| Dynamic Lighting | Coordinate compatible device lighting | Compatible HID LampArray hardware; not equivalent to ASUS keyboard backlight support | [Settings][settings] |
| Device usage | Tailor suggestions to declared usage | Optional personalization; does not add hardware capabilities | [Settings][settings] |

## Apps, accounts, backup and language

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Installed apps | Manage app uninstall/repair/reset when supported | Win32 installers and packaged apps have different lifecycle controls | [Settings][settings] |
| Default apps | Associate extensions, URI protocols and browser defaults | Per-user associations and app registrations | [Defaults][defaults] |
| Startup apps | Control supported logon startup entries | Not an exhaustive list of services/tasks/driver startups | [URI catalog][uris] |
| Optional features | Add/remove Windows capabilities | Payload availability, servicing state and often elevation | [Internals](07-windows-internals.md) |
| Advanced app settings / execution aliases | App-source controls, archive-app behavior and executable aliases | Alias presence does not prove a working app installation | [URI catalog][uris] |
| Apps for websites / video playback | Route registered website links and video preferences | App association, codec, HDR and network support | [URI catalog][uris] |
| Microsoft Store / WinGet | Discover, install and update software | Store policy/region, source availability, per-package licensing | [Internals](07-windows-internals.md) |
| Local / Microsoft / work-school accounts | Different sign-in and connected-service identities | Account type affects sync/management; no account contents harvested | [Settings][settings] |
| Windows Hello / passkeys | PIN or supported biometrics, passwordless service authentication | IR/fingerprint hardware where needed; PIN is device-scoped, not cloud password | [Hello][hello] |
| Dynamic Lock | Lock when paired phone becomes distant | Bluetooth pairing; timing/proximity is approximate, not presence certification | [Hello][hello] |
| Family / other users / assigned access | Separate profiles, family controls, supported kiosk configuration | Edition/account/management dependencies | [URI catalog][uris] |
| Windows Backup | Restore supported folders, preferences and app pins on another Windows PC | Consumer personal Microsoft account; work/school path differs; OneDrive quota | [Backup][backup] |
| OneDrive folder backup | Synchronize selected known folders | Sync propagates changes; not a full disk image; storage/account needed | [Backup][backup] |
| OneDrive Files On-Demand | Cloud placeholders versus downloaded/always-local files | Network required for online-only files; an Explorer entry may contain no local payload | [Backup][backup] |
| Preference sync | Selected accessibility, personalization, language and other preferences | Same supported account and consent; not every application setting | [Backup catalog][backupcatalog] |
| File History / recovery drive | File-version protection / boot recovery media | Different from Windows Backup; external storage and configuration | [Backup/recovery][recovery] |
| Date & time / time zone | Clock synchronization, automatic zone and calendar display | Network/location policy can affect automation | [URI catalog][uris] |
| Language & region | Display language, regional formatting and installed keyboard layouts | **Home Single Language** license limits changing Windows display language; input methods remain separate | [Language][language] |
| Typing / speech | Suggestions, spelling, touch keyboard, speech packages and voice typing | Language/model/cloud dependencies; see AI catalog | [AI catalog](03-copilot-ai.md) |

## Accessibility, privacy, security, gaming and updates

| Capability / surface | User-facing behavior | Requirements and limits | Source |
|---|---|---|---|
| Vision controls | Text size, pointer/cursor, contrast, color filters and animation/transparency options | App support and per-user settings | [Accessibility][accessibility] |
| Magnifier / Narrator | Magnification, reading and screen-reader navigation | Voice/language and app UI Automation quality | [Accessibility][accessibility] |
| Hearing controls | Mono audio, visual alerts and captions | Caption styling differs from speech recognition/translation | [Accessibility][accessibility] |
| Voice access / OSK / keyboard filters | Spoken control, on-screen keys, Sticky/Filter/Toggle Keys | Models, languages and opt-ins; voice access is distinct from cloud dictation | [Accessibility][accessibility] |
| Mouse Keys / eye control | Alternative pointer operation | Numeric keypad / compatible eye tracker; not inferred from IR webcam | [Accessibility][accessibility] |
| App permissions | Camera, microphone, location, contacts and other access controls | Packaged/desktop-app controls differ; permission does not mean sensor actively used | [Settings][settings] |
| Search permissions / indexing | Indexed locations, safe-search/cloud options, history controls | Enhanced/semantic search adds hardware/model gates | [AI catalog](03-copilot-ai.md) |
| Diagnostics, feedback, activity/typing personalization | Control supported diagnostic and personalization flows | Required diagnostic data and organizational policy differ from optional choices | [Settings][settings] |
| Find my device | Locate a registered PC through Microsoft account | Location, connectivity, supported account and prior enablement | [URI catalog][uris] |
| Defender antivirus / firewall | Malware protection and network filtering | Another registered antivirus can change Defender mode; installed service is not current protection proof | [Security][security] |
| App/browser protection | Reputation protection, SmartScreen, supported Smart App Control and exploit controls | Smart App Control has installation/evaluation conditions; not automatically active | [Security][security] |
| Device security | Secure Boot, security processor, core isolation/memory integrity surfaces | Firmware/TPM/virtualization and compatible drivers; current values require read-only proof | [Security][security] |
| Device encryption / BitLocker | Encrypt supported volumes and protect offline data | Device Encryption can exist on Home; full BitLocker management has edition gates; no keys collected | [Encryption][encryption] |
| Game Mode / Game Bar / Captures | Game scheduling policy, overlay, screenshots and app recording | Capture excludes some desktop/protected contexts; background capture needs opt-in | [URI catalog][uris] |
| Auto HDR / windowed optimizations / VRR | HDR conversion and improved presentation for supported games | HDR/VRR display, eligible game API and driver; not the same as NPU Auto SR | [Games][games] |
| Controller and Xbox ecosystem | Gamepad input, Store/Xbox app/game services | Hardware, game, account and optional subscription determine experience | [URI catalog][uris] |
| Windows Update | Quality/feature/security updates and some drivers | Pause/active-hours/restart policy; eligibility and rollout matter | [Settings][settings] |
| Update advanced options | Optional updates, delivery optimization, restart notifications and servicing controls | Edition/management policy and payload availability | [URI catalog][uris] |
| Recovery: Windows Update reinstall | Reinstall current OS preserving apps/files/settings | Supported builds, internet, power and management restrictions | [Repair reinstall][repair] |
| Reset this PC / WinRE / advanced startup | Reset or enter recovery tools | Retain/remove choices differ; recovery can destroy data; not run | [Recovery][recovery] |
| System Restore | Restore supported system configuration checkpoints | Protection/restore points must already exist; not user-file backup | [Recovery][recovery] |
| Developer surfaces | Developer Mode, terminal, device discovery and developer settings | Some options moved to System > Advanced in newer builds; no development settings enabled | [URI catalog][uris] |
| Virtualization / WSL / Sandbox | Linux environment and isolated Windows workloads | CPU/firmware/edition/feature dependencies; see internals | [Internals](07-windows-internals.md) |

## Machine evidence and important drift

The **2026-11-05** private differential capture records Windows 11 **Home Single Language, build 26200**, Ryzen AI 7 445 (6 cores/12 threads), 16 GiB physical memory class, Radeon 840M and a roughly 1 TB Samsung NVMe SSD: **AVAILABLE + CAPTURED historically**, current refresh **UNKNOWN** where collection is denied.

Fresh **2026-11-08** registry metadata reports **26H2, build 26300, UBR 9818, CoreSingleLanguage**; `wsl --version` independently reports host **10.0.26300.9818**. These supersede the November 5 build as a current software reference. `Get-ComputerInfo` returned legacy `Windows 10 Home Single Language`/`2009` fields and null build/hardware fields in the initial restricted session; those compatibility fields are not evidence that this is Windows 10. After the user opened session permissions, fresh CIM succeeded and confirmed Windows 11 Home Single Language, UM3406GA, the Ryzen/Radeon hardware and BIOS recorded above. The original denied queries remain preserved alongside the successful refresh.

Power-state evidence changed between captures. September reported **S0 Network Connected**; November 5 and fresh November 8 report **S0 Network Disconnected**, Hibernate and Fast Startup, with S1/S2/S3 unavailable. The fresh report explicitly says connected standby is disabled by policy; no policy was changed. Preserve the latest dated report; do not assume connected standby remains available. This is an exposed-state report, not a measured overnight-drain or successful resume test.

Historical Quick Settings observations include Wi-Fi, Bluetooth, airplane mode, energy saver, night light, mobile hotspot, Nearby sharing, Cast/Project, accessibility, live captions and Studio Effects. These establish the controls were exposed; they do not establish paired-device interoperability or enabled processing.

[settings]: https://support.microsoft.com/en-us/windows/experience/exploring-windows-settings
[uris]: https://learn.microsoft.com/en-us/windows/apps/develop/launch/launch-settings
[power]: https://support.microsoft.com/en-us/windows/experience/power-battery/power-settings-in-windows-11
[powermode]: https://support.microsoft.com/en-us/windows/experience/change-the-power-mode-for-your-windows-pc
[energy]: https://support.microsoft.com/en-us/windows/experience/power-battery/learn-more-about-energy-recommendations
[storage]: https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/storage-settings-in-windows
[standby]: https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/modern-standby
[presence]: https://support.microsoft.com/en-us/windows/privacy/managing-presence-sensing-settings-in-windows-11
[hdr]: https://support.microsoft.com/en-gb/windows/hardware/display-graphics/hdr-settings-in-windows
[hdrcal]: https://support.microsoft.com/en-us/windows/hardware/display-graphics/calibrate-your-hdr-display-using-the-windows-hdr-calibration-app
[audio]: https://support.microsoft.com/en-us/windows/hardware/audio/fix-sound-or-audio-problems-in-windows
[network]: https://support.microsoft.com/en-gb/windows/experience/connectivity-networking/essential-network-settings-and-tasks-in-windows
[sharing]: https://support.microsoft.com/en-gb/windows/experience/connectivity-networking/file-sharing-over-a-network-in-windows
[defaults]: https://support.microsoft.com/en-us/windows/apps/change-default-apps-in-windows
[accessibility]: https://support.microsoft.com/en-us/accessibility/windows/discover-windows-accessibility-features
[security]: https://support.microsoft.com/en-us/windows/security/windows-security/windows-security-app-overview
[encryption]: https://support.microsoft.com/en-us/windows/security/encryption/device-encryption-in-windows
[games]: https://support.microsoft.com/en-us/windows/hardware/display-graphics/optimizations-for-windowed-games-in-windows-11
[snap]: https://support.microsoft.com/en-us/windows/experience/snap-your-windows
[backup]: https://support.microsoft.com/en-us/windows/experience/backup-recovery/back-up-and-restore-with-windows-backup
[backupcatalog]: https://support.microsoft.com/en-us/windows/experience/backup-recovery/windows-backup-settings-catalog
[recovery]: https://support.microsoft.com/en-us/windows/experience/backup-recovery/backup-restore-and-recovery-in-windows
[repair]: https://support.microsoft.com/en-gb/windows/deployment/install-upgrade/fix-issues-by-reinstalling-the-current-version-of-windows
[rdp]: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remotepc/remote-desktop-supported-config
[devdrive]: https://learn.microsoft.com/en-us/windows/dev-drive/
[language]: https://support.microsoft.com/en-us/windows/hardware/input-devices/check-whether-a-version-of-windows-supports-multiple-languages
[hello]: https://support.microsoft.com/en-us/windows/security/windows-security/windows-security-app-overview
[archives]: https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/zip-and-unzip-files
[gestures]: https://support.microsoft.com/en-us/windows/hardware/input-devices/touch-gestures-for-windows
