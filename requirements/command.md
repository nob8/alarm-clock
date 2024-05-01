# Command
Commands can be sent to the alarm clock by placing them in this folder. Command files can have any name, but for ease of use should be prefixed with the timestamp they were sent on.

## Command file content

| Name | Type | Notes |
|------|------|-------|
| date | Timestamp | Time at which the command was sent. Commands will be resolved in time order |
| command | String | Name of the command to execute |
| args | String List | Parameters for the command. Later, it would be nice if the commands were modeled and validated |

## Commands

| Name | argument 1 | argument 2 | Notes |
|------|------------|------------|-------|
| settimezone | Time zone name | | It would be kind to provide users a prefilled selector for this |
| testalarmsound | alarm name | | Manually play an alarm sound |
| stopall | | | Stop all media and lighting |
| mute | | | Immediately silence all sound |
| unmute | | | Un-set the mute status |
| snooze | (optional) Minutes | (optional) Alarm name | Stop the alarm and re-schedule it minutes in the future. Defaults are 5 mins and the current alarm |
