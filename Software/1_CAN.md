---
title: CAN
parent: Software
layout: default
nav_order: 1
---

A CAN bus is another method of communication between the ardupilot and it's peripherals. It uses two wires refered to as CAN high (CAN-H) and CAN low (CAN-L). They use the voltage different between these two lines to transmit information.
>CAN_D1_PROTOCOL = 10 (Scripting)  
>CAN_P1_BITRATE = XXXX  
>CAN_P1_DRIVER = 1
{: .note }
To create a CAN bus device handler use `CAN:get_device(buffer_len)` where the buffer_len is the length of the buffer. 

After creating your CAN bus device handler use `CAN_buffer:read_frame()` to get a frame object and smiliarly `CAN_buffer:wrtie_frame(frame, timeout_us)` to write a frame into the bus.

Each frame object has 2 main properties, the first is it's ID `frame:id()` returns the ID and the data within the frame `frame:data(number)` unlike most things in lua, it uses 0 indexing. Number goes from 0-7

----