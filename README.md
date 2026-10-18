<div align="center">

<a href="https://dawndrums.tn"><img title="dawndrums" alt="dawndrums" src="assets/dd_logo_v2.png" width="70%" /></a>
<p>As the drums of awakening echo through the dawn, let technology be the rhythm that enhances our freedom, guiding us towards a brighter tomorrow</p>


[![License: GPL-3.0](https://img.shields.io/badge/License-GPL%203.0-blue.svg)](#license)
[![Discord](https://img.shields.io/badge/Discord-%235865F2.svg?logo=discord&logoColor=white)](https://discord.gg/HVb5jNBTRH)
[![Matrix](https://img.shields.io/badge/Matrix-000?logo=matrix&logoColor=fff)](https://matrix.to/#/#dawndrums-r2:matrix.org)
[![Mastodon](https://img.shields.io/badge/Mastodon-000?logo=mastodon&logoColor=fff)](https://mastodon.social/@dawndrums)

[Website](https://dawndrums.tn) · [Documentation](https://docs.dawndrums.tn/docs/Current_state) · [DawnOS](https://github.com/dawndrums/dawnos/)

</div>

## Divine D.

**A Mobile Linux System.**

![Divine D.](https://github.com/dawndrums/divine/raw/refs/heads/main/d._/assets/rev1.1/dd.rev1.1.jpg)
Our first assembled Divine D. with mainPCB Rev. 1.1 video is now public: booting, navigating the interface, and browsing on the device.

[![Watch Divine D. running native Linux](https://img.youtube.com/vi/G_B7cwbMqq8/hqdefault.jpg)](https://youtu.be/G_B7cwbMqq8)

**[Watch the demo on YouTube →](https://youtu.be/G_B7cwbMqq8)**

Divine D. is a working minimum viable product (MVP). The demo marks a milestone in bringing the hardware and software together; reliability, power management, and production readiness remain active development priorities.

## Overview

Divine D. is an open-source, close-to-mainline mobile Linux system running Linux kernel **7.1.0**, built around the Rockchip RK3588S. It combines a custom mainboard, a touchscreen, cellular connectivity, and accessible hardware interfaces in a portable enclosure.

We design the MainPCB and assemble the devices in-house. Our goal is to make a mobile system that people can use, understand, modify, and develop for, from Linux applications and desktop interfaces to drivers and hardware accessories.

[DawnOS](https://github.com/dawndrums/dawnos/) is our ongoing software integration effort, based on Mobian/Debian. Divine D. runs native Linux with access to the Debian software ecosystem. Development includes Plasma Mobile and Phosh, alongside device-specific kernel, driver, and userspace work.

The platform also provides room to explore on-device AI, camera processing, multimedia, and hardware expansion. Support depends on the relevant drivers and applications, hardware capability alone does not imply a finished software feature.

## Contents

- [Current status](#current-status)
- [Hardware](#hardware)
- [Software](#software)
- [Development priorities](#development-priorities)
- [Contributing](#contributing)
- [Community and contact](#community-and-contact)
- [Support](#support)
- [License](#license)

## Current status

**Development snapshot: October 2026 — MVP · Linux 7.1.0 · MainPCB Rev. 1.1, Hannibal Batch.**

The system boots into a mobile Linux desktop, supports navigation and web browsing, and has working Wi-Fi and cellular telephony. GPU acceleration is working, and camera capture and autofocus are under active development.

| Area | Status and remaining work |
| --- | --- |
| Boot and desktop | Working; continued integration and stability testing |
| Wi-Fi and cellular | Working connectivity and telephony; regression testing remains important |
| Graphics | Working GPU acceleration; ongoing performance and power tuning |
| Camera | Capture and autofocus development in progress; tuning, responsiveness, and still-image workflow need further work |
| Battery and power | Ongoing work on battery reporting, usable runtime, charging, and suspend/resume reliability |
| Updates and recovery | A repeatable update and restore process is a development priority |
| Hardware and enclosure | Rev. 1.1 is the current development platform; further revisions and mechanical refinements are being evaluated |

This is not yet a production release. Features are being tested as a complete system, and software support varies by component and kernel branch.

See the [project documentation](https://docs.dawndrums.tn/docs/Current_state) for detailed status and development notes.

## Hardware

### MainPCB — Rev. 1.1, Hannibal Batch

<img alt="Divine D. MainPCB Rev. 1.1" src="https://github.com/dawndrums/divine/blob/main/d._/assets/rev1.1/MainPCB_Rev1.1.png" width="800" />

The following describes the board design and configuration options. It is not a claim that every interface is fully enabled or validated in the current software image.

| Component | Design / configuration |
| --- | --- |
| Mainboard | Custom 10-layer HDI PCB |
| Processor | Rockchip RK3588S; 4× Cortex-A76 and 4× Cortex-A55 |
| Memory | LPDDR4X; current development unit: 8 GB; design options include 16 GB and 32 GB |
| Storage | eMMC; current development unit: 32 GB; design options include 64 GB, 128 GB and 256 GB |
| Graphics | Arm Mali-G610 GPU |
| Compute and multimedia | Integrated NPU and video processing hardware; support depends on the software stack |
| Wireless | AP6275P Wi-Fi / Bluetooth module; M.2 3042 interface for cellular modem; LoRa |
| Storage expansion | microSD Express interface with legacy microSD compatibility in the design |
| Display and ports | MIPI display interfaces, USB-C, Micro HDMI, and 3.5 mm audio jack |
| Audio | ES8388 codec, CS43131 DAC, dual amplifiers, dual microphone and earpiece interfaces |
| Sensors and feedback | Six-axis IMU, proximity and ambient-light sensing, haptic driver, LED indicators and IR LED |
| Power | Battery charger, USB-C PD controller, fuel gauge, under-voltage monitor, and power/battery switches |
| Hardware controls | Kill-switches for cameras, microphones, and connectivity |
| Expansion | 18-pin pogo interface for accessories and development |
| Debug | USB Maskrom, UART, and JTAG/SWD interfaces |

Charging rates, display-output modes, expansion interfaces, and multimedia capabilities require validation in the complete device. Final supported configurations will be documented as testing progresses.

### Display, cameras, and enclosure

- **Display:** 5.5-inch AMOLED, 1080 × 1920 pixels.
- **Rear camera:** Sony IMX586, 48 MP sensor; usable capture modes depend on the driver and camera pipeline.
- **Front camera:** Sony IMX378, 12 MP sensor in the hardware design; software support is tracked separately.
- **Controls:** Power and volume buttons.
- **Audio:** Stereo speakers and a 3.5 mm jack.
- **Enclosure:** 3D-printable design under continued mechanical refinement.
- **Battery, final dimensions, and weight:** To be finalized for the release configuration.

## Software

### DawnOS

DawnOS brings together the distribution, device support, and mobile user experience for Divine D. It is based on Mobian/Debian and remains a work in progress.

- Native Linux applications and Debian packages.
- Wayland-based mobile interfaces, including Plasma Mobile and Phosh.
- Device-specific kernel configuration, device trees, and driver integration.
- Ongoing camera, audio, telephony, and power-management work.

### Kernel and drivers

Divine D. runs Linux kernel **7.1.0** on a **close-to-mainline** kernel base. Development has progressed beyond the original vendor-kernel bring-up, while retaining device-specific patches needed to support the hardware. Hardware enablement includes graphics, sensors, power management, and the camera stack; the close-to-mainline designation does not mean that all device support has been merged upstream.

Exact kernel versions, patch sets, and component support should be checked against the relevant source branch and [development documentation](https://docs.dawndrums.tn/docs/Current_state).

Divine D. builds on the work of the Linux, Debian, Mobian, KDE, Phosh, Mesa, libcamera, U-Boot, and wider open-source communities. Thank you to everyone contributing upstream and helping bring open mobile hardware to life.

## Development priorities

Our next milestone is a more reliable and reproducible system that contributors can test and develop against.

1. **Power and battery:** Improve battery reporting, discharge behavior, charging, runtime, and suspend/resume reliability.
2. **Updates and recovery:** Establish a tested installation, update, and restore workflow.
3. **Core functionality:** Reduce regressions in telephony, networking, audio, and everyday interaction.
4. **Camera:** Improve capture reliability, autofocus, image tuning, and the still-image workflow.
5. **Hardware readiness:** Validate revisions, refine the enclosure, and document assembly and testing.
6. **Community development:** Publish reproducible instructions and use testing feedback to guide priorities.

## Contributing

Contributions are welcome across kernel and driver work, mobile applications, testing, documentation, hardware, and enclosure design.

- Report bugs through **GitHub issues**, including the hardware revision, software image or commit, reproduction steps, and relevant logs.
- Discuss substantial changes before starting implementation so we can coordinate work.
- Submit focused pull requests with a clear explanation of the change and how it was tested.
- Share which use cases and improvements matter most to you through our community channels.

## Community and contact

- [Discord](https://discord.gg/HVb5jNBTRH)
- [Matrix](https://matrix.to/#/#dawndrums-r2:matrix.org)
- [Mastodon](https://mastodon.social/@dawndrums)
- [Website](https://dawndrums.tn)
- Email: [contact@dawndrums.tn](mailto:contact@dawndrums.tn)

## Support

Donations help fund prototype manufacturing, hardware and software development, testing, and infrastructure.

[![Donate via Liberapay](https://liberapay.com/assets/widgets/donate.svg)](https://liberapay.com/dawndrums/donate)

For other ways to support the project, contact [contact@dawndrums.tn](mailto:contact@dawndrums.tn).

## License

This project is licensed under GPL-3.0. See the license text and any file-specific notices in the repository for the applicable terms.
