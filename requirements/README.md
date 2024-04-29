# The Alarm Clock
This is going to be long-running driver software for an alarm clock. The driver software receives commands from a socket, and persists state in a configurable `alarm-clock` directory.

It is assumed that native-space program/programs will read the `alarm-clock` and "do the right thing" in response to updates to that directory. The native-space program is read-only and does not lock the files.


## The `alarm-clock` directory
### Serialization
This directory will contain a number of files that need to be read by code that reads/writes to the HAL for LED control and sound control. So, serialization should be kept
easy to read from a rarely-updated C++ program. No language-specific serializers like Kryo.

To avoid depending on a specific field ordering or structure at the start, we'll make this easy and just use JSON. JSON isn't fast or space efficient, but it does write easily and has easy access to object mapping
in most languages. Later something like CapnProto or Protobuf would be a neat demo.

### Alarms directory
#### All alarms
Every alarm has a name, a ringtone, and an optional light pattern.
#### Single alarm
A single alarm is set for a specific instant in time. It fires when that time arrives, and then it's done.
#### Recurring alarm
A recurring alarm is set for a particular pattern of calendar values. For example, an alarm could be set for:
* Every Monday at 9AM
* Every Monday, Tuesday, Wednesday, Thursday, Friday at 8AM
* Every second day of the month at 5:30PM

#### Alarm file
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
