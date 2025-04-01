<div align="center">
<a href="https://dawndrums.tn"><img title="dawndrums" src="assets/dd_logo_v2.png" width="70%"/></a>

<span style="color: #e1ba66;">As the drums of awakening echo through the dawn, let technology be the rhythm that enhances our freedom, guiding us towards a brighter tomorrow</span>


[![License](https://img.shields.io/badge/License-GPL%203.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![discord](https://img.shields.io/badge/Discord-%235865F2.svg?&logo=discord&logoColor=white)](https://discord.gg/dEeTTjjB)
[![Reddit](https://img.shields.io/badge/Reddit-FF4500?logo=reddit&logoColor=white)](https://reddit.com/r/dawndrums)
[![Matrix.org](https://img.shields.io/badge/Matrix-000?logo=matrix&logoColor=fff)](https://matrix.to/#/#dawndrums.tn:matrix.org)


<p float="center">
<img src="https://github.com/dawndrums/divine/blob/main/d._/assets/dd.rev1.jpg" width="50%" object-fit="cover"/>
</p>
<sub>
  Divine D.
</sub>
</div>

## Table of content

- [Divine](#divine)
  - [Table of content](#table-of-content)
  - [Overview](#overview)
  - [Features](#features)
    - [Hardware](#hardware)
      - [PCB](#pcb)
      - [Body](#body)
    - [Software](#software)
      - [DawnOS](#dawnos)
      - [Desktop UIs](#ui)
      - [Kernel and Drivers](#kernel)
  - [Current state](#current-state)
  - [Licence GPL-3.0](#licence-gpl-30)

## Overview

Divine is an open-source mobile system running a native Linux distribution [DawnOS](https://www.github/dawndrums/dawnos/).
Divine is powered with the SoC RK3588S, an octa-core and highly capable SoC with Armv8 architecture and 3nm process. The D. variant known as "Divine D." focuses on delivering 
a system that's also for developing purposes and tests, much like a development kit, except that it comes as a fully functional mobile system. Yes, it runs "Doom" and makes calls.
For the first time, an open-source mobile system brings local AI to its set of applications.
With the integrated 3-core NPU and up to 16 GB of RAM (32 GB MAX) Divine D. is able to run LLMs and smaller models Offline and Local, pushing private and portable AI to unprecedented level.
The RK3588S features a set of high performance subsystems, most notably the Mali GPU and the VPU up to 8k of video playback. 
Divine D. comes currently with dual-cameras, front (12 MP, imx-378) and rear (48MP imx-586) Sony® sensors to provide excellent image quality for low-light and color accuracy.
We bring also the world-class DAC, Cirrus CS43131, a tiny and mighty audio processor for excellent high fidelity Music playback on the 3.5 mm jack.
An additional audio codec takes care of routing audio to a set of stereo speakers, dual-microphone and an earpiece.
Divine D. supports currently fast charging up to 27 W (9V 3A) with Power-delivery protocol over USB-C, which supports display-port for external display as well as USB3/USB2 data transfer.
An AMOLED, 5.5" 1080P screen is accommodated for lively colors and deep blacks. 

Being a portable device, the power consumption is always a concern and we're committed to optimize and balance out power consumption and performance.
We intend to use a minimum of 4800 mAh battery, depending on the final body size.
The RK3588S can a already dynamically perform in an on-demand scheme with respect to the load and ultimately can enter suspend to demand less than 80 mA @ 4.2V.
The system can effectively enter suspend while being able to accept calls and sms (duty-cycled RF). We work also here to make this as stable as possible.

While the hardware features provide interesting capabilities, the software needs to be on point to take advantage of all that. This is also part of our commitment for DawnOS.
We currently have a system that enters desktop UI, connects to WIFI/4G, makes calls and comes with working drivers such a 3D and video acceleration.
Together with the community, we continuously work to improve the overall stability and robustness.
Please refer the [Current state](#current-state) for more details.

We chose mobian as our base for its initial stability with support for Phosh and Plasma Mobile UIs. It provides access to a plethora of applications in the Debian repositories.
This work is coming to life thanks to us at danwdrums :) and the commitment of the open-source community and vendors who promote technological freedom.
At the time of writing, this is the World's most powerful and free open-source mobile system.
More on this, stay tuned.

PS: If you want to support and contribute, you know what to do. You can always contact us by writing to contact@dawndrums.tn.

## Features (Divine D.)

### Hardware

#### MainPCB, Hannibal batch Rev. 1.0
<kbd><img title="HW" src="https://github.com/dawndrums/divine/blob/main/d._/assets/divine_mb_1.0.jpg"/></kbd>
<sub>
MainPCB Hannibal batch
</sub>
- A 10-layer HDI board
- Processor: RK3588S, 4x Cortex-A76 @ 2.4 GHz, 4x Cortex-A55 core @ 1.8 GHz
- RAM: LPDDR4x, 8 GB, 16 GB
- GPU: Arm Mali-G610 "Odin"
- VPU: Video decoder – 8Kp60 H.265, VP9, AVS2, 8Kp30 H.264 AVC/MVC, 4Kp60 AV1, 1080p60 MPEG-2/-1, VC-1, VP8 Video encoder – 8Kp30 H.265/H.264 video encoder
- 3x NPU Cores, 6 TFLOPS 
- eMMC 64 GB, 128 GB, 256 GB
- microSD
- AP6275P WIFI 6, Bluetooth 5.3
- Ports: USB-C, 3.5 mm Jack
- 5A battery fast charger
- USB-C PD controller
- Fuel-gauge
- Positioning: GNSS, Galileo
- Audio: ES8388, CS43131
- Dual Audio amplifiers
- 6-axis MEMS IMU, Gyroscope and Accelerometer
- Dual Camera interfaces
- Dual MIPI interfaces
- Dual Microphones
- Debug: USB Maskrom, UART and JTAG/SWD
- mini-PCIe Interface for 4G/GSM
- SecondPCB interface
#### SecondPCB Rev. 1.0
- Proximity and light sensor
- RGB LED
- Earpiece interface
- MainPCB interface
- Hardware kill-switches for cameras, microphones, connectivity

#### Body
- Screen: 5.5" AMOLED, 1080x1920 pixels
- Front Camera: 12 MPixels Sony IMX-378 Front Camera
- Rear Camera: 48 MPixels, Sony IMX-586 Rear Camera
- Battery: min  4800 mAh
- Volume Up/Down and Power button
- Stereo speakers
- 3D printable enclosure
- Dimensions: 15 mm
- Weight: TBD


### Software
#### DawnOS (WIP)
- Native Linux® based on mobian/debian, release 02.2025
- Security and Privacy by design
- Phosh and Plasma mobile desktop UIs
- Device Tree configuration
- Custom Kernel based on vendor Kernel 6.1.84 and soon the [upcoming Mainline Kernel](https://gitlab.collabora.com/hardware-enablement/rockchip-3588/notes-for-rockchip-3588/-/blob/main/mainline-status.md)
- U-boot 2017.09
#### Desktop UIs

We have tested several desktop UIs, including KDE, Gnome.. A the moment we will further conduct improvement on DawnOS with Phosh UI.
It works with wayland and we encountered the least issues with it. Phosh also seems to demand less resources compared for example to Plasma Mobile.
The latter will not be excluded from improvements but it seems it needs some more optimizations. Plasma home screen is more flexible and features attractive UI.
Depending on our workload we will occasionality issue fixes but priority will go to Phosh-based DawnOS.

#### Kernel and Drivers

At the time we started with divine development, the vendor kernels such as Armbian and Radxa provided kernels that supported RK3588(S) based boards.
These kernels come with certain driver support and were more suitable to use than mainline kernel.
The current kernel version used for DawnOS is 6.1.x coming with our patches, configuration and device tree to support divine hardware.
Recent changes on the mainline kernel brought several improvements and driver support and is becoming more mature to be adopted for the next iterations of DawnOS.
Please refer to our doc pages for the latest changes.

### Current state

There is always work in progress, whether we issue fixes and improvements or add new features.
For the divine and DawnOS projects, below are the most relevant changes and the actual status.
Please refer to our [docs](https://docs.dawndrums.tn) for in-depth changes.


## Licence GPL-3.0

This work is licenced under GPL-3.0 Licence.
