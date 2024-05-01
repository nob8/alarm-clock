# MediaPlayer
The media player sub-component of the alarm clock. Responsible for playing music and rendering video. 

## Basic Playback
The MediaPlayer sub-component should be able to handle most of the basic functions people expect
of a media player. It should be able to:
* Show the currently playing track
* Read and play playlist files, including by importing .m3u8 playback files
* Go forward, go back, seek forward, seek back, play/pause
* Start playing from a particular point in a playlist

### Alarms
But, this is still an alarm clock! An alarm should interrupt the currently playing music.

## Visualizations
But, we can go a few steps further! We have LED lights, which means we can do cool visualizations.
To facilitate this, we will also have a set of Visualizations, that can be responsive to the playing
music by varying in speed, intensity, and output.
