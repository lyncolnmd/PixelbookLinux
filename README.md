~~FYI THIS DOES NOT WORK ON ANY DISTRIBUTION OR SETUP USING A KERNEL GREATER THAN 6.0! (I BELIEVE 6.1.1 IS THE LAST WORKING KERNEL) UNTIL THEN ALL PIXELBOOK USERS SHOULD STAY ON KERNEL 6.0 OR LOWER. ALL FEATURES WILL BE WORKING NATIVELY EXCEPT THE AUDIO, THE ACCELEROMETER AND THE KEYBOARD TOP ROW... THIS GITHUB OUTLINES THOSE FIXES. FOR DISTRIBUTIONS WITH THE LTS KERNEL (5.15) EXPECT THAT THE BACKLIGHT WILL NOT WORK OUT OF THE BOX. KERNEL 5.17 AND ABOVE HAS FIXED THIS ISSUE.~~ (This should be fixed now)

## Installing ALSA drivers and configuration files for the Pixelbook (Eve) Under Linux.

### Manual Method

Copy the files to the respective locations according to the paths listed below:

```
  /lib/firmware/9d71-GOOGLE-EVEMAX-0-tplg.bin

  /lib/firmware/dsp_lib_dsm_core_spt_release.bin

  /lib/firmware/intel/dsp_fw_C75061F3-F2B2-4DCC-8F9F-82ABB4131E66.bin

  /opt/google/dsm/dsmparam.bin

  /usr/share/alsa/ucm2/Intel/kbl-r5514-5663-/Hifi.conf

  /usr/share/alsa/ucm2/Intel/kbl-r5514-5663-/kbl-r5514-5663-.conf

  /usr/share/alsa/ucm2/conf.d/kbl-r5514-5663-/Hifi.conf (or create a symbolic link to the file in the intel folder)

  /usr/share/alsa/ucm2/conf.d/kbl-r5514-5663-/kbl-r5514-5663-.conf (or create a symbolic link to the file in the intel folder)

  /usr/lib/udev/hwdb.d/61-eve-sensor.hwdb

  /usr/lib/udev/hwdb.d/61-eve-keyboard.hwdb
```

After installation of the files run

```
  systemd-hwdb update
```

This will update th hwdb to allow the accelerometer and keyboard to work correctly

## Automated method

Install ansible (it'll be called either `ansible` or `ansible-core` on most Linux OSes. Install it using `yum`, `dnf`, `apt-get`, `pacman`, or similar)

`cd` into the repo and start the playbook like this:

```
ansible-playbook -K playbook.yaml
```

You will be prompted for your `sudo` password (so Ansible can do actions as `root` where needed)

Let ansible do its thing


## Note about Pipewire

The audio drivers WILL NOT work with pipewire. They will give sound but its mostly slow playing and covered by white noise (you can try it if you like to see what im talking about) For this reason we must replace pipewire with pulseaudio. Of note, HDMI/DP Out is not working on Ubuntu 22.10 or later nor is it working under fedora systems but it does work with Ubuntu 22.04 and Linux Mint. (Those OSes have pulseaudio natively installed and maybe their configurations allow for HDMI/DP out to work but at this point I have not figured out how to get it working on newer versions where pulseaudio needs installation. I have also tried it under Arch. HDMI/DP does not work even with Pulseaudio natively installed.


TO INSTALL PULSEAUDIO ON UBUNTU 22.10 OR LATER (May also be applicable to Pop!OS)

Run the following commands:

```
  sudo apt install pipewire-media-session (this will remove wireplumber)

  sudo apt install pulseaudio

  sudo apt remove pipewire-pulse (this will stop pipewire from attempting to run its daemon and give way to pulseaudio)
  
  sudo apt remove pipewire-alsa
```

TO INSTALL PULSEAUDIO ON FEDORA

```
  sudo dnf swap --allowerasing pipewire-pulseaudio pulseaudio
  
  sudo dnf swap wireplumber pipewire-media-session
  
  sudo dnf swap pipewire-jack-audio-connection-kit jack-audio-connection-kit
  
  sudo dnf remove pipewire-alsa
```
