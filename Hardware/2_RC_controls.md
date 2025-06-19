---
title: RC controls
parent: Hardware
layout: default
nav_order: 2
---
## RC controls
We will be looking at the [RP1](https://www.radiomasterrc.com/products/rp1-expresslrs-2-4ghz-nano-receiver) receiver along with the [Radiomaster Boxer](https://www.radiomasterrc.com/products/boxer-radio-controller-m2). First download ExpressLRS ... if you are struggling here is a guide that might prove usefull [Pairing guide](https://www.youtube.com/watch?v=J3Hg2f7RL1A&t=1466s).

There are times when you do not need the feedback from the FC to the remote, or you can't afford a serial connection for your reciver. You can configure an [SBUS](https://oscarliang.com/how-to-output-sbus-from-an-expresslrs-receiver/) output from an ExpressLRS Receiver.
>RC_PROTOCOLS = 512(CRSF) or 8(SBUS)  
>If you're using CRSF protocol you need to set the serial protocol and baud rate  
>SERIALX_PROTOCOL = 23  
>SERIALX_BAUD = 57
{: .note }
Under setup > Manditory Hardware > Radio calibration you should see all the various channels on your contorller.  When you move the joysticks you should see it refeclted on the screen. The vaious joysticks and switches are mapped to channels which can be configured on your controller. These channels can then be mapped to various functions of the drone. For this simple drone boat we will only be using 3 channels, throttle, streeing, arming.


---