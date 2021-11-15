---
title: Timing
permalink: /doc/timing
---

The time when display refresh frame could be  measured directly. A **Marker**, usually small square at corner of viewport on the topmost layer, could flip between two colors, e.g. black and white, in different frames. A [photodiode](https://en.wikipedia.org/wiki/Photodiode) can be placed on the **Marker** converting light intensity to electrical signal. By recording and analyzing the signal, the light intensity change time can be extracted and that would be the exact frame change time. 

Because the **Marker** is flipping between two colors, it would be natural to convert the photodiode analog signal to digital signal and it can be done in real-time by a [Photodiode Logic Board](https://github.com/Experica/LPC43xx_M4_AnalogToDigital).

The asymmetric [display response time](https://en.wikipedia.org/wiki/Comparison_of_CRT,_LCD,_Plasma,_and_OLED_displays) between Black->White, i.e. rising and White->Black, i.e. falling could introduce different lags when photodiode analog signal being threshold and converted to digital signal. To get the exact frame change time, these two lags should be measured and saved for the specifically configurated display and used later to correct the digital signal flip time.

![RiseLag](/assets/images/RiseLag.png "RiseLag")
![FallLag](/assets/images/FallLag.png "FallLag")

In addition to `Measure` **Marker** on display, a duplicated `Sync` digital signal is needed to provide extra robustness to recover possibly corrupted `Measure` signal.

The `Sync` signal is usually sent through Parallel Port or USB-GPIO, which should be very fast(<0.1ms) so that the external DAQ Device will be notified immediately at the time of a event. The `Command` event time is the result of the internal timer used to manage all time related functions in **Command**. In case of corrupted `Sync` signal, the internal `Command` time could be converted to external DAQ `Sync` time by a time zero delay and timer drift speed between **Command** and DAQ. These parameters could be calculated from a test run with `Sync` signal and set in experiment parameter panel.

The TimerDriftSpeed and Display Latency could be updated based on data. this is only useful in case sync and measure channles have currupted data, and timing needs those parameters to do corrections, otherwise those parameters would be automatically evaluated in dataexport

Here shows condition duration from photodiode real-time digital convertion, corrected by above asymmetric display response time.

![Long](/assets/images/Condition Duration (500ms).svg "Long")
![Short](/assets/images/Condition Duration (22ms).svg "Short")