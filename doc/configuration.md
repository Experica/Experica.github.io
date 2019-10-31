---
title: Configuration
permalink: /doc/configuration
---

In **Experica** system, each component program can be configured differently. The **Command** has a Configuration Manager that helps organizations and users to choose appropriate configuration file for each time use.

One entry in configuration file: `ExDir`, is the  directory that contains all experiment definitions. These are the experiments show on the experiment list in the Command Control Panel. By using different `ExDir`, one can setup a specific set of experiments without affecting others.

Below are some of the configure entries briefly explained.

- `IsSaveExOnQuit`: when quit Command, all opened experiments can be saved, so it remains the same when loaded next time.
- `SaveDataFormat`: currently the data are saved in YAML, a HDF5 based binary format is planed.
- `Display`: contains data describe Displays, it may include display measurement data which can be used to calibrate the display.