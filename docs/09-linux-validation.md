# Linux validation: what WSL can prove

Phase 3 started **2026-11-08** at the user's request. Windows collection remains the reference; this phase checks useful Linux behavior without replacing the Windows installation. Paint/Photos AI depth and exhaustive physical keyboard checks remain outside the current scope. Android coverage remains about ecosystem capability, not the owner's phone.

## Use the cheapest environment that can establish the result

| Capability class | Useful first environment | Evidence it can establish | Still needs native Linux |
|---|---|---|---|
| CLI tools, file handling, synthetic audio DSP, CPU inference | Separate Linux filesystem in WSL/container | A real Linux program processes a controlled fixture with a checked result | Native-device integration, actual latency/power and physical quality |
| GUI app behavior, supported graphics APIs | WSLg or a VM | App launch and supported virtualized rendering | Native compositor, display modes, HDR/color/OLED behavior and input integration |
| Android protocols and file-transfer software | WSL/container for software tests; suitable isolated peers for transport tests | Protocol/software operation under explicitly tested network conditions | Real Wi-Fi/Bluetooth modes, Miracast and radio/peer interoperability |
| ASUS battery/fan/ALS/OLED/platform controls | Native Linux boot on separate media | Kernel/firmware interface exposure and real hardware behavior | WSL/ordinary VM results cannot replace these checks |
| Speaker codec/amplifier, hardware protection and microphone array | Native Linux with exact device/driver/tuning evidence | Real routing, gain, protection, sound and microphone behavior | Windows-hosted virtual audio cannot establish the Linux Realtek/Cirrus path |
| AMD NPU / GPU workload | Exact supported Linux device/runtime path; native boot when that path is unavailable in WSL | Only an actual accelerated workload establishes use | An installed runtime or virtual GPU is not proof of native NPU support |
| Suspend/resume, USB4/docks, power draw | Native Linux and relevant physical peer | Successful controlled cycle and measured behavior | These depend on the real firmware/kernel/device path |

