# Windows ↔ Android capabilities

Official-source review: **2026-11-08**. This is a capability reference, not a record of personal phone content. No pairing, messages, photos, clipboard, contacts, or account contents were inspected for this chapter.

**Scope:** Windows ↔ Android as an ecosystem, including vendor-specific restrictions where the official feature contract requires them. This is not an assessment of the owner's personal phone. Phone model/OS examples in official compatibility lists describe eligibility classes; a personal-device inventory or pairing test is not required to complete this reference.

`DOCUMENTED` means the vendor describes the capability. **Actual UM3406GA + phone availability and behavior remain `UNKNOWN` unless the separate runtime/status inventory supplies evidence.** Installing Phone Link, GlideX, a Bluetooth driver, or ADB does not prove successful pairing or an enabled feature. Android model, OS build, app version, region, account type, permissions, and PC update can each change availability.

## Phone Link and Windows mobile-device integration

Baseline: Phone Link on Windows and Link to Windows on Android pair through a personal Microsoft account. Microsoft's current general requirements specify Android 10+, Windows 11 (or supported Windows 10 builds), and the same Wi-Fi network. Some features permit mobile-data synchronization; this is not evidence that every feature works remotely. Work/school accounts and multiple Android profiles are not supported by the documented Phone Link experience. [Setup][PL]

The transport column names the documented connection requirement; it does not claim an independently captured wire protocol.

