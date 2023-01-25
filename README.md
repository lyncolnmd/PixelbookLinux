Installing ALSA drivers and configuration files for the Pixelbook (Eve) Under Linux:

Copy the files to the respective locations according to the paths listed below:

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


After installation of the files run

  systemd-hwdb update

This will update th hwdb to allow the accelerometer and keyboard to work correctly


TO INSTALL PULSEAUDIO ON UBUNTU

Run the following commands:

  sudo apt install pipewire-media-session (this will remove wireplumber)

  sudo apt install pulseaudio

  sudo apt remove pipewire-pulse (this will stop pipewire from attempting to run its daemon and give way to pulseaudio)
  
  sudo apt remove pipewire-alsa


TO INSTALL PULSEAUDIO ON FEDORA

  sudo dnf swap --allowerasing pipewire-pulseaudio pulseaudio
  
  sudo dnf swap wireplumber pipewire-media-session
  
  sudo dnf swap pipewire-jack-audio-connection-kit jack-audio-connection-kit
  
  sudo dnf remove pipewire-alsa
