# GNU/Linux

This is a set of notes on learning more about GNU/Linux.

You cannot learn everything at once.

## Learning GNU/Linux in a self-paced way

I am frequently asked how to learn GNU/Linux. The fastest way to learn is to
install a GNU/Linux distribution on your computer and use it everyday. Figure
out how to do all of the tasks you would normally do with a computer using only
free, libre, and open source software. Do not try to run all of the programs
you once used, learn what the task was that you were doing and find a workflow
that can accomplish the task.

The second thing that has advanced my career with GNU/Linux the most is taking
notes.

When I am about to do something new, I first write out what I am trying to do,
the problem that I am trying to solve, or the original error message. I then
research the topic. I take notes on the research and add the relevant links.
Before I enter in any commands from the Internet, I try to understand the
commands and switches as thoroughly as possible. I document the commands I use
and add any notes about what each command does. If I forgot to document my
commands, I can piece them together by looking at the. bash_history file.

If I messed up something, I should be able to refer to my notes and undo any
changes. I then document that process.

Months later when the issue arises again and I have forgotten the process, I can
look at my notes instead of restarting over again at the research phase.

Here are some other resources that can help you along the way:

- [Linux Journey](https://linuxjourney.com/) has milestones to help you learn
  GNU/Linux as if you were playing an RPG game sort of.
  https://linuxjourney.com/

- [/r/linuxupskillchallenge](https://old.reddit.com/r/linuxupskillchallenge/) is
  a Reddit community built around a 30 day commitment to learning how to manage
  a webserver. This is a reasonable and practical way to learn the fundamentals
  of system administration.

- [overthewire](http://overthewire.org/) is a series of games.
  [Bandit](http://overthewire.org/wargames/bandit/) is a game played through
  SSH. Try to get the next level's password by figuring out a command line
  concept.

- [Codecademy](https://www.codecademy.com/learn/learn-the-command-line) is a
  great interactive way to learn programming languages for the web. They have a
  quick course on using the UNIX and GNU/Linux command line. Expect to spend
  about an hour on this course and it should be done in one sitting.
  https://www.codecademy.com/learn/learn-the-command-line

  Other useful courses on Codecademy: Their HTML + CSS course is very quick and
  useful. Their Python course was good. The quality of the free resources seems
  to have gotten worse over time.

  To get the most out of Codecademy or any other site like it where there is a
  text editor that runs code in the browser or a terminal in the browser, make
  sure you can translate the same concept to your local machine. It takes a bit
  more work to copy and paste and do everything twice, but you do not have to
  recreate each lesson. At the end of each section, make sure that you can
  locally edit text files, run them through a programming language, run a
  web server, or run the commands locally on your machine. If you skip this
  important unwritten step, you may realize that you do not actually know how
  to translate what you learned into a practical skill that you can use on your
  own computer.

- [The Linux Foundation](https://training.linuxfoundation.org/linux-courses/system-administration-training)
  has a series of free MOOCs about understanding and learning "Linux" for the
  enterprise.
  https://training.linuxfoundation.org/linux-courses/system-administration-training

  [Introduction to Linux](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-0)
  is their popular course and the one you should start with.
  https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-0

  Add any courses you complete to your resume.

- If you do not have permission to install another operating system or dual-boot
  your machine, you can use a Virtual Machine manager such as
  [VirtualBox](https://www.virtualbox.org/) to practice installing and using an
  operating sytem that you may not be familiar with. Install
  [Ubuntu Server](https://www.ubuntu.com/download/server) or
  [Debian](https://www.debian.org/) as a virtual machine and follow along with
  the tutorials in a course. If you are already using a GNU/Linux machine, I
  would recommend `virt-manager` instead of VirtualBox. I would also recommend
  using a single-board computer such as a
  [Raspberry Pi](https://github.com/TechnologyClassroom/RaspberryPiProgrammingWorkshop/)
  as they are cheap enough that you can take more risks than experimenting with
  your only computer.

- [The Linux Command Line](http://linuxcommand.org/tlcl.php) By William Shotts
  and published by No Starch Press is an excellent book to learn some of the
  basics about the command line. You can also download the PDF free from
  [his page](http://sourceforge.net/projects/linuxcommand/files/TLCL/17.10/TLCL-17.10.pdf/download).

- Self reference - All commands have built in help.

```
cat -h
cat --help
man cat
```

- [Explainshell](http://explainshell.com/) pulls relevant man page information
  for commands that are entered.
- [The Arch wiki](https://wiki.archlinux.org/) contains a large amount of
  quality information about GNU/Linux. Arch is an operating system, but the
  information is very useful for all GNU/Linux distributions.
- [cmdchallenge](https://cmdchallenge.com/) has tricky problems that can be
  solved with UNIX one-liners (web based).
- [vim adventures](https://vim-adventures.com/) teaches vim like an old school
  rpg. vim is a command line text editor like nano, but FAR more powerful and
  customizable.
- [Article: GNU/Linux command line wizardry: Learn to think in sed, awk, and grep](https://arstechnica.com/gadgets/2021/08/linux-bsd-command-line-101-using-awk-sed-and-grep-in-the-terminal/)
- Stay up-to-date with changes by subscribing to relevant news sources such as:
  - [LWN.net](https://lwn.net/)
  - [Linux Today](https://www.linuxtoday.com/)
  - [Linux Insider](https://www.linuxinsider.com/)
  - [LXer](http://lxer.com)
  - [News from the Free Software Foundation](https://www.fsf.org/news)
  - [Electronic Freedom Foundation](https://www.eff.org/)
  - Subreddits
    - [/r/linux](https://old.reddit.com/r/linux/)
    - [/r/linux4noobs](https://old.reddit.com/r/linux4noobs/)
    - [/r/linuxquestions](https://old.reddit.com/r/linuxquestions/)
    - [/r/linuxupskillchallenge](https://old.reddit.com/r/linuxupskillchallenge/)
  - Magazines
    - [Linux Format](https://www.linuxformat.com/)
    - [Linux Magazine](http://www.linux-magazine.com/)
    - [Linux Journal](https://www.linuxjournal.com/)
    - Raspberry Pi's [MagPi](https://www.raspberrypi.org/magpi/)

## Suggested Distributions

- [Debian](https://www.debian.org/) - Community driven, stable OS with only
  libre software by default. Avoid the nonfree repo if you can.
- [Ubuntu Studio](https://ubuntustudio.org/) - Targeted towards those interested
  in graphic design and audio/video production activities.
- [Trisquel](https://trisquel.info/) - Based on Ubuntu, but with all non-free
  software removed.
- [Arch](https://www.archlinux.org/) - Bleeding edge community driven distro
  based on minimalism and simplicity.
- [Parabola](https://www.parabola.nu/) - Arch Linux with non-free software
  removed.
- [Ubuntu Server](https://www.ubuntu.com/download/server) - Ubuntu without a
  graphical user interface (GUI) is a popular choice for enterprise servers.
- [AlmaLinux](https://almalinux.org/) - Stable community driven branch of Red
  Hat Enterprise Linux (RHEL). I would only recommend AlmaLinux if you are
  trying to prepare for a job that will be using RHEL.

## Proprietary NVIDIA drivers

See my [NVIDIA](https://github.com/TechnologyClassroom/nvidia) repository for
bash scripts to help make installing proprietary NVIDIA drivers and CUDA.

Note: If privacy is a concern of yours do not use the proprietary NVIDIA
drivers as they contain telemetry that cannot be turned off. Instead use the
nouveau driver if you must use NVIDIA hardware.

## Stress testing CPU on debian based systems

<http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature>

<http://www.tecmint.com/linux-cpu-load-stress-test-with-stress-ng-tool/>

    apt update && apt install -y lm-sensors stress

If `lm-sensors` and `stress` are not found, you may need to add the `universe`
repository to the `/etc/apt/sources.list` file.

    sensors && uptime && stress --cpu 8 -v --timeout 30s && uptime && sensors

See my [HardwareTest](https://github.com/TechnologyClassroom/HardwareTest)
repository for more thorough, comprehensive tests.

## UEFI Install resources

<http://ubuntuforums.org/showthread.php?t=2147295>

## Samba Network Shares

If you want to share files between Windows and GNU/Linux, you can use samba.

    sudo apt install -y samba samba-client

Modify the configuration file.

    sudo nano /etc/samba/smb.conf

Add the details for your share at the bottom of the page. Here is an example
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

    sudo /etc/init.d/samba restart

## Useful commands

Upgrade pip.

    sudo pip3 install -U pip

Seach within files for a string and list the filenames with matches.

    grep string -l *

Search for a string within files recursively.

    grep -R string .

Install tldr offline examples.

```
sudo npm install -g tldr
tldr --update
tldr tar
```

[tldr source](https://github.com/tldr-pages/tldr)

Access common examples from command line without installing additional packages.

    curl cheat.sh/tar

Replace tar with the program name.

[cheat.sh source](https://github.com/chubin/cheat.sh)

List cronjobs.

    crontab -l

Edit cron jobs as root.

    sudo crontab -e

Edit cron jobs as another users.

    sudo crontab -u username -e

## Mount a drive neatly in /media/ from the command line like the GUI file managers

List the drives.

    lsblk

    ls -la /dev/disk/by-path

Mount the device with the `udiskctl mount` command.

    udisksctl mount -b /dev/sdb1

If the disk is encrypted, decrypt first with `udiskctl unlock` command and replace sdb1 with the drive identifier.

    udisksctl unlock -b /dev/sdb1

If successful, the command will return a dm device. Proceed to use `udiskctl mount` command on the dm devices that the command gives you.

    udisksctl mount -b /dev/dm-4

To unmount, do the opposite with `udiskctl unmount` command.

    udisksctl unmount -b /dev/dm-4

If the disk was encrypted, you can lock it again with `udiskctl lock` command.

    udisksctl lock -b /dev/sdb1

## Add drive to fstab manually

I often found myself trying to set a drive to automatically boot on a system.

List the drives by uuid.

    ls -la /dev/disk/by-uuid/

Find the one you want and complete the ls entry using tab completion.

    ls -la /dev/disk/by-uuid/926c2f9e-239d-4f4b-8bfd-f937f0de253f

As root, remove the first part and replace it with echo and append it to the
/etc/fstab file.

    echo 926c2f9e-239d-4f4b-8bfd-f937f0de253f >> /etc/fstab

Edit /etc/fstab as root.

    nano /etc/fstab

Modify the line to look like this.

    UUID=926c2f9e-239d-4f4b-8bfd-f937f0de253f /mnt/desiredtmountpoint      ext4    defaults        0       2

Change desired mountpoint to that of your chosing. CTRL+X, y, enter

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

## openSUSE Tumbleweed notes

Look for a package.

    cnf man

Install package.

    sudo zypper install -y -l man

Update packages.

    sudo zypper update -y -l

Update distribution packages

    sudo zypper dist-upgrade -y -l

# Exit QEMU control capture

```
CTRL+ALT+2
quit
```

## Troubleshooting

### USB Boot problems

Problem: fat32 and fat16 formatted flash drive gives errors and has trouble
booting.

Solution: Use GNU/Linux command line tools to inspect and repair problems.

This command checked the fat32 partition for errors. If errors are found, fix
them automatically. /dev/sdc is my flash drive in this example.

    sudo dosfsck -w -r -l -a -v -t /dev/sdc1

dosfsck complained about a dirty bit and could not automatically repair. This
command can fix a dirty bit:

    sudo fsck.vfat /dev/sdc1

My response was 2 to restore backup.

My response was 1 and y to remove dirty bit.

Sources:
- <http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system>
- <https://bbs.archlinux.org/viewtopic.php?id=164185>

### Node.js path problem

Problem: nodejs cannot find the correct path. Gives error:

    /usr/bin/env: node: No such file or directory

Solution: Improperly named nodejs needs to be linked to node. Create symlink
with:

    sudo ln -s /usr/bin/nodejs /usr/bin/node

From digitalmediums at https://github.com/nodejs/node-v0.x-archive/issues/3911

### Password is too short notification

Problem: Password is too short.
Solution: Allow passwords of any length

Note: Only use this for standard account and when security does not matter.

http://ubuntuhandbook.org/index.php/2015/06/minimum-password-length-ubuntu/

    sudo nano /etc/pam.d/common-password

Remove the word 'obscure' and save.

### Dash default problem

Problem: Ubuntu defaults to dash instead of bash. Bash scripts sometimes do not
work.

Solution: Remove links to dash and repace link to bash.

```
sudo rm /bin/sh # Remove symlink to dash
sudo ln -s /bin/bash /bin/sh # Symlink bash to sh
exec bash # Restart shell
```

Links for directories work the same way.

    sudo ln -s /data/software/drivers/linux /usr/share/nginx/html/

Restart network stack with Ubuntu 16.04 server
sudo systemctl restart NetworkManager.service

### libappstream3 problem

Problem: Ubuntu 16.04 crashes on apt-get update.
Solution: Something changed in Ubuntu 16.04 during the Summer of 2017 and
libappstream3 breaks updates. Remove libappstream3 to fix the problem.

    sudo apt-get purge -y libappstream3

### Hidden grub problem

Problem: Ubuntu skips grub menu

Solution: During boot, hold Shift to access a hidden grub menu.

If that does not work, edit the /etc/default/grub file.

    sudo nano /etc/default/grub

Add a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0. CTRL+X, y, enter
to save.

Update grub.

    sudo update-grub

Modified from Eric Carvalho & Vojtech Trefny at
http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time

### Old DHCP problem

Problem: Ubuntu 16.04 does not manage the network devices. dhcp can be set
manually.

Solution: Edit config file and set managed equal to true.

    sudo nano /etc/NetworkManager/NetworkManager.conf

Change ```managed=false``` to ```managed=true```. CTRL+X, y, enter

### Old Sugar cursor problem

Problem: Ubuntu's outdated Sugar DE clobbers the cursor outside of sugar

Solution: Reset cursor theme

    gsettings reset org.gnome.desktop.interface cursor-theme

### No sound issue

Problem: No audio output and command line only.

Solution: Use amixer to toggle your output.

```
amixer # Lists all outputs
amixer sset Headphone toggle
```

### Ruby gem issue

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

### Old NIC issue

Problem: All ethernet devices are not shown in ifconfig on Ubuntu Server 16.04.

Solution: List all cards and manually add them to /etc/network/interfaces

Lists all network ports. Network ports are something like eth0, em1, p4n1,
enp3s0, and wlan0.

    ip link show

Edit the /etc/network/interfaces file.

    sudo nano /etc/network/interfaces

Use the template shown with lo for all of your network ports. CTRL+X, y, enter

### International keyboad issue

Problem: Keyboard incorrectly set to international and your minimal install does
not have the GUI tools to fix this problem

Solution: Change default keyboard settings in /etc/default/keyboard

    sudo nano /etc/default/keyboard

Remove intl from XKBLAYOUT and XKBVARIANT. Hold CTRL and press X, press y, and
press the enter or return key.

### Debian CD sources issue

Problem: Debian asks for the installation CD while updating repositories.

Solution: Remove the cdrom source from the /etc/apt/sources.list file.

    sudo nano /etc/apt/sources.list

Add a # at the beginning of the line that starts with "deb cdrom" and leave
everything else. Hold CTRL and press X, press y, and press the enter or return
key.

### Incomplete install issue

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

### Default program preferences

Problem: The default program is not the preferred choice.

Solution: Change default applications.

    sudo update-alternatives --config

Use tab completion after this to list all options. I use:

```
sudo update-alternatives --config editor
sudo update-alternatives --config x-terminal-emulator
sudo update-alternatives --config x-www-browser
```

`editor` will open the default text editor. This is useful for scripting.

`xdg-open` will open a file with the default graphical utility.

### Display manager preference

Problem: How do I find which display manager I am using with systemd?

Solution: Run this command:

    cat /etc/systemd/system/display-manager.service | grep ExecStart

### Old grub issue

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

### vim clobber vi issue

Problem: Installing vim, changes vi.

Solution: Change vim to vim.tiny

    sudo update-alternatives --config vi

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

Sometimes you just want to check where the alternatives are set to and they might be 2 redirects deep. This command is useful for checking in that instance.

    ls -la $(ls -la $(which phar) | awk '{print $NF}')

### Persistent num lock settings issue

Problem: Num lock is off after reboot.

Solution: Install numlockx and insert the command into your rc.local file.

```
sudo apt-get install numlockx
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local
```

<https://help.ubuntu.com/community/NumLock>

### Locale issue

Problem: This message appears when you login to a server: `-bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)`

Solution: Run this command `locale-gen en_US.UTF-8` as root.

### LVM issue

Problem: Console reports an issue with /dev/dm-3. How do you know what /dev/dm-3 is?

Solution: /dev/dm* are device mapper entries associated with lvm partitions.

The command to reveal what /dev/dm-3 is mapped to would be this command:

    sudo dmsetup info /dev/dm-3

To list them all, use this command:

    dmsetup ls

### Connecting to the Internet with nmcli

Problem: Need to connect to WiFi using command line after initial install.

Solution: Use Network Manager's `nmcli` to connect.

     sudo nmcli device wifi connect ACCESSPOINTNAMEHERE password PASSWORDHERE

If you cannot see the output, watch network connections from router to see if it worked.

### GPG key retrieval issue

Problem: When running `gpg --recv-keys GPGFINGERPRINTHERE`, `gpg` returns `gpg: keyserver receive failed: Server indicated a failure` instead of downloading a key.

Solution: Specify a keyserver that is likely to work such as Ubuntu's SKS pool `gpg --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 GPGFINGERPRINTHERE`. You can also set this permanently by adding `keyserver hkp://keyserver.ubuntu.com` to your `~/.gnupg/gpg.conf` configuration file.

### Debian root path issue

Problem: Debian's root user is having trouble finding programs that it should have access to.

Solution: Make sure /bin/sbin is in your path.

    echo $PATH

If not, make a temporary fix.

    export PATH="/usr/sbin:$PATH"

A permanent fix is adding the above line to your `/root/.bashrc` file and reloading your terminal with the `source ~/.bashrc` command.

### Ubuntu ads issue

Problem: Ubuntu added ads when you SSH into a server or run apt. Examples: `The following security updates require Ubuntu Pro with 'esm-apps' enabled:` and `Expanded Security Maintenance for Applications is not enabled.`

Solutions:

Opt-out with this command:

    sudo pro config set apt_news=false

From Gaia and Pablo Bianchi at https://askubuntu.com/a/1457810/1651935

Comment out the action lines in the apt hook.

    sudo sed -i'' -e 's/^\(\s\+\)\([^#]\)/\1# \2/' /etc/apt/apt.conf.d/20apt-esm-hook.conf

From nb52er and John Weldon at https://askubuntu.com/a/1434762/1651935

Add return statements before messages.

    sudo sed -Ezi.orig \
      -e 's/(def _output_esm_service_status.outstream, have_esm_service, service_type.:\n)/\1    return\n/' \
      -e 's/(def _output_esm_package_alert.*?\n.*?\n.:\n)/\1    return\n/' \
      /usr/lib/update-notifier/apt_check.py

Test.

    /usr/lib/update-notifier/apt_check.py --human-readable

Regenerate.

    sudo /usr/lib/update-notifier/update-motd-updates-available --force

From jwatson0 at https://askubuntu.com/a/1456185/1651935

When the ad packages ubuntu-advantage-tools and or ubunutu-pro-client-l10n have an update, this change will cause packages to be held-back wtih unattended-upgrades enabled.

    sudo apt update
    sudo apt upgrade

The installer will get hung up like this:

```
Configuration file '/etc/apt/apt.conf.d/20apt-esm-hook.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** 20apt-esm-hook.conf (Y/I/N/O/D/Z) [default=N] ?
```

You can compare the proposed change with D if you want, or just use the default N to keep it as it is.

After fixing the held-package, there will still be a notice when you log in over SSH.

```
2 updates could not be installed automatically. For more details,
see /var/log/unattended-upgrades/unattended-upgrades.log
```

This is fixed by removing the `kept-back` file.

    sudo rm /var/lib/unattended-upgrades/kept-back

### apt-file update issue

Problem: `apt-file` increases the `apt update` time considerably by downloading contents updates.

Solution: Disable the apt-file configuration.

    sudo mv /etc/apt/apt.conf.d/50apt-file.conf{,.disabled}

If you want to enable it again, use this command:

    sudo mv /etc/apt/apt.conf.d/50apt-file.conf{.disabled,}

If you want to enable it, update the contents for apt-file, and then disable it again, do this:

    sudo mv /etc/apt/apt.conf.d/50apt-file.conf{.disabled,} && sudo apt update && sudo mv /etc/apt/apt.conf.d/50apt-file.conf{,.disabled}

From Stephen Kitt at https://unix.stackexchange.com/a/495022/553861

### Disk full issue

Problem: Disk is full when I run the `df -h` command. How do you get some wiggle room?

Solution: Free up some space.

On a Debian-based system, mark journal logs as archived, remove journal logs except for 100MB, remove dependencies that are no longer needed with apt, and clear local apt cache.

    sudo journalctl --rotate && sudo journalctl --vacuum-size=100M && sudo apt autoremove && sudo apt autoclean

From cowlinator at https://askubuntu.com/a/1461683/1651935

Look for directories that take up the most space with the `ncdu` program.

    sudo apt install -y ncdu
    sudo ncdu /

Make sure you have backups or do not need the files before removing them. The `d` key can delete files and directories from within the `ncdu` program.

### Disk inodes issue

Problem: Disk is full, but `df -h` shows that I have disk space.

Solution: Lots of little files are taking up available inodes. Run `df -ih` to check free inodes. You can search your current directory for where the most inodes are being used with this command:

    sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n

From simon and the Tin Man at https://stackoverflow.com/a/9387415

### GNOME missing characters

Problem: GNOME Terminal is missing characters.

Solution: In GNOME Termianl, click on `Edit` in the menu bar. Click on the `Preferences` option. Click on the `Compatibility` tab. Beside `Encoding` select something that is not `Unicode - UTF-8` preferably in a similar locale to your own. Change it back to the `Unicode - UTF-8` option. Click on the `Close` button.

From hlidka at https://unix.stackexchange.com/a/365281/553861

### GNOME shutdown updates

Problem: GNOME tries to update packages on reboot and shutdown with a checked box to update packages. If that fails or tries to do more or less than what is intended, it may break the system.

Solution: Disable that option through polkit setting.

Create a new rule file.

    sudo vim /etc/polkit-1/rules.d/99-disable-offline-update.rules

Place this text in the file:

```
polkit.addRule(function(action, subject) {
  if ((action.id == "org.freedesktop.packagekit.trigger-offline-update")) {
    return polkit.Result.NO;
  }
});
```

Set the ownership of the file to the `root` user and the `polkitd` group.

    sudo chown root:polkitd /etc/polkit-1/rules.d/99-disable-offline-update.rules

Based on Jonathan Kamens solution at <https://askubuntu.com/a/1562050>.

### Prevent apt from updating a package

Problem: I have a system with an older NVIDIA card. If I update all of the packages, the NVIDIA drivers will break and I will not have a graphical display upon reboot.

Solution: Hold the packages with apt.

This is the format.

    sudo apt-mark hold nameofpackage

This is the literal command I used to hold all of the NVIDIA packages at version 580.105.08-1 the latest version that works with my old graphics card.

    sudo apt-mark hold nvidia-open-580.105.08:amd64=580.105.08-1 nvidia-kernel-open-dkms:amd64=580.105.08-1 firmware-nvidia-gsp:amd64=580.105.08-1 nvidia-driver:amd64=580.105.08-1 nvidia-kernel-support:amd64=580.105.08-1 nvidia-driver-libs:amd64=580.105.08-1 libnvidia-rtcore:amd64=580.105.08-1 libgles-nvidia1:amd64=580.105.08-1 libgles-nvidia2:amd64=580.105.08-1 libnvidia-vksc-core:amd64=580.105.08-1 nvidia-egl-icd:amd64=580.105.08-1 nvidia-vulkan-icd:amd64=580.105.08-1 libnvidia-eglcore:amd64=580.105.08-1 libnvidia-api1:amd64=580.105.08-1 libglx-nvidia0:amd64=580.105.08-1 libnvidia-gpucomp:amd64=580.105.08-1 libnvidia-ml1:amd64=580.105.08-1 libnvidia-glvkspirv:amd64=580.105.08-1 libnvidia-allocator1:amd64=580.105.08-1 libnvidia-cfg1:amd64=580.105.08-1 libnvidia-ngx1:amd64=580.105.08-1 nvidia-vdpau-driver:amd64=580.105.08-1 libegl-nvidia0:amd64=580.105.08-1 xserver-xorg-video-nvidia:amd64=580.105.08-1 nvidia-modprobe:amd64=580.105.08-1 libnvidia-glcore:amd64=580.105.08-1 nvidia-driver-cuda:amd64=580.105.08-1 nvidia-opencl-icd:amd64=580.105.08-1 libnvcuvid1:amd64=580.105.08-1 libnvidia-opticalflow1:amd64=580.105.08-1 libnvidia-fbc1:amd64=580.105.08-1 libnvoptix1:amd64=580.105.08-1 libnvidia-nvvm4:amd64=580.105.08-1 libnvidia-encode1:amd64=580.105.08-1 libnvidia-sandboxutils:amd64=580.105.08-1 libnvidia-nvvm704:amd64=580.105.08-1 libnvidia-present:amd64=580.105.08-1 libcuda1:amd64=580.105.08-1 libnvidia-ptxjitcompiler1:amd64=580.105.08-1 libnvidia-pkcs11-openssl3:amd64=580.105.08-1 libcudadebugger1:amd64=580.105.08-1 nvidia-persistenced:amd64=580.105.08-1 nvidia-settings:amd64=580.105.08-1 libxnvctrl0:amd64=580.105.08-1 nvidia-xconfig:amd64=580.105.08-1 libegl-nvidia0:i386=580.105.08-1 libgles-nvidia2:i386=580.105.08-1 libnvidia-allocator1:i386=580.105.08-1 libnvidia-glcore:i386=580.105.08-1 libnvidia-gpucomp:i386=580.105.08-1 nvidia-driver-libs:i386=580.105.08-1 libgles-nvidia1:i386=580.105.08-1 libglx-nvidia0:i386=580.105.08-1 libnvidia-eglcore:i386=580.105.08-1 libnvidia-glvkspirv:i386=580.105.08-1 libnvidia-ml1:i386=580.105.08-1 nvidia-vulkan-icd:i386=580.105.08-1

List held packages.

    apt-mark showhold

Accepting donations for a newer graphics card. :D

### WeeChat color issue

Problem: System and WeeChat color scheme makes it difficult to read nicks when they ping you.

Solution: Change the `weechat.color.chat_highlight` colors to very different options.

    /set weechat.color.chat_highlight black
    /set weechat.color.chat_highlight_bg green
