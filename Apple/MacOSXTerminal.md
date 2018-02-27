# Terminal Commands for Mac OS X

Michael McMahon

Here are examples of programs I use on the Mac to help create a creative and
safe environment for the kids.

I use the Terminal often on Mac as it is a UNIX system.  Mac uses outdated
terminal commands before GPL v3 I think.  Many of the common gnu tools are
there.  Homebrew (a port system) automates the download and build process of
common open source software.  The software available to homebrew is limited, but
includes some favorites such as minetest and wget.

Here is a command to copy the contents of a file with admin rights as a limited
user:

```
su adminnamehere -c sudo\ cp\ /Users/adminnamehere/HOSTSFmac.txt\ /etc/hosts
su adminnamehere -c sudo\ cp\ /Users/adminnamehere/HOSTSMTWRmac.txt\ /etc/hosts
```

Another su example using ls to explore system directories that require root:

```su adminnamehere -c ls\ /Users/adminnamehere```

Notice that the escape \ character is required before spaces.  Also, note that
the admin password is required twice (once for su and once for sudo).

This command locks the dock:

```
defaults write com.apple.dock contents-immutable -bool true && killall Dock
```

This command unlocks the dock:

```
defaults write com.apple.dock contents-immutable -bool false && killall Dock
```

This command displays the calendar for the year:

```cal 2016```

This command finds the IP address of a webpage and checks connectivity:

```ping www.google.com```

This command lists the IP addresses of the computer:

```ifconfig | grep inet```

This command lists the usernames:

```ls /Users```

This command backup minetest worlds.  Incredibly useful against "griefer"
culture:

```mkdir -p ~/Documents/BAK/minetest/$(date +%Y-%m-%d) && cp -R ~/Library/Application\ Support/minetest/worlds/ ~/Documents/BAK/minetest/$(date +%Y-%m-%d)/```

Same concept for that other one

```mkdir -p ~/Documents/BAK/minecraft/$(date +%Y-%m-%d) && cp -R ~/Library/Application\ Support/minecraft/saves/ ~/Documents/BAK/minecraft/$(date +%Y-%m-%d)/```

Python shell

```python```

Edit text

```
vi textfile.txt
nano textfile.txt
```

Compile C

```gcc textfile.c```

Send words out of the speakers:

```say hello```

Other available, useful programs include ssh, rsync, ls, cd, cat, cp, mv, rm,
su, sudo, passwd, less, grep, ifconfig, vi, vim, nano, zip, unzip, gzip, bzip2,
tar, base64, curl, uname, svn, head, tail, sqlite3, sort, git, gcc, sed, awk,
file, expect, ruby, rails, python, php, perl, col, cal, calendar, mkdir, say,
visudo, traceroute, chroot, chown, whatis, whereis, which, whoami, pwd, uptime,
users, etc.

To list most of the available programs that are not included in the
/Applications folder, run this command

```ls /usr/bin && ls /usr/sbin```

## Make a bootable install USB for OS X Mavericks

http://forums.macrumors.com/threads/how-to-make-a-bootable-install-of-mavericks-on-flash-usb-drive.1649986/#post-18081307

An 8GB USB drive must be titled Untitled and formatted as Mac OS Extended
(Journaled) using Disk Utility.

```sudo /Applications/Install\ OS\ X\ Mavericks.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ Mavericks.app --nointeraction```

Hold the alt or option key to boot from the USB

## Boot with Single User Mode

Hold Command-S

## Download a directory of files

```wget -nc -r --no-http-keep-alive http://download.folder/here```

## Connect to a Raspberry Pi

```ssh pi@ipaddressofpi```

## Copy file to Raspberry Pi

```scp /Directory/path/of/file.zip pi@ipaddressofpi:/home/pi```

## Puppet

```/opt/puppetlabs/puppet/bin/puppet```

## Force SketchUp to close as limited user.

SketchUp starts in a window without the standard red button to exit.  This can
prevent a shutdown.

```su Computer\ Clubhouse -c sudo\ pkill\ -9\ SketchUp```
