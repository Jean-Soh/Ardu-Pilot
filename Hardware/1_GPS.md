---
title: GPS
parent: Hardware
layout: default
nav_order: 1
---
## GPS
The first step is to identify what serial protocal the GPS is using. Some GPS use a CANbus, others use UART or I2C. 

The first GPS we will be looking at is the [MATEKSYS GNSS M9N-G4-3100](https://www.mateksys.com/?portfolio=m9n-g4-3100). This is an example of a GPS that uses a CAN protocol.You have to wire up CAN high and CAN low, typically there is a jst provided to connect to the flight contorller.
>CAN_D1_PROTOCOL = 1  
>CAN_P1_DRIVER = 1  
>GPS_TYPE = 9 (droneCAN)
{: .note }
Lastly you need to check the COMPASS_TYPEMASK, ensure that DroneCAN is Unchecked. 

The next GPS will be the [Micro M9N GPS](https://holybro.com/collections/gps/products/micro-m9n-gps). This uses both UART and I2C protocol, the UART is for the GPS while the compass is on the I2C. Checking the UART mapping you can see that GPS1 is mapped to serial 3.
>SERIAL3_BAUD = 230  
>SERIAL3_PROTOCOL = 5  
>GPS_TYPE = 2 (uBlox)
{: .note }
Similarly you need to check the COMPASS_TYPEMASK, ensure that uBlox is Unchecked. 

---