| Feature | Behavior | Transport | Requirements and restrictions | Evidence |
|---|---|---|---|---|
| Pairing and feature permissions | Choose which phone functions synchronize; permissions can be revoked separately | Microsoft-account pairing; Wi-Fi baseline | Link to Windows, personal account; Android 13+ notification runtime permission is additional to notification-access permission | DOCUMENTED [Setup][PL] |
| Notifications | View phone alerts in Windows, dismiss them on both devices, choose per-app feeds/banners, use supported inline actions | Phone Link connection | Android notification access; actions depend on app and preinstalled versus downloaded Link to Windows | DOCUMENTED [Manage notifications][NOTIFY] |
| Sensitive notification restrictions | Android can withhold sensitive notification text, including verification codes | Android notification filtering before synchronization | Android 15+; hidden content must be viewed on the phone; do not treat empty text as failed hardware | DOCUMENTED [Restrictions][SENSITIVE] |
| SMS and MMS | Read/reply from the PC; attach supported images/GIFs | Phone Link connection; phone/carrier sends messages | Message permission; documented view covers the last 30 days; messages cannot be managed/deleted from the PC | DOCUMENTED [Messages][SMS] |
| RCS in Phone Link | Supported rich messaging on selected Samsung configurations | Phone Link plus phone's RCS/carrier service | Eligible model, **Samsung Messages as default**, operator and country support; not a general Google Messages or all-Android promise | DOCUMENTED [Supported devices][DEVICES] |
| Calls | Dial and answer phone calls through PC microphone/speakers; call history and in-call keypad | **Bluetooth** between phone and PC | Bluetooth on both sides and Android permissions; phone still provides telephony; not a substitute for primary/emergency telephone service | DOCUMENTED [Calls][CALLS] |
| Recent call history | Show recent calls without editing/deleting the phone log | Bluetooth / Phone Link | Microsoft's Android instructions describe the last 90 days; not a complete archive | DOCUMENTED [Calls][CALLS] |
| Recent phone photos | View, save, copy, share, or open a phone photo for PC editing | Phone Link connection | Photo/file permissions; PC edits save a new file; the feature is not a cloud-photo-backup browser | DOCUMENTED [Photos][PHOTOS] |
| Delete a phone photo | Explicit PC action can delete the phone's local photo | Phone Link connection | Single-photo deletion; cloud backup is unaffected; phone trash behavior depends on the Android gallery | DOCUMENTED [Photo deletion][PHOTOS] |
| Insert media into Office | Pick phone media from supported Office web/desktop insertion flows | Link to Windows connection / pairing | Android 10+, Link to Windows; Office app/version and insertion flow matter | DOCUMENTED [Supported experiences][DEVICES], [Photos][PHOTOS] |
| File sharing through share sheets | Windows Share → Phone Link; Android Share → Link to Windows → PC | Phone Link connection | Windows 11, Android 10+, Link to Windows ≥1.24032.518.0 and Phone Link ≥1.24032.156.0; locally stored files transfer, cloud-only items share links | DOCUMENTED [Content transfer][TRANSFER] |
| Clipboard synchronization | Replace the other device's clipboard with copied text or images | Wi-Fi / permitted mobile data | Selected supported phones, explicit toggle; images over 1 MB resized; formatting/size restrictions and Secure Folder boundaries | DOCUMENTED [Content transfer][TRANSFER] |
| Drag and drop with phone windows | Transfer files through supported mirrored screens/apps | Wi-Fi phone screen / Apps | Selected OEM devices; receiving app/file type matters; touch/pen drag is not supported by this flow | DOCUMENTED [Content transfer][TRANSFER] |
| Phone screen | Mirror and interact with the Android screen using PC input | Same Wi-Fi network | Supported preinstalled Link to Windows device, Android 10+, DirectX 11 PC GPU; selected markets; not every Android phone | DOCUMENTED [Phone screen][SCREEN] |
| Individual Android app windows | Stream phone apps into separate PC windows and pin entry points to Start/taskbar | Wi-Fi | Eligible Samsung, HONOR, OPPO, ASUS, vivo, Xiaomi models; apps continue executing **on the phone** | DOCUMENTED [Apps setup][APPSSETUP], [Apps behavior][APPS] |
| Multiple streamed apps | Open several supported phone apps beside Windows apps | Wi-Fi | Android 11+ and a specifically eligible device/build; current device list is authoritative; Android version alone is insufficient | DOCUMENTED [Apps setup][APPSSETUP] |
| Recent apps | Launch eligible recently used phone apps from Phone Link/tray | Wi-Fi | Separate model/build requirements; some apps/input behaviors are incompatible | DOCUMENTED [Apps behavior][APPS] |
| Phone media remote controls | Previous/play-pause/next controls for supported Android players | Notification-backed Phone Link control | Notification access and compatible media app; audio normally remains on the phone or its attached speaker | DOCUMENTED [Audio controls][AUDCTRL] |
| Audio from Apps / phone screen | Hear supported streamed app audio through the PC | Phone screen / Apps connection | Documented Samsung One UI 5+ path; app versions and audio permissions required; distinct from simple media remote control | DOCUMENTED [Apps audio][APPS] |
| Android camera as PC webcam | Connected phone camera appears as a selectable camera to PC apps | Wireless linked-device connection | Windows 11, Android 10+, Link to Windows ≥1.24022.0; enable “Use as connected camera” under Mobile devices; camera permissions | DOCUMENTED [Connected camera][CAMERA] |
| Wireless phone files in Explorer | Browse, open, copy, move, rename and delete Android files in File Explorer | Wireless Link to Windows connection | Windows 11, Android 11+, Link to Windows ≥1.24072.258.0; “Show mobile device in File Explorer”; only one phone displayed at once | DOCUMENTED [Explorer][EXPLORER] |
| Explorer phone-file recovery/cache | Connected-device recycle folder provides a 30-day recovery window; local PC copies can exist | Same integration | Deleting from the connected phone is a real file action; documented cache cleanup first disables Explorer exposure | DOCUMENTED [Explorer][EXPLORER] |
| Instant Hotspot | Put an eligible phone's hotspot in the Windows Wi-Fi menu without repeated password entry | Bluetooth setup/discovery; **Wi-Fi hotspot** data | Windows 11 22H2 build 22621+, BT/Wi-Fi, required app versions; selected Samsung/HONOR/OPPO/OnePlus/realme/vivo OS builds; hotspot-capable SIM plan | DOCUMENTED [Instant Hotspot][HOTSPOT] |
| Start-menu phone companion | Battery/connectivity view, shortcuts to phone functions and Send Files | Android Wi-Fi / Phone Link | Windows 11, Microsoft account, supported Phone Link version; vendor describes gradual rollout; configurable under Personalization → Start | DOCUMENTED [Start companion][START] |
| Cross-device Resume | Taskbar phone-badged prompt continues a supported phone activity on PC | Internet plus linked Mobile devices | Windows 11, Android 10+, Link to Windows; supported app/action only; Settings → Apps → Resume has per-app controls | DOCUMENTED [Resume][RESUME] |
| Resume expansion in 2026 | Continue Spotify, supported browsing, and eligible online Office files opened from mobile Copilot | Internet / app services | Microsoft release notes add selected HONOR/OPPO/Samsung/vivo/Xiaomi file flows; PC Office app or browser fallback; rollout/build dependent | DOCUMENTED [2026 release notes][RESUME2026] |
| Mobile-data sync | Allow supported content synchronization away from Wi-Fi | Mobile data / Internet | User opt-in; metered-data charges possible; not a blanket exception for Wi-Fi-only screen/app features | DOCUMENTED [Setup][PL] |

