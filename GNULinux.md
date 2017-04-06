# GNU/Linux

# Suggested Distributions
- Debian
https://www.debian.org/

- Ubuntu Studio for those interested in graphic design and audio/video production activities.
https://ubuntustudio.org/

- Trisquel - Ubuntu with non-free software removed
https://trisquel.info/

- Arch - Bleeding edge community driven distro based on minimalism
https://www.archlinux.org/

- Parabola - Arch Linux with non-free software removed
https://www.parabola.nu/

- Fedora - Bleeding edge community driven branch of Red Hat Enterprise Linux
https://getfedora.org/

- CentOS - Stable community driven branch of Red Hat Enterprise Linux
https://www.centos.org/

# Arch Wiki
This link contains lots of information about GNU/Linux.  Some of the wiki is specific to Arch Linux, but the wiki is very useful for all GNU/Linux distributions.
https://wiki.archlinux.org/

# UEFI Install resources
http://ubuntuforums.org/showthread.php?t=2147295

# Allow passwords of any length (Only use this for standard account)
http://ubuntuhandbook.org/index.php/2015/06/minimum-password-length-ubuntu/
sudo nano /etc/pam.d/common-password
# Remove the word 'obscure' and save.

# Problem: Ubuntu defaults to dash instead of bash.  Bash scripts sometimes do not work.
# Solution: Remove links to dash and repace link to bash.
sudo rm /bin/sh # Remove symlink to dash
sudo ln -s /bin/bash /bin/sh # Symlink bash to sh
exec bash # Restart shell

# Links for directories work the same way.
sudo ln -s /data/software/drivers/linux /usr/share/nginx/html/

# Problem: Ubuntu skips grub menu
# Solution: During boot, hold Shift to access a hidden grub menu.
# If that does not work, edit the /etc/default/grub file.
sudo nano /etc/default/grub
#Add a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0.  CTRL+X, y, enter to save.
sudo update-grub
# Modified from Eric Carvalho & Vojtech Trefny at http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time

# Problem: Ubuntu's outdated Sugar DE clobbers the cursor outside of sugar
# Solution: Reset cursor theme
gsettings reset org.gnome.desktop.interface cursor-theme

# Problem: No audio output and command line only.
# Solution: Use amixer to toggle your output.
amixer # Lists all outputs
amixer sset Headphone toggle

# Problem: All ethernet devices are not shown in ifconfig.
# Solution: List all cards and manually add them to /etc/network/interfaces
ip link show # Lists all network ports.  Network ports are something like eth0, em1, p4n1, enp3s0, and wlan0.
nano /etc/network/interfaces # Requires root.  Use the template shown with lo for all of your network ports.

# Problem: Keyboard incorrectly set to international and your minimal install does not have the GUI tools to fix this problem
# Solution: Change default keyboard settings in /etc/default/keyboard
sudo nano /etc/default/keyboard
# Remove intl from XKBLAYOUT and XKBVARIANT.  Hold CTRL and press X, press y, and press the enter or return key.

# Problem: Debian asks for the installation CD while updating repositories.
# Solution: Remove the cdrom source from the /etc/apt/sources.list file.
sudo nano /etc/apt/sources.list
# Add a # at the beginning of the line that starts with "deb cdrom" and leave everything else.  Hold CTRL and press X, press y, and press the enter or return key.

# Samba Network Shares
# If you want to share files between Windows and GNU/Linux, you should use samba.
sudo apt-get install samba samba-client
# Modify the configuration file
sudo nano /etc/samba/smb.conf
# Add the details for your share at the bottom of the page.  Here is an example that worked as a public folder:
[TestShare]
path = /home/noob/test # Folder directory
public = yes
force user = noob # Replace noob with the username of the owner of the folder.
guest ok = yes
writable = yes
read only = no
create mask = 0755
# Restart samba for changes to take effect.
sudo /etc/init.d/samba restart

# Install greg podcatcher
sudo pip3 install --user greg

# Upgrade pip
sudo pip install --upgrade pip
sudo pip3 install --upgrade pip

# Seach within files for a string and list the filenames with matches
grep string -l *


# Proprietary NVIDIA drivers
Download without a gui
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/NVIDIA-Linux-x86_64-375.26.run
wget https://developer.nvidia.com/compute/cuda/8.0/prod/local_installers/cuda_8.0.44_linux-run

# To uninstall use the --uninstall switch
./NVIDIA-Linux-x86_64-375.26.run --uninstall


# Stress testing debian based systems

http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature
http://www.tecmint.com/linux-cpu-load-stress-test-with-stress-ng-tool/

apt update && apt install lm-sensors stress stress-ng
# If lm-sensors and stress are not found, add universe to the /etc/apt/sources.list file.

sensors && uptime && stress --cpu 8 -v --timeout 30s && uptime && sensors


# Add drive to fstab manually

I often find myself trying to set a drive to automatically boot on a system.

# List the drives by uuid:
ls -la /dev/disk/by-uuid/

# Find the one you want and complete the ls entry using tab completion

ls -la /dev/disk/by-uuid/926c2f9e-239d-4f4b-8bfd-f937f0de253f

# As root, remove the first part and replace it with echo and append it to the /etc/fstab file.

echo 926c2f9e-239d-4f4b-8bfd-f937f0de253f >> /etc/fstab

# Edit /etc/fstab:

nano /etc/fstab

# Modify the line to look like this:
UUID=926c2f9e-239d-4f4b-8bfd-f937f0de253f /mnt/desiredtmountpoint      ext4    defaults        0       2

# Change desired mountpoint to that of your chosing.


# opensuse tumbleweed notes
# Look for a package
cnf man
# Install package
sudo zypper install -y -l man
# Update packages
sudo zypper update -y -l
# Update distribution packages
sudo zypper dist-upgrade -y -l

# Exit QEMU
CTRL+ALT+2
quit
