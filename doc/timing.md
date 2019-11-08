---
title: Timing
permalink: /doc/timing
---

The most accurate way to get the times display change frames is to measure it directly. **Experica** have a build-in **Marker**(a uniform color square located at corners of viewport on topmost visual layer) that flips between two colors(default are black and white) when an event occurs and needed to sync to external device. A photodiode can be placed on the **Marker** to get a analog signal of light intensity. By recording the analog signal along with other signals, the light intensity change time can be extracted and that would be the exact frame change time. 

Since the **Marker** is flipping between two colors, it would be natural to convert the photodiode analog signal to digital signal and it can be done in real-time by a [Photodiode Logic Board](https://github.com/Experica/LPC43xx_M4_AnalogToDigital).

In the following figure, we could see that there are rising lag and falling lag if thresholds are used to trigger digital signal from photodiode analog signal. These lags are the results of [display response time](https://en.wikipedia.org/wiki/Comparison_of_CRT,_LCD,_Plasma,_and_OLED_displays). For most of displays, rising time would be short, e.g. 0.01ms for CRT, 1-6ms for LCD, but the falling time could be long, e.g. 6-14ms for LCD. So these two lags should be measured for each display, and the difference between them be compensated later to get consistent frame change timing. It could be set in the **Configuration** for each display as `FallRiseLagDiff` = Lag2 - Lag1.

![Photodiode Logic Board Signal](/assets/images/FallRiseLagDiff.svg "Display Response Time")