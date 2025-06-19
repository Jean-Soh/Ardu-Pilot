---
title: Network Radio
parent: Hardware
layout: default
nav_order: 5
---
## Network Radio
An alternative to connecting to your drone is to use wifi instead. You can asssign it an IP address and if your GCS is on the same network, you can connect to it remotely instead. Some of the parameters can only be accessed after `NET_ENABLE = 1`. There are two protocols to connect mission planner to your drone, 1st is TCP the 2nd is UDP. TCP ensures all packets are delivered in the correct order and verifies their arrival with a 3 way acknowledgment system. UDP sends packets independently, without all this overhead, it can transmit data much faster. As such we will use TCP to ensure our commands from the GCS reach the drone. 
>NET_ENABLE = 1  
>NET_DHCP = 0 (important to disable the DHCP client for fixed IP addresss)   
>NET_IPADDX = 192.168.8.X  
>NET_NETMASK = 24  
>NET_OPTIONS = 1  
>NET_P1_PORT = XXXX  
>NET_P1_PROTOCOL = 2 (MAVLINK 2)  
>NET_P1_TYPE = 4 (TCP server)  
{: .note }
When connecting to the drone via TCP you have to enter the IP address as well as the port number define above
---