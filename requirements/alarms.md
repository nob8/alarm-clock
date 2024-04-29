# Alarms
Alarms are stored in `alarm-clock/alarms`. Each alarm is represented with its own file, serialized according to the currently selected serialization.

An alarm is defined by the following requirements:

## All alarms
Every alarm has a name, a ringtone, and an optional light pattern.

* Name is set by the user at alarm creation time. It does not need to match the name of the alarm file, and probably should not so users can use the same name multiple times if desired.
* Ringtone is a string reference to a Media object. The Media object is handled by the Media subsystem LINK GOES HERE
* Light pattern is a string reference to a LightSequence object. The LightSequence object is handled by the Lights subsystem LINK GOES HERE

Generally, alarms do not need to think about what happens after they fire. They should not inspect the Media or LightSequence length. 
Alarms may overlap, and it is ok to let that happen: the HAL layer will use a simple tiebreaker to determine which alarm gets to execute.

## Single alarm
A single alarm is set for a specific instant in time. It fires when that time arrives, and then it's done.
## Recurring alarm
A recurring alarm is set for a particular pattern of calendar values. For example, an alarm could be set for:
* Every Monday at 9AM
* Every Monday, Tuesday, Wednesday, Thursday, Friday at 8AM
* Every second day of the month at 5:30PM
## Alarm file
Contains a series of named "alarm" files. Different alarms have slightly different field requirements, represented in this table:

| Name | Type | Details |
|------|------|---------|
| name | String | User-supplied name. Limit 80 characters |
| ringtone | String | Filename of the ringtone |
| light-pattern | String | String identifier of the light pattern |
| alarm-type | Enum | Used to switch the following optional types |
| \<SINGLE ALARM> date | long | Unix timestamp |
| \<WEEKLY/MONTHLY ALARM> hour-of-day | int | Hour for the alarm, 24-hour time |
| \<WEEKLY/MONTHLY ALARM> minute-of-hour | int | minute for the alarm |
| \<WEEKLY ALARM> day-of-week | byte | Bits 1-8 are whether the alarm is active that day. Bit 0 is checksum |
| \<MONTHLY ALARM> day-of-month | int32 | Bits 1-31 are whether the alarm is active that day. Bit 0 is checksum |
