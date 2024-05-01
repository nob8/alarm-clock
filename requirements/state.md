# State
The state directory has a variety of read-only files that tell you about the current state of the HAL.

## `overview.state`
| Name | Type | Notes |
|------|------|-------|
| nextAlarms | AlarmDetail list | Contains the list of the upcoming 5 alarm times |
| currentTime | epoch-seconds | The current time, according to the clock |
| (optional) lightSequenceState | LightSequenceState | If implemented, the state of the running lightSequence |
| (optional) musicPlayerState | MusicPlayerState | If implemented, the state of the music player |
| (optional) weatherForecast? | WeatherForecast | If implemented, the weather forecast? |

## (optional) `musicplayer.state`
| Name | Type | Notes |
|------|------|-------|
| currentPlaylist | Playlist | The current playlist |
| visualization? | String | The name of the current visualization |
| TBD  | TBD  | TBD   |
