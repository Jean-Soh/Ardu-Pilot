---
title: Software
layout: default
nav_order: 2
---

ArduPilot has introduced support for Lua scripting. Scripting provides a safe, “sandboxed” environment for new behaviors to be added to the autopilot without modifying the core flight code. Scripts are stored on the SD card and run in parallel with the flight code.

Ensure your autopilot has at least 2 MB of flash and 80 kB of memory. High powered autopilots like the CubePilot Cube Orange and HolyBro Durandal will certainly work well but check the specifications of your autopilot. Scripting is not available in F4 based autopilots. Autopilots must have an SD card to store the script. 

Upload scripts (files with extension .lua) to the autopilot’s SD card’s APM/scripts folder. Set SCR_ENABLE = 1 to enable scripting, this also creates the folder. This folder can also be created manually on the SD card. You can access it via the GCS like mission planner or you can write directly into the SD card just ensure that the file path is correct.

For developing new scripts you can look [here](https://github.com/ArduPilot/ardupilot/tree/Rover-4.3/libraries/AP_Scripting/examples) for examples.