---
title: Intro
layout: home
nav_order: 0
---

This is a quick start to ardurover for a drone boat using [ardurover](https://ardupilot.org/rover/index.html).

The first step is choosing an AutoPilot borad, this will be the brains of your drone. We will be looking at the [MATEKSYS H743-WLITE](https://www.mateksys.com/?portfolio=h743-wlite) as well as the [Pixhawk 6X](https://ardupilot.org/plane/docs/common-holybro-pixhawk6X.html). You will also need [Mission Planner](https://firmware.ardupilot.org/Tools/MissionPlanner/MissionPlanner-latest.msi), which is a ground control station (GCS). Although if you plan on strictly using RC control it will not be needed but highly recommended. It displays real-time data on the UAVs performance and position. A GCS can also be used to control a UAV, uploading new mission commands and setting parameters. It is often also used to monitor the live video streams from a UAV’s cameras.

When you first open up mission planner, you should be on the data tab. The top right is the connect button, always remeber to set the COM port to AUTO if this is your first time connecting or if you've changed the mode of connection. Navigate to the config > full perameter list. The first thing to do is to change the FRAME_TYPE = 2(Boat). You will be doing most of the configuration in this tabs.

Place the flight controller into the drone facing the correct orientation. If you require an alternative orientation you can configure it in mission planner under [Board Orientation](https://ardupilot.org/rover/docs/common-mounting-the-flight-controller.html)

---