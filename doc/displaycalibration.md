---
title: Display Calibration
permalink: /doc/displaycalibration
---

## Setup Display System
Display and Graphics system should be carefully setup on machines running **Experica** **Environment**, cause displays may have smart automatic adjustment or energy saving mode. Make sure the display mode and parameters is set so the brightness, contrast, etc. are what you want. On the Graphics side, parameters such as Resolution, Refresh Rate, Adaptive-Sync, etc. should also be properly adjusted.

## Calibrate Display
By default, **Experica** is using [Unity Linear Rendering](https://docs.unity3d.com/Manual/LinearLighting.html), which assume all inputs such as colors and textures are linear and no [gamma related correction](https://en.wikipedia.org/wiki/Gamma_correction) are applied by **Unity**. Mathmatically, color space specification and convertion, or lighting calculations in [Shaders](https://en.wikipedia.org/wiki/Shader) are all in linear space, so any color or texture that are gamma encoded, or displays with gamma response curve should be verified and corrected, that any linear digital color and texture, after any calculation and convertions, will result on display also Linear Physical [Luminance](https://en.wikipedia.org/wiki/Luminance).

To calibrate the gamma response curve of a display, series of linearly spaced digital R,G,B primary color values are used to specify a color, and it's final luminance on the display are measured by a [photometer](https://en.wikipedia.org/wiki/Photometer) or [spectroradiometer](https://en.wikipedia.org/wiki/Spectroradiometer). After fitting the display response function, a counter function is constructed, usually in a [lookup table](https://en.wikipedia.org/wiki/Lookup_table), and will be applied before sending images to the display.

![Intensity Measurement of ViewSonic VX3276mhd](/assets/images/VX3276mhd_Intensity_Measurement.svg "Gamma")
![Linear Spline Correction](/assets/images/VX3276mhd_Intensity_LinearSplineCLUTTest.svg "GammaCorrection")

In Unity linear rendering mode, the final backbuffer will be encoded in [sRGB](https://en.wikipedia.org/wiki/SRGB) and usually counteracts with the gamma response curve of display, resulting a almost linear luminance response.
