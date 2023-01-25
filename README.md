Installing ALSA drivers and configuration files for the Pixelbook (Eve) Under Linux:

Copy the files to the respective locations according to the paths listed below:
/mnt/lib/firmware/9d71-GOOGLE-EVEMAX-0-tplg.bin

/mnt/lib/firmware/dsp_lib_dsm_core_spt_release.bin

/mnt/lib/firmware/intel/dsp_fw_C75061F3-F2B2-4DCC-8F9F-82ABB4131E66.bin

/mnt/opt/google/dsm/dsmparam.bin

/usr/share/alsa/ucm2/Intel/kbl-r5514-5663-/Hifi.conf

/usr/share/alsa/ucm2/Intel/kbl-r5514-5663-/kbl-r5514-5663-.conf

/usr/share/alsa/ucm2/conf.d/kbl-r5514-5663-/Hifi.conf (or create a symbolic link to the file in the intel folder)

/usr/share/alsa/ucm2/conf.d/kbl-r5514-5663-/kbl-r5514-5663-.conf (or create a symbolic link to the file in the intel folder)

/usr/lib/udev/hwdb.d/61-eve-sensor.hwdb

/usr/lib/udev/hwdb.d/61-eve-keyboard.hwdb
