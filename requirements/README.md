# The Alarm Clock
This is going to be long-running driver software for an alarm clock. The driver software receives commands from a socket, and persists state in a configurable `alarm-clock` directory.

It is assumed that native-space program/programs will read the `alarm-clock` and "do the right thing" in response to updates to that directory. The native-space program is read-only and does not lock the files.

## The `alarm-clock` directory
### Serialization
This directory will contain a number of files that need to be read by code that reads/writes to the HAL for LED control and sound control. So, serialization should be kept
easy to read from a rarely-updated C++ program. No language-specific serializers like Kryo.

To avoid depending on a specific field ordering or structure at the start, we'll make this easy and just use JSON. JSON isn't fast or space efficient, but it does write easily and has easy access to object mapping
in most languages. Later something like CapnProto or Protobuf would be a neat demo.

### Modules
To simplify the operation of the alarm clock, each logical subsystem for the clock will get its own sub-directory inside alarm-clock. Those directories are: 
* [alarms](alarms.md)
* [lightsequences](lightsequences.md)
* [media](media.md)
* [state](media.md)
* [command](command.md)

### Extra feature: Media player
Using the same base directories above, our alarm clock can also be a pretty sweet media player with visualizations! This will involve a new directory:
* [mediaplayer](mediaplayer.md)
  * [playlists](playlists.md)
  * [mediavisualization](mediavisualization.md)