Device lists evolve. “ASUS supported” in a phone list refers to named **ASUS phones**, not proof that every Android phone paired to an ASUS laptop gains those features. Recent Microsoft setup and usage pages can list different subsets; use the feature-specific current support list and actual UI before claiming availability. [Device list][DEVICES]

## File transfer and nearby mechanisms

| Feature | Behavior | Transport | Requirements and restrictions | Evidence |
|---|---|---|---|---|
| **Windows Nearby sharing** | Share files and links between nearby **Windows PCs** | Bluetooth or same private-network Wi-Fi | Enable on both PCs; own-devices mode uses Microsoft account; this is a different service from Google Quick Share | DOCUMENTED [Windows Nearby][NEARBY] |
| **Google Quick Share for Windows** | Send/receive files and folders with Android, nearby people, or own devices | Bluetooth discovery plus Wi-Fi/Ethernet network | Android 6+, 64-bit Windows 10+; ARM requires Windows 11+; Google currently specifies same network and ~5 m proximity; BLE extended advertising can affect discovery | DOCUMENTED [Quick Share][QUICK] |
| Quick Share consent/account behavior | Transfer encryption; accept incoming requests; own-account transfers can auto-accept | Same Quick Share connection | Visibility matters; Google account unlocks all options; run as ordinary user, not administrator; Samsung PCs use Samsung's app | DOCUMENTED [Quick Share][QUICK] |
| Bluetooth file transfer | Transfer selected files without Internet; Windows provides explicit send/receive flow | Bluetooth | Pair devices; phone must implement compatible receiving/sending; Windows must be waiting in Receive files mode | DOCUMENTED [Bluetooth files][BTFILE] |
| USB file transfer | File Explorer can copy exposed Android files after phone unlock and USB-mode selection | USB data cable; normally MTP | Select File transfer on phone; charge-only cables cannot transfer; does not expose private app storage as an ordinary disk | DOCUMENTED [USB procedure][USB], [WPD][WPD] |
| PTP / portable-device driver framework | Windows supports picture/media object transfer through WPD class protocols | PTP/MTP over USB and other supported transports | Phone must expose that mode; protocol support in Windows does not prove that this phone enables every transport | DOCUMENTED [WPD][WPD] |
| Cloud file access | Reach the same uploaded files from Android and Windows/web clients | Internet | Google Drive/Photos or OneDrive account and storage; cloud operation, not nearby transfer; permissions and quota apply | DOCUMENTED [Google file choices][USB], [OneDrive mobile][ONEDRIVE] |
| OneDrive camera backup | Upload phone photos/videos for access elsewhere | Internet / Wi-Fi or permitted mobile data | Photo permission, background app and storage quota; **one-way backup**, not two-way local gallery synchronization; one camera-backup account at a time | DOCUMENTED [Camera backup][ONEDRIVECAM] |
| Samsung Gallery → OneDrive change | Existing uploaded media remains in OneDrive; new automatic uploads use OneDrive Camera backup under current guidance | Cloud | Check current Samsung/OneDrive instructions instead of assuming historical Gallery sync still applies | DOCUMENTED [Service change][GALLERY] |

