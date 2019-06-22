---
title: Setup
permalink: /doc/setup
---

## Setup Hardware 
Experica system should be able to run on most of machines. However, we recommend building a custom PC which provides the flexibility for upgrades or addon cards.

Minimum:
- CPU: Intel/AMD 4 cores
- Memory: 16GB
- Network: 1Gb Ethernet
- Graphics: 6GB, DirectX 12/Vulkan, Adaptive-Sync
- Display: 1080p, 120Hz, Adaptive-Sync

Simple fast digital trigger can be done through parallel port, but most computers no longer has buildin parallel port, a PCIe parallel port adaptor can be used instead.

In order to get precise timing of display refresh, photodiode measuring is needed, but it's more conveniant to convert photodiode analog signal to TTL digital signal. Make your own or checkout this [Photodiode Logic Board](https://github.com/Experica/LPC43xx_M4_AnalogToDigital).

## Setup Software 

- Setup appropriate UEFI parameter.
- Install Operating System, Linux/Windows/Mac should all be able to run Experica, but currently only Windows 7/10 are tested.
- Get Git or simply use [GitHub Desktop](https://desktop.github.com/).
- Install Unity and IDE. [UnityHub](https://unity3d.com/get-unity/download) can install both of them.

## Setup Experica
- Update Drivers and OS 
- Clone [Command](https://github.com/Experica/Command)/[Environment](https://github.com/Experica/Environment)/[Analysis](https://github.com/Experica/Analysis) from Experica Github repositories.
- Install Drivers/Plugins in /Command/Install/ as needed.
- Since no executable binary is included in the repositories, you should open Command/Environment/Analysis in Unity editor to do test runs. Do build in Unity editor whenever you find appropriate.
