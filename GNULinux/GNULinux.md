# GNU/Linux

This is a set of notes on learning more about GNU/Linux.

## Learning GNU/Linux in a self-paced way

I am frequently asked how to learn GNU/Linux.  The fastest way to learn is to
install a GNU/Linux distribution on your computer and use it everyday.  Figure
out how to do all of the tasks you would normally do with a computer using only
free, libre, and open source software.

The second thing that has advanced my career with GNU/Linux the most is taking
notes.

When I am about to do something new, I first write out what I am trying to do,
the problem that I am trying to solve, or the original error message.  I then
research the topic.  I take notes on the research and add the relevant links.
Before I enter in any commands from the Internet, I try to understand the
commands and switches as thoroughly as possible.  I document the commands I use
and add any notes about what each command does.  If I forgot to document my
commands, I can piece them together by looking at the. bash_history file.

If I messed up something, I should be able to refer to my notes and undo any
changes.  I then document that process.

Months later when the issue arises again and I have forgotten the process, I can
look at my notes instead of restarting over again at the research phase.

Here are some other resources that can help you along the way:

- [Codecademy](https://www.codecademy.com/learn/learn-the-command-line) is a
  great interactive way to learn programming languages for the web.  They have a
  quick course on using the UNIX and GNU/Linux command line.  Expect to spend
  about an hour on this course and it should be done in one sitting.
  https://www.codecademy.com/learn/learn-the-command-line

  Other useful courses on Codecademy: Their HTML + CSS course is very quick and
  useful.  Their Python 2 course is VERY good.

- [The Linux Foundation](https://training.linuxfoundation.org/linux-courses/system-administration-training)
  has a series of free MOOCs about understanding and learning "Linux" for the
  enterprise.
  https://training.linuxfoundation.org/linux-courses/system-administration-training

  [Introduction to Linux](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-0)
  is their popular course and the one you should start with.
  https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-0

  Add any courses you complete to your resume.

- [Linux Journey](https://linuxjourney.com/) has milestones to help you learn
  GNU/Linux as if you were playing an RPG game sort of.
  https://linuxjourney.com/

- If you do not have permission to install another operating system or dual-boot
  your machine, you can use a Virtual Machine manager such as
  [VirtualBox](https://www.virtualbox.org/) to practice installing and using an
  operating sytem that you may not be familiar with.  Install
  [Ubuntu Server](https://www.ubuntu.com/download/server),
  [Lubuntu](https://lubuntu.net/downloads/), or
  [Debian](https://www.debian.org/) as a virtual machine and follow along with
  the tutorials in a course.

- [The Linux Command Line](http://linuxcommand.org/tlcl.php) By William Shotts
  and published by No Starch Press is an excellent book to learn some of the
  basics about the command line.  You can also download the PDF free from
  [his page](http://sourceforge.net/projects/linuxcommand/files/TLCL/17.10/TLCL-17.10.pdf/download).

- [The Debian System Administrator's Handbook](https://debian-handbook.info/) is
  a useful ebook for learning system administration techniques.

- Self reference -  All commands have built in help.

```
cat -h
cat --help
man cat
```

- [Explainshell](http://explainshell.com/) pulls relevant man page information
  for commands that are entered.
- [The Arch wiki](https://wiki.archlinux.org/) contains a large amount of
  quality information about GNU/Linux.  Arch is an operating system, but the
  information is very useful for all GNU/Linux distributions.
- [overthewire](http://overthewire.org/) is a series of games.
  [Bandit](http://overthewire.org/wargames/bandit/) is a game played through
  SSH.  Try to get the next level's password by figuring out a command line
  concept.
- [cmdchallenge](https://cmdchallenge.com/) has tricky problems that can be
  solved with UNIX one-liners (web based).
- [vim adventures](https://vim-adventures.com/) teaches vim like an old school
  rpg.  vim is a command line text editor like nano, but FAR more powerful and
  customizable.
- Stay up-to-date with changes by subscribing to relevant news sources such as:
  - [LWN.net](https://lwn.net/)
  - [Linux Today](https://www.linuxtoday.com/)
  - [Linux Insider](https://www.linuxinsider.com/)
  - [LXer](http://lxer.com)
  - [News from the Free Software Foundation](https://www.fsf.org/news)
  - [Electronic Freedom Foundation](https://www.eff.org/)
  - Subreddits
    - [/r/linux](https://www.reddit.com/r/linux/)
    - [/r/linux4noobs](https://www.reddit.com/r/linux4noobs/)
    - [/r/linuxquestions](https://www.reddit.com/r/linuxquestions/)
  - Magazines
    - [Linux Format](https://www.linuxformat.com/)
    - [Linux Magazine](http://www.linux-magazine.com/)
    - [Linux Journal](https://www.linuxjournal.com/)
    - Raspberry Pi's [MagPi](https://www.raspberrypi.org/magpi/)
  
## Suggested Distributions

- [Debian](https://www.debian.org/) - Community driven, stable OS with only
  libre software by default.  https://www.debian.org/
- [Ubuntu Studio](https://ubuntustudio.org/) - Targeted towards those interested
  in graphic design and audio/video production activities.
  https://ubuntustudio.org/
- [Trisquel](https://trisquel.info/) - Based on Ubuntu, but with all non-free
  software removed.  https://trisquel.info/
- [Arch](https://www.archlinux.org/) - Bleeding edge community driven distro
  based on minimalism and simplicity.  https://www.archlinux.org/
- [Parabola](https://www.parabola.nu/) - Arch Linux with non-free software
  removed.  https://www.parabola.nu/
- [Fedora](https://getfedora.org/) - Community driven development branch of Red
  Hat Enterprise Linux.  https://getfedora.org/
- [CentOS](https://www.centos.org/) - Stable community driven branch of Red Hat
  Enterprise Linux.  https://www.centos.org/
- [Ubuntu Server](https://www.ubuntu.com/download/server) - Ubuntu without a
  graphical user interface (GUI) is a popular choice for enterprise servers.
- [Lubuntu](https://lubuntu.net/downloads/) - Ubuntu with the LXDE desktop
  environment (DE) is good for older computers.

## Proprietary NVIDIA drivers

See my [NVIDIA](https://github.com/TechnologyClassroom/nvidia) repository for
bash scripts to help make installing proprietary NVIDIA drivers and CUDA.

Note: If privacy is a concern of yours do not use the proprietary NVIDIA
drivers as they contain telemetry that cannot be turned off.  Instead use the
nouveau driver if you must use NVIDIA hardware.

## Stress testing CPU on debian based systems

http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature
http://www.tecmint.com/linux-cpu-load-stress-test-with-stress-ng-tool/

```apt update && apt install lm-sensors stress stress-ng```

If lm-sensors and stress are not found, add universe to the
/etc/apt/sources.list file.

```sensors && uptime && stress --cpu 8 -v --timeout 30s && uptime && sensors```

See my [HardwareTest](https://github.com/TechnologyClassroom/HardwareTest)
repository for more thorough, comprehensive tests.

## UEFI Install resources

http://ubuntuforums.org/showthread.php?t=2147295

## Samba Network Shares

If you want to share files between Windows and GNU/Linux, you can use samba.

```sudo apt-get install samba samba-client```

Modify the configuration file.

```sudo nano /etc/samba/smb.conf```

Add the details for your share at the bottom of the page.  Here is an example
that worked as a public folder:

```
[TestShare]
path = /home/noob/test # Folder directory
public = yes
force user = noob # Replace noob with the username of the owner of the folder.
guest ok = yes
writable = yes
read only = no
create mask = 0755
```

Restart samba for changes to take effect.

```sudo /etc/init.d/samba restart```

## Useful commands

Upgrade pip

```
sudo pip install --upgrade pip
sudo pip3 install --upgrade pip
```

Seach within files for a string and list the filenames with matches

```grep string -l *```

Install tldr offline examples

```
sudo npm install -g tldr
tldr --update
tldr tar
```

Source https://github.com/tldr-pages/tldr

Access common examples from command line without installing additional packages.

```curl cheat.sh/tar```

Replace tar with the program name.

Source https://github.com/chubin/cheat.sh

List cronjobs.

```
crontab -l
```

Edit cron jobs as root.

```
sudo crontab -e
```

Edit cron jobs as another users.

```
sudo crontab -u username -e
```

## Add drive to fstab manually

I often find myself trying to set a drive to automatically boot on a system.

List the drives by uuid.

```ls -la /dev/disk/by-uuid/```

Find the one you want and complete the ls entry using tab completion.

```ls -la /dev/disk/by-uuid/926c2f9e-239d-4f4b-8bfd-f937f0de253f```

As root, remove the first part and replace it with echo and append it to the
/etc/fstab file.

```echo 926c2f9e-239d-4f4b-8bfd-f937f0de253f >> /etc/fstab```

Edit /etc/fstab as root.

```nano /etc/fstab```

Modify the line to look like this.

```UUID=926c2f9e-239d-4f4b-8bfd-f937f0de253f /mnt/desiredtmountpoint      ext4    defaults        0       2```

Change desired mountpoint to that of your chosing.  CTRL+X, y, enter

## Blink lights

Blinking drive lights is useful for checking drive led lights through GPIO
cables on servers

Debian based systems can install ledmon.

```
sudo apt-get update
sudo apt-get install -y ledmon
sudo ledctl locate=/dev/sda
sudo ledctl locate_off=/dev/sda
```

Red Hat based systems come with sgpio.

Sometimes the numbers are backwards.

```
su
sgpio -p 1 -s locate
sgpio -p 1 -s off
```

## CentOS 7 Minimal notes

```
nmtui # CLI network manager
yum update -y # Update all software to the latest version
yum groups install -y Development\ Tools # Install the Development Tools group
yum install -y tmux # Install tmux
yum install -y nano # Install nano
yum clean all # Clean package cache
```

## opensuse tumbleweed notes

Look for a package.

```cnf man```

Install package.

```sudo zypper install -y -l man```

Update packages.

```sudo zypper update -y -l```

Update distribution packages

```sudo zypper dist-upgrade -y -l```

# Exit QEMU

```
CTRL+ALT+2
quit
```

## Troubleshooting

Problem: fat32 and fat16 formatted flash drive gives errors and has trouble
booting.

Solution: Use GNU/Linux command line tools to inspect and repair problems.

This command checked the fat32 partition for errors.  If errors are found, fix
them automatically.  /dev/sdc is my flash drive in this example.

```sudo dosfsck -w -r -l -a -v -t /dev/sdc1```

dosfsck complained about a dirty bit and could not automatically repair.  This
command can fix a dirty bit:

```sudo fsck.vfat /dev/sdc1```

My response was 2 to restore backup.

My response was 1 and y to remove dirty bit.

Sources:
http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system
https://bbs.archlinux.org/viewtopic.php?id=164185

Problem: nodejs cannot find the correct path.  Gives error:

```/usr/bin/env: node: No such file or directory```

Solution: Improperly named nodejs needs to be linked to node.  Create symlink
with:

```sudo ln -s /usr/bin/nodejs /usr/bin/node```

From digitalmediums at https://github.com/nodejs/node-v0.x-archive/issues/3911

Problem: Password is too short.
Solution: Allow passwords of any length

Note: Only use this for standard account

http://ubuntuhandbook.org/index.php/2015/06/minimum-password-length-ubuntu/

```sudo nano /etc/pam.d/common-password```

Remove the word 'obscure' and save.

Problem: Ubuntu defaults to dash instead of bash.  Bash scripts sometimes do not
work.

Solution: Remove links to dash and repace link to bash.

```
sudo rm /bin/sh # Remove symlink to dash
sudo ln -s /bin/bash /bin/sh # Symlink bash to sh
exec bash # Restart shell
```

Links for directories work the same way.

```sudo ln -s /data/software/drivers/linux /usr/share/nginx/html/```

Restart network stack with Ubuntu 16.04 server
sudo systemctl restart NetworkManager.service

Problem: Ubuntu 16.04 crashes on apt-get update.
Solution: Something changed in Ubuntu 16.04 during the Summer of 2017 and
libappstream3 breaks updates.  Remove libappstream3 to fix the problem.

```sudo apt-get purge -y libappstream3```

Problem: Ubuntu skips grub menu

Solution: During boot, hold Shift to access a hidden grub menu.

If that does not work, edit the /etc/default/grub file.

```sudo nano /etc/default/grub```

Add a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0.  CTRL+X, y, enter
to save.

Update grub.

```sudo update-grub```

Modified from Eric Carvalho & Vojtech Trefny at
http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time

Problem: Ubuntu 16.04 does not manage the network devices.  dhcp can be set
manually.

Solution: Edit config file and set managed equal to true.

```sudo nano /etc/NetworkManager/NetworkManager.conf```

Change ```managed=false``` to ```managed=true```.  CTRL+X, y, enter

Problem: Ubuntu's outdated Sugar DE clobbers the cursor outside of sugar

Solution: Reset cursor theme

```gsettings reset org.gnome.desktop.interface cursor-theme```

Problem: No audio output and command line only.

Solution: Use amixer to toggle your output.

```
amixer # Lists all outputs
amixer sset Headphone toggle
```

Problem: gem install fails with message:

```
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h
```

Solution: Install ruby dev packages.

```
sudo apt-get update 2>/dev/null
sudo apt-get install -y ruby-dev 2>/dev/null
sudo apt-get install -y ruby2.0-dev 2>/dev/null
sudo apt-get install -y ruby2.2-dev 2>/dev/null
sudo apt-get install -y ruby2.3-dev 2>/dev/null
sudo yum install -y ruby-devel 2>/dev/null
sudo zypper install -y ruby-devel 2>/dev/null
```

Problem: All ethernet devices are not shown in ifconfig on Ubuntu Server 16.04.

Solution: List all cards and manually add them to /etc/network/interfaces

Lists all network ports.  Network ports are something like eth0, em1, p4n1,
enp3s0, and wlan0.

```ip link show```

Edit the /etc/network/interfaces file.

```sudo nano /etc/network/interfaces```

Use the template shown with lo for all of your network ports.  CTRL+X, y, enter

Problem: Keyboard incorrectly set to international and your minimal install does
not have the GUI tools to fix this problem

Solution: Change default keyboard settings in /etc/default/keyboard

```sudo nano /etc/default/keyboard```

Remove intl from XKBLAYOUT and XKBVARIANT.  Hold CTRL and press X, press y, and
press the enter or return key.

Problem: Debian asks for the installation CD while updating repositories.

Solution: Remove the cdrom source from the /etc/apt/sources.list file.

```sudo nano /etc/apt/sources.list```

Add a # at the beginning of the line that starts with "deb cdrom" and leave
everything else.  Hold CTRL and press X, press y, and press the enter or return
key.

Problem: Ubuntu machine lost power during an install.

Solution: Log into TTY and attempt to fix packages.

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt update
sudo apt upgrade -y
sudo apt-get dist-upgrade -y
sudo shutdown -r now
```

If this does not fix the problem, backup and reinstall.

Problem: The default program is not the preferred choice.

Solution: Change default applications.

```sudo update-alternatives --config```

Use tab completion after this to list all options.  I use:

```
sudo update-alternatives --config editor
sudo update-alternatives --config x-terminal-emulator
sudo update-alternatives --config x-www-browser
```

Problem: How do I find which display manager I am using with systemd?

Solution: Run this command:

```
cat /etc/systemd/system/display-manager.service | grep ExecStart
```

Problem: During a Ubuntu 16.04 upgrade, I receive the error:

```
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
```

Solution: Remove grub and reinstall grub-efi.

```
sudo apt-get purge -y grub\*
sudo apt-get install -y grub-efi
sudo apt-get autoremove -y
sudo update-grub
```

Based on John and David Foerster at https://askubuntu.com/questions/763472

Problem: Installing vim, changes vi.

Solution: Change vim to vim.tiny

```sudo update-alternatives --config vi```

There are 2 choices for the alternative vi (providing /usr/bin/vi).

```
  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/vim.basic   30        auto mode
  1            /usr/bin/vim.basic   30        manual mode
  2            /usr/bin/vim.tiny    10        manual mode

Press <enter> to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/vi (vi) in manual mode
```

Problem: Num lock is off after reboot.

Solution: Install numlockx and insert the command into your rc.local file.

```
sudo apt-get install numlockx
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local
```

https://help.ubuntu.com/community/NumLock

Problem: This message appears when you login to a server: `-bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)`

Solution: Run this command `locale-gen en_US.UTF-8` as root.