**Interoperability boundary:** a Bluetooth pairing, Wi-Fi Direct-capable adapter, or “Nearby sharing” Windows switch does not prove Google Quick Share, Phone Link file transfer, or Android mirroring works. These have separate applications, permissions and protocols.

## Networking, casting, and connected cameras

| Feature | Behavior | Transport | Requirements and restrictions | Evidence |
|---|---|---|---|---|
| Ordinary phone hotspot | Windows joins the phone like a Wi-Fi router | Wi-Fi; phone cellular uplink | Phone hotspot, compatible band/security, tethering entitlement; independent of Instant Hotspot OEM eligibility | DOCUMENTED [Android tethering][TETHER] |
| USB tethering | Phone presents an Internet connection through USB | USB networking | Android USB tethering enabled, data cable and usable network driver; carrier restrictions/data charges can apply | DOCUMENTED [Android tethering][TETHER] |
| Bluetooth tethering | Windows obtains connectivity from phone hotspot over Bluetooth | Bluetooth PAN | Both devices paired; phone shares over Bluetooth; Windows Devices → phone → Personal Area Network → Join | DOCUMENTED [Windows BTPAN][BTPAN], [Android tethering][TETHER] |
| Wi-Fi Direct primitive | Compatible apps form peer-to-peer links without an access point/Internet | Wi-Fi P2P | Android device/API/permissions and compatible PC application required; radio support alone provides no general file browser | DOCUMENTED [Android Wi-Fi Direct][DIRECT] |
| Android → Windows Miracast projection | Compatible phone can project to a Windows wireless-display receiver | Wi-Fi / Miracast | Phone must support Miracast; Windows compatible Wi-Fi/graphics and Wireless Display optional feature/app; receiver policy/consent matter | DOCUMENTED [Windows projection][CAST] |
| Windows → wireless display | Win+K selects a compatible TV/display; Win+P chooses duplicate/extend modes | Miracast | Does not make a generic Android phone a Windows external monitor; receiver support required | DOCUMENTED [Windows projection][CAST] |
| Google Cast | Android apps cast to compatible Chromecast/Google Cast receivers | Same Wi-Fi network | Separate receiver ecosystem; Microsoft's Miracast instructions do not establish Google Cast receiver support on the PC | DOCUMENTED [Google Cast][GOOGLECAST] |
| USB phone webcam | Supported Pixel phone exposes a standard camera to a UVC-capable PC | **USB Video Class** | Supported phone with Webcam USB mode and data cable; distinct from Link to Windows connected camera; not promised for every Android device | DOCUMENTED [Pixel UVC][UVC] |

Mirroring sources can intentionally hide protected or app-restricted content. No DRM or privacy restriction was bypassed or tested here. A future physical test should use a blank test screen or synthetic media.

## ASUS and other OEM continuity

