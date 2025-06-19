---
title: Flight controller
parent: Hardware
layout: default
nav_order: 0
---
## Flight controller
The first step is to flash ardupilot's firmware onto your flight controller. You can easliy do this by connecting it to your computer and opening up [Mission Planner](https://firmware.ardupilot.org/Tools/MissionPlanner/MissionPlanner-latest.msi). Once you are connected simply go to the setup tab and click on install firmware, the version of rover that you want to use and you're all set.

Although most setting are flight controller agnostic, it's important to take note of the UART mapping. For example if I were to set up a GPS on the [MATEKSYS H743-WLITE](https://www.mateksys.com/?portfolio=h743-wlite), I can see that GPS1 is tied to serial 3. I will then go to serial 3 and set the baud rate and protocol. Or if I were to configure a telemetry radio on the [Pixhawk 6X](https://ardupilot.org/plane/docs/common-holybro-pixhawk6X.html), I can see that Telem1 is mapped to serial 1. Similarly I will then go to serial 1 and set the appropriate baud rate and protocol.

Anothering thing when choosing a flight controller is to look at the number of PWM outputs and GPIOs if you have many servos, motors and peripherals.

---