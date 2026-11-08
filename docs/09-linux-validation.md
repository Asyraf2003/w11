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

## Next useful work

1. Reuse the lab for further controlled software checks only where the result answers a migration decision: audio processing, useful CPU inference or Android protocol tooling. Record the fixture and result instead of treating installation as success.
2. Use a later authorized native Linux boot from separate media for **ASUS platform controls, real codec/amplifier routing/protection, OLED/display behavior, NPU driver/workload, radio/dock and suspend**. Existing Windows stays available as the comparison reference.
3. Start physical audio checks from the captured Realtek/Cirrus identity, OEM routing and protection requirements. A software gain/EQ pass is insufficient to choose safe speaker gain or replace amplifier calibration.

Audio processing uses generated signals and file/null output. It will not play through the laptop speakers, use private media or copy proprietary Dolby tuning. Passing EQ/limiting checks can establish generic DSP building blocks; it cannot establish licensed Dolby Atmos reproduction, smart-amplifier protection or safe physical speaker gain. [FFmpeg filter contracts](https://ffmpeg.org/ffmpeg-filters.html).

Results will be updated in this document after each completed check, with command/tool version, fixture and outcome. Native hardware checks remain untested until the appropriate environment is actually used. No existing Frankenstein implementation or reference repository is modified.
