---
title: RC controls
parent: Software
layout: default
nav_order: 2
---
## RC controls
Sometimes you wish to influence the code using your remote, lua scripts allows you to map radio channels specifically for coding, you first have to set `RCX_OPTION = 153(Scripting)` to allow your lua script acess the RC channel. 

Next you need to create a channel handel with `scripting_rc_name = rc:find_channel_for_option(300)`. You can then use `scripting_rc_1:get_aux_switch_pos()` which returns a number depending on the position of the switch. 

----