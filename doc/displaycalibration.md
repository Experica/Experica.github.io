---
title: Display Calibration
permalink: /doc/displaycalibration
---

## Setup Display System
**Display** and **Graphics** system should be carefully setup on machines responsible for visuals.

Display may have adjustable parameters(brightness, contrast, etc.) or smart automatic adjustment(energy saving, etc.), therefore they need checking to make sure the display works as you intended.

- Refresh Rate: To prevent frame tearing, presenting visuals is usually configurated to _VSync_ with the display, so the faster the display refreshes, the higher the maximum frame rate could be achieved.

Graphics should also be set(Resolution, Color Depths, Gamma, etc.) to work with the specifically configurated display.

- Adaptive-Sync: [G-Sync](https://en.wikipedia.org/wiki/Nvidia_G-Sync)/[FreeSync](https://en.wikipedia.org/wiki/FreeSync) makes display adapting its refresh rate to graphics frame rate, reducing latency from graphics frame to display frame.

## Linearize Display Primaries Luminance
By default, **Experica** is using [Unity Linear Rendering](https://docs.unity3d.com/Manual/LinearLighting.html), in which linear quantified lights are simulated, rendered, displayed, and no [gamma related correction](https://en.wikipedia.org/wiki/Gamma_correction) are applied by **Unity**. Mathmatically, color space specification and convertion, or lighting calculations in [Shaders](https://en.wikipedia.org/wiki/Shader) are all in linear space, so any color or texture that are gamma encoded, or displays with gamma response curve should be verified and corrected, that any linear digital color and texture, after any calculation and convertions, will result on display also Linear Physical [Luminance](https://en.wikipedia.org/wiki/Luminance).

To calibrate the gamma response curve of a display, series of linearly spaced digital R,G,B primary color values are used to specify a color, and it's final luminance on the display are measured by a [photometer](https://en.wikipedia.org/wiki/Photometer) or [spectroradiometer](https://en.wikipedia.org/wiki/Spectroradiometer). After fitting the display response function, a counter function is constructed, usually in a [lookup table](https://en.wikipedia.org/wiki/Lookup_table), and will be applied before sending images to the display.

![Intensity Measurement of ViewSonic VX3276mhd](/assets/images/VX3276mhd_Intensity_Measurement.svg "Gamma")
![Linear Spline Correction](/assets/images/VX3276mhd_Intensity_LinearSplineCLUTTest.svg "GammaCorrection")

In Unity linear rendering mode, the final backbuffer will be encoded in [sRGB](https://en.wikipedia.org/wiki/SRGB) and usually counteracts with the gamma response curve of display, resulting an almost linear luminance response.

### HDR Rendering and HDR Display
By default, **Experica** is using the Unity High-Defination Render Pipeline(HDRP) with High Dynamic Range(HDR) rendering.This means high bits floating-point values are used to represent color model of visible lights, and the final rendering results could stored in a HDR backbuffer. In order to faithfully reproduce the HDR rendering results, a propriate HDR capable display are needed, with high luminance range and resolution.

## Measure Display Primaries Spectral
In order to get conversion matrix from digital color space, usually RGB, to photorecepter space, e.g. Cone response in retina, the spectral of RGB primaries on a specific display are measured and then combined with Cone fundamentals.

![Spectral Measurement of Sony Trinitron](/assets/images/Trinitron_Spectral_Measurement.svg "CRT Trinitron")
![Spectral Measurement of Asus ROG Swift](/assets/images/ROGPG279Q_Spectral_Measurement.svg "LCD ROGPG279Q")