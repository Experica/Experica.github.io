---
title: Setup
permalink: /doc/setup
---

## Setup Hardware 
**Experica** system could run on most machines. However, a custom-built machine would provide more flexibility.

- CPU: 4 cores
- RAM: 16GB
- Network: Gb Ethernet
- GPU: 6GB, DirectX 12/Vulkan
- Display: 1080p, 120Hz, Adaptive-Sync

General Purpose Digital IO can be obtained through Parallel Port(PCIe adaptor card), USB-GPIO([USB bridging chip](https://www.adafruit.com/product/2264)) and DAQ device([multi-function digital and analog IO](https://www.mccdaq.com/)).

## Setup Software 
- Setup UEFI.
- Install Operating System(Linux/Windows/Mac). Currently only Windows 7/10 are tested.
- Get Git or simply use [GitHub Desktop](https://desktop.github.com/).
- Install Unity and IDE. [UnityHub](https://unity3d.com/get-unity/download) can install both of them.

## Setup Experica
- Update Drivers and OS 
- Clone [Command](https://github.com/Experica/Command)/[Environment](https://github.com/Experica/Environment)/[Analysis](https://github.com/Experica/Analysis) from Github repositories, or download binaries from Github Releases.
- Install Drivers or Plugins in folder /Command/Install/ as needed.
- Open Command/Environment/Analysis in Unity editor to do test runs. Do build in Unity editor whenever you find appropriate.
