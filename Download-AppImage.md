## Download and Run

The most recent [releases](https://github.com/pdf2htmlEX/pdf2htmlEX/releases) have [AppImages](https://appimage.org/) built on a range of recent Ubuntu releases.

An AppImage is a self contained collection of an executable (such as `pdf2htmlEX`) and any non-standard libraries that it depends upon.

This means that an AppImage *should* be able to be run on most modern GNU/Linux distributions. Simply:

1. Download the `*.AppImage` file from our [releases page](https://github.com/pdf2htmlEX/pdf2htmlEX/releases).
2. Make the downloaded image executable using the file browser or the `chmod a+x ` in the command line.
3. Run it...

Our AppImages are known to work on Ubuntu, and recent Windows 10 (with ['Windows Subsystem for Linux'](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux)).

Unfortunately our AppImages are unlikely to run on the MacOSX platforms ([since MacOSX can not work with the FUSE subsystem](https://github.com/AppImage/pkg2appimage/issues/96)).

## Configuration

While an AppImage contains its own copies of any non-standard shared libraries, it does depend upon any local configuration found in your `/etc` directories.

In particular, our AppImage will use *your* Fontconfig, and iconv configuration.

## Dependencies

The following packages are needed for a full installation (principally for their associated configuration):

```
sudo apt -y install libfontconfig1
#   fontconfig-config fonts-dejavu-core libfreetype6 libpng16-16 ucf
sudo apt -y install libglib2.0-0
#   libglib2.0-data libicu60 libxml2 shared-mime-info xdg-user-dirs
sudo apt -y install libxcb1
#   libbsd0 libxau6 libxdmcp6 multiarch-support
sudo apt -y install libx11-6
#   libx11-data

```