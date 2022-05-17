# Kodi addon repository with VDR for CoreELEC
This is the kodi addon repository providing a **F**ull-**F**eatured VDR for CoreELEC provided by df. 

This VDR distribution is based on the idea of using Kodi as a package manager for installation and automatic software update distribution since the CoreELEC does not include a full package manager.

The names of all provided addons have the prefix `ff-vdr`.

## Supported platform:
These addons are compiled for the following platform:

Project: Amlogic-ce\
Device: Amlogic-ng\
Subdevices: Odroid_N2\
Arch: arm

## List of available addons:

### Addons for CoreELEC-Version: 19.4

| Addon | Version |
| ----- | ------- |
| ff-vdr-eventlircd | 19.4.100 |
| ff-vdr-frontend | 19.4.100 |
| ff-vdr-media-modules-aml | 19.4.100 |
| ff-vdr-plugin-dfatmo | 19.4.100 |
| ff-vdr-plugin-remoteosd | 19.4.100 |
| ff-vdr-plugin-satip | 19.4.100 |
| ff-vdr-plugin-softhdodroid | 19.4.100 |
| ff-vdr-plugin-streamdev | 19.4.100 |
| ff-vdr-plugin-svdrpservice | 19.4.100 |
| ff-vdr | 19.4.100 |
| ff-vdr-repository | 19.4.100 |

## Installation steps:

- Prerequisite is an official CoreELEC image installed and configured on your device.

- Install kodi addon `locale` from the official repositories, chose your desired locale and reboot.

- In Kodi system settings allow installation of addons from unknown locations.

- Download and copy the [ff-vdr repository kodi addon](https://durchflieger.github.io/ff-vdr-coreelec-n2-odroid-repo/19.4/ff-vdr-repository/ff-vdr-repository-19.4.100.zip) to your device.

- Use `install from zip` in Kodi to install the repository addon. Further installation of ff-vdr addons in Kodi is done by using this repository as source location.

- Install addon `ff-vdr-frontend` in Kodi. This automatically installs dependend addons `ff-vdr` and `ff-vdr-plugin-softhdodroid`. 

- Depending on your requirements install additional addons for reception e.g. `ff-vdr-plugin-streamdev`, `ff-vdr-plugin-satip` or local DVB drivers (available in the official Kodi repositories).

- Open the settings in Kodi for the addon `ff-vdr` and select whether the VDR process should continue to run in the background when Kodi is running or is stopped. The former makes sense if the VDR is also used for recording. The latter if it is only used as an output client. Furthermore you can choose if the VDR or Kodi should be executed after the start of the system.

- Now it's time to do further configuration of VDR outside of Kodi e.g. copy a channel.conf and tweak settings in directory `/storage/.vdr`.

To start and/or switch to VDR exceute the `ff-vdr-frontend` addon available in the progamm group of Kodi.

To start Kodi execute the Kodi command available in the VDR menu under commands.

From a shell command line your can start, stop or switch between VDR and Kodi with `systemctl start vdr-frontend` and `systemctl start kodi`. You can directly execute these to switch. No need to stop a service first.

If your chosen mode is `continue to run VDR in background` you can start/stop the VDR process with `systemctrl start/stop vdr`.

The `ff-vdr` addon comes already with a preconfigured `remote.conf` so that your remote control and control by keyboard should be available out of the box.

## Important file locations:

- `/storage/.config/vdr/args` -> Command line arguments for VDR and VDR plugins.
- `/storage/.config/vdr/config` -> Configuration files e.g. settings.conf, channels.conf ....
- `/storage/.config/vdr/command-hooks` -> Directory for command menu entrys.
- `/storage/.config/vdr/shutdown-hooks` -> Directory for shutdown scripts.
- `/storage/.config/vdr/recording-hooks` -> Directory for recording scripts.
- `/storage/.config/vdr-frontend-hook.sh` -> Hook script called by start/stop of vdr-frontend
- `/storage/.cache/vdr` -> Directory used as cache by VDR e.g. epg.data ....
- `/storage/videos` -> Directory for recordings

## Notes for specific packages:

### ff-vdr-media-modules-aml
This package provides Amlogic media driver kernel modules which support the Picture-In-Picture feature of softhdodroid.
You should install this package only for PIP support.
After installation reboot your system.

### ff-vdr-eventlircd
This packages provides a enhanced eventlircd daemon that support sending commands to LG TV's over a serial connection.
Do not install this package.

## TODO

Unfortionally the addon management features of Kodi are limited.
They did not provid sufficient control while removing addons.
Because of that removing ff-vdr addons will currently not remove all installed resources.
