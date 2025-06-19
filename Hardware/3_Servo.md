---
title: Servos
parent: Hardware
layout: default
nav_order: 3
---
## Servos
Most servos are contorlled via Pulse Width Modulation (PWM) typically between 1000 to 2000 with 1500 for the center. They have 3 pins, one for VCC, one for ground, last for the PWM signal. 

The default for ardurover for turning is tied to servo 1 SERVO1_FUNCTION = 26. While the throttle is tied to servo 3 SERVO_FUNCTION = 70. There are 3 different configurations for motor drivers that is controlled with the MOT_PWM_TYPE parameter they are, “Normal” is the most common and involves sending PWM values normally between 1000 and 2000 (1ms ~ 2ms), “Brushed With Relay” is for brushed motor drivers that use a relay pin to indicate whether it should rotate forward or backward, “Brushed BiPolar” is for brushed motor drivers that, a bit like “Normal” PWM. These devices interpret a low PWM value for reverse, a high PWM value for forward.  
## Arming  
Typically to prevent accidental activation of the throttle, arming the drone is required. This is typically tired to RC6 but you can confgure this to any RC channels with RCX_OPTION = 153(ARM/DISARM). You should also configure the behaviour of the throttle when the device isn't armed as some ESC will throw an error when it dosen't recve a PWM signal MOT_SAFE_DISARM = 0(PWM enabled while disarmed). 
>It will go to the RCX_TRIM value when disarmed so ensure it is at a value where the motor is not on or the drone will run when it is disarmed. 
{: .warning }
You can check everything by leaving your motors and servos disconnected and go to Setup>Mandatory Hardware>Servo Output to ensure the behaviour of the servos are set-up correctly.

----