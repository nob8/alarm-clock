# Media
The media directory contains the following subdirectories.
## Library
`library/` contains files intended to be played as multimedia output. Initial supported formats will be *.mp3 and *.mkv. Files in `library` may be organized further in sub-folders, or not.
## Playback
`playback/` contains files that instruct the alarm clock how to play back files from the `library`. A `playback` file has the following content:

### .playback file
| name  | type | note |
|-------|------|------|
| title | String | Contains the name for the playback. This does NOT need to match the source file(s) |
| loop  | boolean | Whether playback should loop at the end of the segment list |
| shuffle | boolean | Whether the segments should be randomized before playback |
| duration | Decimal | The length of the playback, in decimal seconds. This will stop playback in the middle of a segment, if needed |
| volume | Decimal | dB volume for this playback. Keep in mind the OS volume setting still exists |
| content | PlaybackSegment List | An ordered list of PlaybackSegment |

### PlayBackSegment
| name | type | note |
|------|------|------|
| path | String | Relative path to the source file |
| start | Decimal | Decimal seconds to start playing from in the file |
| end | Decimal | Decimal seconds to stop playing at in the file |
| relativeVolume | Decimal | dB offset relative to the owning playback volume. Useful for creating alarms that ramp up |
