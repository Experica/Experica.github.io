---
title: Setup
---

## Setup Hardware 
Most of computers in the market should be enough to run VLAB system, but some flexibility is always preferred in a lab environment, we recommend building a custom PC, otherwise make sure your machine has enough space or slots for whatever adaptors needed.

Recommended:
- CPU: Intel i7
- Memory: 16GB
- Graphics: DirectX 12/Vulkan, Adaptive-Sync
- Display: 1080p, 240Hz, Adaptive-Sync

For fast trigger or communicating to external hardware, Parallel Port/Serial Port/GPIO are preferred. Most computers no longer has building parallel port, so installation of parallel port adaptor though PCIe is needed; serial port may be emulated through USB.

In order to get precise timing of display refresh, photodiode measuring is needed, but it's more continent to convert photodiode analog signal to TTL digital signal. Make your own or checkout this [Photodiode Logic Board](https://github.com/VLABSys/LPC43xx_M4_AnalogToDigital).

## Setup Software 

- Setup appropriate UEFI parameter.
- Install Operating System, Linux/Windows/Mac should all be able to run VLAB, but currently only Windows 7/10 are tested.
- Get Git running or just simply use [GitHub Desktop](https://desktop.github.com/).
- Install Unity and code editor. [UnityHub](https://unity3d.com/get-unity/download) can install both of them.

## Setup VLAB
- Update Drivers and OS 
- Clone [VLab](https://github.com/VLABSys/VLab)/[VLabEnvironment](https://github.com/VLABSys/VLabEnvironment)/[VLabAnalysis](https://github.com/VLABSys/VLabAnalysis) from VLAB Github repositories.
- Since we do not provide executable binary, you should open  VLab/VLabEnvironment/VLabAnalysis in Unity editor and do test run. Do build in Unity editor whenever you find appropriate.
- Setup display for VLabEnvironment 
  - Most displays have some smart adjustment for brightness or other parameters. Make sure the display mode and parameters is what you want. 
  - In your PC, Set graphics card parameters such as Resolution, Refresh Rate, Adaptive-Sync, etc.
  - Use photometer to Test and calibrate luminance and color, and make adjustment to Gamma value, so that color values is presented linearly on the display. 
- Test Parallel Port/Serial Port/GPIO, photodiode logic board or whatever hardware you are using 