| Feature | Behavior | Transport | Requirements and restrictions | Evidence |
|---|---|---|---|---|
| GlideX Mirror / Extend | Mirror phone to PC or use mobile device as extra display | Wi-Fi or supported USB path | Windows 10/11 64-bit 1909+, H.264 graphics, Android 9+; app permissions; Android USB path requires debugging approval | DOCUMENTED [GlideX introduction][GLIDEX] |
| GlideX Unify Control / files / URLs | Share PC input across supported devices and transfer files/text/links | Supported LAN/Wi-Fi; feature-specific Bluetooth/USB | Both GlideX clients; exact connection/permission requirements depend on feature; generic PC support differs from ASUS Exclusive entitlement | DOCUMENTED [GlideX overview][GLIDEXWEB], [Introduction][GLIDEX] |
| GlideX communication / Shared Cam / remote access | Vendor alternatives for calls, notifications, phone camera and remote PC/file access | Bluetooth for communication; supported network paths for camera/remote features | ASUS Exclusive vs General edition limits; PC installation alone does not prove active device entitlement or working connection | DOCUMENTED [GlideX overview][GLIDEXWEB] |
| GlideX app streaming on selected ASUS phones | Up to four phone app windows, drag/drop and bidirectional text clipboard | GlideX connection | ASUS lists Zenfone 11 Ultra, Zenfone 12 Ultra, ROG Phone 9 for this exclusive flow; app drag/file support varies | DOCUMENTED [Selected phone features][GLIDEXAPPS] |
| Samsung DeX for PC | Historical phone desktop on Windows using PC client | USB / supported wireless path | **No longer supported on One UI 7+**; One UI 6 client remains without technical support; direct DeX to TV/monitor is a separate capability | DOCUMENTED; UNAVAILABLE on documented One UI 7+ configurations [Samsung change notice][DEX] |

## Development interfaces and account continuity

| Feature | Behavior | Transport | Requirements and restrictions | Evidence |
|---|---|---|---|---|
| ADB over USB | Development shell, application deployment/debugging and file operations | USB; local ADB client/server → Android daemon | SDK Platform Tools, USB debugging and on-phone computer authorization; vendor USB driver may be required; powerful access is separate from MTP | DOCUMENTED [ADB][ADB] |
| Wireless debugging | Pair workstation by code/QR, then debug without cable | Same Wi-Fi / TCP | Phones Android 11+; recent Platform Tools and approved pairing; network isolation/discovery can block connection | DOCUMENTED [ADB][ADB] |
| ADB Wi-Fi 2.0 | Improved discovery and reconnection on user-trusted networks | Wi-Fi, current ADB stack | Google's 2026 documentation specifies Android 17, Platform Tools 37.0.0 and Android Studio Quail 3+; do not assume an older phone has it | DOCUMENTED [Google announcement][ADB2] |
| Edge browser synchronization | Share selected bookmarks, history, tabs and other supported browser data across Android and PC | Account/cloud Internet service | Same account and sync enabled; item availability/policy varies; this is not phone-screen mirroring | DOCUMENTED [Edge sync][EDGE] |
| SwiftKey Cloud Clipboard | Synchronize copied text between SwiftKey Android and Windows | Microsoft account/cloud | Compatible SwiftKey, Windows clipboard sync and personal Microsoft account; most recent cloud clip retained for one hour; separate from Phone Link OEM clipboard | DOCUMENTED [SwiftKey clipboard][SWIFTKEY] |
| Google Messages for web | Use phone messaging in a Windows browser | Internet between web client and connected phone/service | Current Google Messages, supported browser, Google-account device pairing; one active computer; local encrypted browser cache; separate from Phone Link RCS eligibility | DOCUMENTED [Messages web][MESSAGESWEB] |
| Windows Subsystem for Android | Historical on-PC Android runtime, distinct from streaming a real phone | Local virtualization | Microsoft says WSA and Amazon Appstore ceased availability in Microsoft Store on **2025-03-05**; archived docs describe previous behavior, not a current supported install path | DOCUMENTED; UNAVAILABLE from the documented Store distribution [Archived WSA][WSA] |

## Fresh Windows-side evidence, 2026-11-08

