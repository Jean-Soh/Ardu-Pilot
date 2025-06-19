---
title: Serial
parent: Software
layout: default
nav_order: 0
---

The serial port access object is used within ardupilot to interface serial devices. `Serial:find_serial(instance)` returns a serial port access object that allows a script to interface with a device over a port set to protocol 28 (Scripting). Instance 0 is the first such port instance 1 is the second and so on. If the requested instance is not found returns nil. By asserting if the object is nil you can find out if ardupilot has been confugured correctly.

To initalize the serial object, you need to tell it the baud rate of the device using `serial_port_access_object:begin(baud_rate)` and setting the flow control on or off.Flow control is used to tell the other device that it's buffer is full and not to send anymore data.Typically for most modern devices they do not require flow control to be enabled hence you should use `serial_port_access_object:set_flow_control(0)` or `1` if needed. lastly `serial_port_access_object:available()` returns the number of bytes available to read.

To write to the serial device you can use  `serial_port_access_object:write(value)` to write a single byte to the device or `serial_port_access_object:wrtiestring(data)` to write a string of bytes. It also returns the number of bytes written which can retrun 0 if the data is nil. 

To read data, smiliarly, there are two methods. `serial_port_access_object:read()` returns 1 byte of data and removes it form the buffer. `serial_port_access_object:readstring(count)` reuturns a string of len() = count and removes them from the buffer. It returns 0 if there are no bytes in the buffer and nil if there's an error

----