WSL 2 runs a Linux kernel in a managed VM. WSLg supplies integrated GUI/audio/graphics paths through the Windows host; USB forwarding requires additional supported plumbing. Therefore a successful WSL app is valid software evidence, not a native hardware-parity certificate. [WSL architecture](https://learn.microsoft.com/en-us/windows/wsl/compare-versions), [WSLg](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps), [USB forwarding](https://learn.microsoft.com/en-us/windows/wsl/connect-usb).

There is no requirement to replace Windows before native validation: a later authorized Linux boot from separate USB/SSD storage can use the physical hardware while preserving the existing installation. No disk formatting, partition, boot-order, firmware or Windows driver change is part of the current lab setup.

## First batch and progress denominator

This batch has **three checks**, rather than a percentage of every Windows capability:

1. A separate disposable Linux test filesystem, with the existing work environment preserved.
2. A synthetic tone processed by a real Linux equalizer, checking the expected gain.
3. A synthetic limiter test, checking that the output peak stays at the selected threshold.

Initial discovery: WSL **3.0.3.0**, WSLg **1.0.79**, an existing running Ubuntu 24.04 WSL2 distribution, and the official `archlinux` entry in the WSL online catalog. [Arch's official image distribution](https://archlinux.org/download/), [WSL install controls](https://learn.microsoft.com/en-us/windows/wsl/basic-commands).

**Progress: 3/3 checks completed for the first batch.** This is not a percentage of total Windows/Linux parity.

| Check | Actual result, 2026-11-08 | What passed |
|---|---|---|
| Separate test filesystem | Fresh **W11-Lab-Arch** WSL2 distribution on its own virtual disk; Arch shell and package manager ran; existing Ubuntu remains default | Independent lab startup and filesystem, not security isolation from Windows |
| Synthetic equalizer | Requested **+6 dB** at 1 kHz; measured RMS change **+5.9984 dB** | PASS against ±0.15 dB tolerance; real FFmpeg Linux filter execution |
| Synthetic limiter | Requested maximum amplitude **0.5**; measured peak **−6.0206 dBFS** | PASS against −6.20…−6.00 dBFS tolerance; no physical audio output |

Environment: Arch rolling userspace, kernel **6.18.54.1-microsoft-standard-WSL2**, Arch package **ffmpeg 2:9.0.2-2**. The fresh image's package keyring was initialized using Arch's bundled trust data before installing signed repository packages. Changes are confined to the new lab; no production source was deployed.

Fixture: FFmpeg-generated **1 kHz, 48 kHz sample rate, 2 seconds**. The baseline uses `astats`; the EQ path uses `equalizer=f=1000:t=q:w=1:g=6,astats=metadata=0:reset=0`; the limiter path uses `volume=16,alimiter=limit=0.5:level=false,astats=metadata=0:reset=0`. Every invocation takes the generated source and writes to the **null muxer**. No speaker, microphone or personal file is opened.

Raw baseline/EQ/limiter logs, tool version, the assert-based check and SHA-256 provenance are preserved locally outside this public repository. The test establishes these two generic software DSP operations under WSL. It does not establish a ten-band GUI, an active desktop audio chain, speaker calibration, Cirrus protection, licensed Atmos, NPU acceleration or perceptual equivalence.

## Second batch: usable audio software and reconstruction bytes

**Progress: 4/4 checks completed in this batch**, on the same Arch WSL lab. These are software checks, not four native hardware passes.

| Check | Controlled fixture / acceptance | Actual result | Evidence status |
|---|---|---|---|
| Ten-band EQ chain | Centers **32, 64, 125, 250, 500 Hz, 1, 2, 4, 8, 16 kHz**; one band +6 dB, other nine at zero; separate matching 2-second tones; measure after the first 250 ms; ±0.15 dB | **10/10 centers PASS**, measured **+5.988761…+5.998530 dB** | OBSERVED software processing, CAPTURED; no ten-band desktop GUI tested |
| Loudness normalization | Generated 10-second 1 kHz tone; `loudnorm=I=-23:TP=-2:LRA=7:print_format=json`; target ±0.2 LU | Filter reports **−23.04 LUFS**, true peak **−19.97 dBTP**: PASS | OBSERVED reported output, CAPTURED; not an independent loudness-meter comparison or Dolby's real-time volume leveler |
| Stereo routing | Generated L=440 Hz / R=880 Hz with different amplitudes; swap channels; compare every float sample against the opposite original channel | Maximum absolute sample error **0**, finite output: PASS | OBSERVED software routing, CAPTURED; no physical speaker assignment or Atmos rendering claim |
| Existing speaker-tuning reconstruction | Existing reference revision **20543c6**; run its 12 focused tests against a Linux extraction, with deployment targets confined to temporary directories | **12/12 PASS** after LF-preserving export; tuning hashes, routing guards and temporary apply/verify/rollback checks passed | OBSERVED test behavior, CAPTURED; source repository and actual desktop audio unchanged |

The reconstruction check caught a real copy problem: the Windows checkout and a default Windows Git archive both produced **10 passing tests, one failure and one error**. `core.autocrlf=true` converted the graph and license from LF to CRLF, breaking their declared hashes. A byte comparison confirmed that CRLF conversion explains the differences; the binary impulse-response file was unchanged. Do not replace expected hashes to accept the altered copy.

The successful export used command-scoped settings, leaving the existing Git configuration and reference checkout untouched:

```sh
git -c core.autocrlf=false -c core.eol=lf archive --format=tar \
  --output=audio-source.tar 20543c6bdb54e4eb90fcb4a03402d56188c9f7e3 \
  desired/host/zenbook/bin/audio desired/host/zenbook/audio tests/test-audio-oem.py
# Extract inside the Linux lab, then run: python -B tests/test-audio-oem.py -v
```

Git's attributes/configuration control line-ending conversion; the observed archive behavior above belongs to the tested Windows Git environment. Verify resulting bytes on the destination rather than assuming an archive or a successful copy preserves declared hashes. [Git line-ending rules](https://git-scm.com/docs/gitattributes), [Git archive](https://git-scm.com/docs/git-archive).

Generated-input commands, logs, results, original failing copies and successful LF export are preserved privately with SHA-256 manifests. The user-designated removable drive now contains a separate lab folder; its existing files and partitions were preserved. It is **storage for evidence and transfer artifacts**, not an already boot-tested Linux medium. No raw OEM tuning, impulse response or private reference source is published here.

## Private Windows evidence: copied and read successfully from Linux

The user-designated removable drive holds a separate private preservation folder. **64/64 files** matched the SHA-256 digest and byte length calculated from their original Windows sources. Linux Python **3.14.9** also parsed **39 JSON files** with UTF-8/BOM handling and checked the signatures of **18 PNG screenshots**. Remaining files include collection/provenance material. The JSON records, scripts and original screenshot pixels remain private.

This establishes byte preservation and basic structured-data readability across the Windows → removable storage → Linux path. It does not verify every fact inside a capture, render every screenshot, restore a driver, or establish feature behavior. A SHA-256 source manifest, Linux verification result and verification-script hashes accompany the private copy; originals were not converted, moved or overwritten.

## Native verification queue and boot constraints

The selected removable medium is approximately **128 GB class**, **MBR**, with **one exFAT partition** and existing files. Only a new lab folder has been used. An ISO stored in that folder is a transfer artifact; its presence is not proof that the medium boots.

Windows currently reports **Secure Boot enabled**. The official Arch installation ISO does **not** support Secure Boot as supplied, so it is not a ready native-boot path under the unchanged captured policy. No Secure Boot, firmware, TPM, boot-order or partition changes are authorized by merely preparing these files. A separately reviewed boot method is needed. A distribution with an appropriately signed boot chain, such as Ubuntu, can be considered for initial hardware discovery, but its result belongs to that distribution/kernel rather than proving Arch support. [Arch installation-image boundary](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Booting_an_installation_medium), [Ubuntu signed boot chain](https://documentation.ubuntu.com/security/security-features/platform-protections/secure-boot/).

| Native batch | First evidence needed | Completion requires more than enumeration |
|---|---|---|
| ASUS battery and thermal policy | Bound platform driver, exposed threshold/profile choices and before/after charging-limit state | Correct threshold behavior and chosen profile; account for the driver initialization described in [ASUS controls](04-asus-myasus.md#linux-portability-platform-controls-need-firmware-evidence) |
| Realtek/Cirrus audio | Codec/subsystem match, both amplifier components, firmware load and protection/calibration evidence | Controlled routing, quiet playback/recording and later quality comparison; synthetic DSP is not amplifier protection. [Audio driver match](05-dolby-audio.md#linux-driver-match-and-reusable-software-evidence) |
| Radeon, panel and OLED | Native graphics driver, connector/mode and actual color/backlight/compositor controls | Display modes and chosen visual behavior; software pixel shifting is not panel compensation |
| RGB/IR camera and microphone | Exact V4L2/ALSA endpoints and required permissions | A deliberately nonpersonal app workload and effect/capture quality; no biometric enrollment |
| NPU | Exact PCI identity, bound amdxdna driver, firmware/runtime readiness | A supported model completes with recorded accelerator use. [AI runtime boundaries](03-copilot-ai.md#linux-validation-boundary-for-cpu-gpu-and-npu) |
| Wi-Fi, Bluetooth and USB4/docks | Bound drivers, advertised roles and suitable peer/peripheral | Actual connection, data/display/audio path and reconnect behavior; no private peer content needed. [USB4 driver contract](https://www.kernel.org/doc/html/latest/admin-guide/thunderbolt.html) |
| Suspend and power | Exposed `/sys/power/state` and `/sys/power/mem_sleep`, relevant driver errors | Controlled suspend/resume and measured battery behavior; an advertised state is insufficient. [Kernel sleep states](https://docs.kernel.org/admin-guide/pm/sleep-states.html) |
| Android ecosystem | Selected tool/peer versions and granted test permissions | Deliberate nonpersonal transfers/mirroring rather than package presence. [Documented Linux routes](06-android-integration.md#linux-continuation-ecosystem-functions-separate-implementations) |

Initial native discovery can stay read-only at the command level:

```sh
uname -r
lspci -nnk
cat /proc/asound/cards
ls -ld /dev/accel /dev/dri /dev/snd
cat /sys/power/state /sys/power/mem_sleep
journalctl -b -k --grep='cs35l|snd_hda|amdxdna|asus|amdgpu'
```

Keep raw output private and retain missing-file, permission and driver errors. These commands do not write settings, but booting a real kernel can initialize hardware and firmware-managed state. No native Linux boot or physical hardware acceptance has occurred in this phase.

## Next useful work

1. Reuse existing reference implementations and proofs before adding another test. Further lab checks should answer a migration decision: actual audio-provider compatibility, useful CPU inference or Android protocol tooling. Record the fixture and result instead of treating installation as success.
2. Use a later authorized native Linux boot from separate media for **ASUS platform controls, real codec/amplifier routing/protection, OLED/display behavior, NPU driver/workload, radio/dock and suspend**. Existing Windows stays available as the comparison reference.
3. Start physical audio checks from the captured Realtek/Cirrus identity, OEM routing and protection requirements. A software gain/EQ pass is insufficient to choose safe speaker gain or replace amplifier calibration.

Audio processing uses generated signals and file/null output. It will not play through the laptop speakers, use private media or copy proprietary Dolby tuning. Passing EQ/limiting checks can establish generic DSP building blocks; it cannot establish licensed Dolby Atmos reproduction, smart-amplifier protection or safe physical speaker gain. [FFmpeg filter contracts](https://ffmpeg.org/ffmpeg-filters.html).

Results will be updated in this document after each completed check, with command/tool version, fixture and outcome. Native hardware checks remain untested until the appropriate environment is actually used. No existing Frankenstein implementation or reference repository is modified.