| Component / capability | Actual evidence | Status and limitation |
|---|---|---|
| Phone Link | Current-user `Microsoft.YourPhone` **1.26092.119.0** and Phone Link launcher | AVAILABLE + CAPTURED; pairing and every phone-content function UNKNOWN |
| Cross-device infrastructure | `MicrosoftWindows.CrossDevice` **1.26101.77.0**; Connected Devices Platform and Phone services Running | AVAILABLE + CAPTURED; service state OBSERVED, successful integration UNKNOWN |
| GlideX | Current-user app **4.3.5.0**, ASUS GlideX launcher; service installer separately **4.1.2.0** | AVAILABLE + CAPTURED; phone companion, connection and individual feature use UNKNOWN |
| Wireless hardware | MediaTek MT7922/RZ616 Wi-Fi 6E driver **3.5.2.1383**; MediaTek Bluetooth adapter driver **1.1146.2.576** | AVAILABLE + CAPTURED; accessory/phone interoperability not exercised |
| Wi-Fi Direct | Native capability report advertises Device, Group Owner and Client roles, including GO on 5 GHz | AVAILABLE advertised interfaces + CAPTURED; not a verified Phone Link/Quick Share/Miracast session |
| Miracast prerequisite flags | `netsh wlan show drivers` reports Wireless Display graphics and Wi-Fi support | AVAILABLE reported prerequisites + CAPTURED; actual projection UNKNOWN |
| Receiving Windows Wireless Display | Optional capability `App.WirelessDisplay.Connect` is **NotPresent** | UNAVAILABLE as an installed optional receiver in this capture; does not negate outbound Cast support or underlying Wi-Fi Direct |
| Bluetooth profiles | Windows driver inventory includes PAN, RFCOMM, A2DP and hands-free components | AVAILABLE + CAPTURED components; active codec, phone calls and tethering UNKNOWN |
| Quick Share | No matching entry in the narrowly filtered current-user Appx/selected uninstall inventory | UNKNOWN overall installation; this is not an exhaustive all-user/portable-app search |
| Per-phone eligibility | Official matrices document OEM/Android/app restrictions; no personal device evaluation performed | Personal-phone verification is outside this reference's scope. No messages, photos, clipboard data, contacts or phone identifiers were read |

## Remaining verification gaps

- For a future concrete deployment, compare the chosen Android model/OS/app versions against the linked official matrix. No personal-phone collection is pending for this ecosystem harvest.
- Current Phone Link/cross-device/GlideX PC installation is verified above; Quick Share exposure remains UNKNOWN. Settings-only inspection can refine this later without opening feeds or galleries.
- Use synthetic test files, test notifications and a blank phone screen for any later transfer/mirroring test. Calls, microphone/camera use, clipboard synchronization and phone permissions need explicit physical/session verification.
- Test Miracast with a compatible phone/receiver before claiming projection; Google Cast and Miracast are separate protocols.
- Carrier hotspot entitlement and actual peer behavior are deployment-specific. A missed or denied query remains `UNKNOWN`, not `UNAVAILABLE`; documented ecosystem functionality does not require a test against the owner's phone.

