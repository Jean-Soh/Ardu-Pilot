---
title: GPS time
parent: Software
layout: default
nav_order: 3
---
## GPS time
If you're using a GPS you can obtain the time in your program. There are two different variables `gps:time_week(0)` and `gps:time_week_ms(0)` with the first returnig the week number and the latter returning how many ms you are into the week. knowing these two numbers, you can determine the GPS time.

There are many programs and functions available for converting between "human" time and Unix time. The more difficult part of the conversion is going between Unix time and GPS time. This is because while there was an offset of 315964800 seconds between Unix and GPS time when GPS time began, that offset changes each time there is a leap second. GPS time labels each second uniquely including leap seconds while Unix time does not, preferring to count a constant number of seconds a day including those containing leap seconds.

The first step is to get the GPS time which is achived by multiplying the `gps:time_week(0)` by 604800(seconds in a week) and adding the `gps:time_week_ms(0)` number divided by 1000(ms in a second).

Next we need to convert gps time to unix time. We first split it into the seconds and ms. We add 315964800 to the seconds due to the offset and subtract the [leapseconds](https://www.nist.gov/pml/time-and-frequency-division/time-realization/leap-seconds)

To handle the ms we will use linear interpolation to achive ms accuracy guaranting a 1-1 correspondence between gps times and unix times. As UTC and GPS time is offset by 0.5 seconds. If the following second is a secduled leap second, we will add the remianding ms by half. If the current second is a leap second we have to add the additional 0.5sec or 500ms as well. If not we simply add the ms. Below is an example of such an implimentation.

```lua
local function gps2unix(gpsTimeSeconds)
    local fpart = gpsTimeSeconds % 1
    local ipart = math.floor(gpsTimeSeconds)
    local unixTimeSeconds = ipart + 315964800 - countleaps(ipart, false)

    if isleap(ipart + 1) then
        unixTimeSeconds = unixTimeSeconds + fpart / 2
    elseif isleap(ipart) then
        unixTimeSeconds = unixTimeSeconds + (fpart + 1) / 2
    else
        unixTimeSeconds = unixTimeSeconds + fpart
    end
    return unixTimeSeconds
end
```

There are many programs and functions available for converting between "human" time and Unix time. You can read more about the algorithm [here](https://www.geeksforgeeks.org/convert-unix-timestamp-to-dd-mm-yyyy-hhmmss-format/). Below is such an implimentation. 

```lua
local function unix2str(unixTimeSeconds, tz_offset)
    local epoch = 946684800 -- January 1, 2000, 00:00:00 (UTC)
    local secondsInDay = 86400
    local offset = tz_offset or 0  -- default to UTC if tz_offset not specified
    unixTimeSeconds = unixTimeSeconds + offset * 3600

    local days = math.floor((unixTimeSeconds - epoch) / secondsInDay)
    local secondsLeft = (unixTimeSeconds - epoch) % secondsInDay

    local year = 2000
    local month, day = 1, 1

    while true do
        local daysInMonth = 31

        if month == 4 or month == 6 or month == 9 or month == 11 then
            daysInMonth = 30
        elseif month == 2 then
            if year % 4 == 0 and (year % 100 ~= 0 or year % 400 == 0) then
                daysInMonth = 29
            else
                daysInMonth = 28
            end
        end

        if days >= daysInMonth then
            days = days - daysInMonth
            month = month + 1
        else
            day = days + 1
            break
        end

        if month > 12 then
            month = 1
            year = year + 1
        end
    end

    local hours = math.floor(secondsLeft / 3600)
    local minutes = math.floor((secondsLeft % 3600) / 60)
    local seconds = secondsLeft % 60

    local tz = 'UTC'
    if offset > 0 then tz = ('%s+%.1f'):format(tz, offset) end
    if offset < 0 then tz = ('%s%.1f'):format(tz, offset) end

    return ('%02d %s %04d %02d:%02d:%02d %s'):format(day, MONTH_NAMES[month], year, hours, minutes, seconds, tz)
end
```

----