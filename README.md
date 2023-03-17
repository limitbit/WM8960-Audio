# WM8960 Audio Driver for CM4

### Install wm8960-soundcard
Get the wm8960 soundcard source code. and install all linux kernel drivers

```bash
git clone https://github.com/robotdoly/WM8960-Audio.git
cd WM8960-Audio
sudo ./install.sh 
sudo reboot
```

Check that the sound card name matches the source code wm8960-soundcard.

```bash
pi@raspberrypi:~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: wm8960soundcard [wm8960-soundcard], device 0: bcm2835-i2s-wm8960-hifi wm8960-hifi-0 [bcm2835-i2s-wm8960-hifi wm8960-hifi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
If you want to change the alsa settings, You can use `sudo alsactl --file=/etc/wm8960-soundcard/wm8960_asound.state  store` to save it.

### Usage:

#test speakers for both channels
speaker-test -twav -c2 

#capture sound 
#It will capture sound for both channels (L/R), duration 4 seconds, test.wav file name
arecord -f S16_LE -d 4 -r 16000 -c 2 test.wav
```

```bash
#play sound file test.wav
aplay test.wav
```

### uninstall wm8960-soundcard
If you want to upgrade the driver , you need uninstall the driver first.

```bash
pi@raspberrypi:~/WM8960-Audio-HAT $ sudo ./uninstall.sh 
...

------------------------------------------------------
Please reboot your raspberry pi to apply all settings
Thank you!
------------------------------------------------------
```