[PL]: https://support.microsoft.com/en-us/windows/apps/phonelink/phone-link-requirements-and-setup
[NOTIFY]: https://support.microsoft.com/en-au/windows/apps/view-and-manage-mobile-notifications-on-your-pc
[SENSITIVE]: https://support.microsoft.com/en-us/windows/apps/phonelink/troubleshooting-notifications-in-the-phone-link
[SMS]: https://support.microsoft.com/en-us/windows/apps/phonelink/send-and-receive-text-messages-from-your-pc
[DEVICES]: https://support.microsoft.com/en-us/windows/apps/phonelink/supported-devices-for-phone-link-experiences
[CALLS]: https://support.microsoft.com/en-us/windows/apps/make-and-receive-phone-calls-from-your-pc
[PHOTOS]: https://support.microsoft.com/en-us/windows/apps/photos/view-and-manage-photos-from-your-android-device-on-your-pc
[TRANSFER]: https://support.microsoft.com/en-us/windows/apps/phonelink/seamlessly-transfer-content-between-your-devices
[SCREEN]: https://support.microsoft.com/en-US/Windows/Apps/PhoneLink/setting-up-and-using-phone-screen-in-the-phone-link
[APPSSETUP]: https://support.microsoft.com/en-gb/windows/apps/phonelink/setting-up-apps-in-the-phone-link
[APPS]: https://support.microsoft.com/en-us/windows/apps/mobileapps/use-apps-from-your-android-device-on-your-pc
[AUDCTRL]: https://support.microsoft.com/en-us/windows/apps/phonelink/setting-up-notifications-in-the-phone-link
[CAMERA]: https://support.microsoft.com/en-us/windows/apps/phonelink/use-your-mobile-device-s-camera
[EXPLORER]: https://support.microsoft.com/en-us/windows/experience/fileexplorer/setting-up-and-using-your-phone-in-file-explorer
[HOTSPOT]: https://support.microsoft.com/en-us/windows/experience/connectivity-networking/instant-hotspot
[START]: https://support.microsoft.com/en-gb/windows/apps/phonelink/mobile-device-in-start-menu
[RESUME]: https://support.microsoft.com/en-us/windows/apps/phonelink/cross-device-resume-feature
[RESUME2026]: https://support.microsoft.com/en-us/servicing/os/windows-11/2026/01/january-29-2026-kb5074105-os-builds-26200-7705-and-26100-7705-preview
[NEARBY]: https://support.microsoft.com/en-us/windows/experience/connectivity-networking/share-things-with-nearby-devices-in-windows
[QUICK]: https://support.google.com/android/answer/13801258?hl=en
[BTFILE]: https://support.microsoft.com/en-us/windows/hardware/bluetooth/send-and-receive-files-over-bluetooth-in-windows
[USB]: https://support.google.com/android/answer/9064445/transfer-files-between-computer-and-Android-device
[WPD]: https://learn.microsoft.com/en-us/windows-hardware/drivers/portable/wpd-drivers-overview
[ONEDRIVE]: https://support.microsoft.com/en-us/onedrive/use-onedrive-on-android-and-ios-devices
[ONEDRIVECAM]: https://support.microsoft.com/en-us/onedrive/automatically-save-photos-videos-with-onedrive
[GALLERY]: https://support.microsoft.com/en-us/onedrive/changes-to-samsung-gallery-sync-and-onedrive
[TETHER]: https://support.google.com/android/answer/9059108?hl=en
[BTPAN]: https://support.microsoft.com/en-us/windows/hardware/bluetooth/connect-to-a-bluetooth-network-in-windows
[DIRECT]: https://developer.android.com/develop/connectivity/wifi/wifi-direct
[CAST]: https://support.microsoft.com/en-us/windows/hardware/display-graphics/screen-mirroring-and-projecting-to-your-pc-or-wireless-display
[GOOGLECAST]: https://support.google.com/chromecast/answer/3006709
[UVC]: https://support.google.com/pixelcamera/answer/14274129?hl=en
[GLIDEX]: https://www.asus.com/support/faq/1050468/
[GLIDEXWEB]: https://www.asus.com/content/glidex/
[GLIDEXAPPS]: https://www.asus.com/us/support/faq/1051122/
[DEX]: https://www.samsung.com/sg/support/apps-services/changes-to-the-way-you-connect-samsung-galaxy-mobile-devices-to-pcs/
[ADB]: https://developer.android.com/tools/adb
[ADB2]: https://developer.android.com/blog/posts/introducing-fast-and-reliable-wireless-debugging-with-android-debug-bridge-adb-wi-fi-2-0
[EDGE]: https://support.microsoft.com/en-us/edge/sign-in-to-sync-microsoft-edge-across-devices
[SWIFTKEY]: https://support.microsoft.com/en-us/swiftkey-keyboard/how-to-use-microsoft-swiftkey-keyboard-to-copy-and-paste-text-between-swiftkey-and-windows
[MESSAGESWEB]: https://support.google.com/messages/answer/7611075?hl=en-ca
[WSA]: https://learn.microsoft.com/en-us/previous-versions/windows/android/wsa/
