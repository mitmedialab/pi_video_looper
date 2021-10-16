# pi_video_looper
An application to turn your Raspberry Pi into a dedicated looping video playback device.
Can be used in art installations, fairs, theatre, events, infoscreens, advertisment etc...

Easy to use out of the box but also has a lot of settings to make it fit your use case.

If you miss a feature just post an issue on github. (https://github.com/adafruit/pi_video_looper)

## Changelog
See https://github.com/adafruit/pi_video_looper#changelog

## how to install:
sudo ./install.sh

## copymode explained:
when a usb drive with video files is plugged in, they are copied onto the rpi. (with progress bar)

to protect the player from unauthorised drives a file must be present on the drive that has a filename 
as defined in the password setting in the ini file (default: videopi)

there is also a setting that controls, if files on the drive should replace the existing files or get added. (replace means that the videofiles on the rpi get deleted)
this ini setting can be overruled by placing a file named "replace" or "add" on the drive.
the default mode is "replace"

Note: files with the same name always get overwritten

## notable things:
* you can have one video repeated X times before playing the next by adding _repeat_Nx to the filename of a video, where N is a positive number
    * with hello_video there is no gap when a video is repeated but there is a small gap between different videos
    * with omxplayer there will also be a short gap between the repeats
    
* if you have only one video then omxplayer can also loop seamlessly (and wth audio)

### keyboard commands:
if enabled (via config file) the following keyboard commands are active:
* "ESC" - stops playback and exits video_looper
* "k" - sKip - stops the playback of current file and plays next file
* "s" - Stop/Start - stops or starts playback of current file
* "p" - Power off - stop playback and shutdown RPi

### screen size tips for Ingcool 7 inch screen

https://www.amazon.com/Ingcool/dp/B08RHXP9J4/?th

#### /boot/config.txt

Example:
  - `hdmi_group=2  # Display Monitor (standard)`
  - `hdmi_mode=16  # 1280×720 @ 60Hz`

Documentation
https://pimylifeup.com/raspberry-pi-screen-resolution/

More:
https://www.raspberrypi.com/documentation/computers/config_txt.html


#### omxplayer trick

Add `--win 0,12,1024,588` at the end of this line:

https://github.com/mitmedialab/pi_video_looper/blob/master/assets/video_looper.ini#L200

### troubleshooting:
* nothing happening (screen flashes once) when in copymode and new drive is plugged in?
    * check if you have the "password file" on your drive (see copymode explained above)
* if enabled (via config file) log output can be found in `/var/log/supervisor/`
  You can use e.g. `tail -f /var/log/supervisor/*` to view the logs

for a detailed tutorial visit: https://learn.adafruit.com/raspberry-pi-video-looper/installation
