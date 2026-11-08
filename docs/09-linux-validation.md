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

Initial discovery: WSL **3.0.3.0**, WSLg **1.0.79**, an existing running Ubuntu 24.04 WSL2 distribution, and the official `archlinux` entry in the WSL online catalog. A named fresh Arch lab installation was started; completed isolation and audio test results are **PENDING**, not counted as passes. [Arch's official image distribution](https://archlinux.org/download/), [WSL install controls](https://learn.microsoft.com/en-us/windows/wsl/basic-commands).

Audio processing uses generated signals and file/null output. It will not play through the laptop speakers, use private media or copy proprietary Dolby tuning. Passing EQ/limiting checks can establish generic DSP building blocks; it cannot establish licensed Dolby Atmos reproduction, smart-amplifier protection or safe physical speaker gain. [FFmpeg filter contracts](https://ffmpeg.org/ffmpeg-filters.html).

Results will be updated in this document after each completed check, with command/tool version, fixture and outcome. Native hardware checks remain untested until the appropriate environment is actually used. No existing Frankenstein implementation or reference repository is modified.
