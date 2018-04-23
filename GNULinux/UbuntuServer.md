# Ubuntu Server

[Ubuntu Server webpage](https://www.ubuntu.com/download/server)

Ubuntu Server is Ubuntu without a Graphic User Interface (GUI).  This leaves
your server with only a Command Line Interface (CLI).  Ubuntu Server or Ubuntu
Minimal are a good choice when a system will have no monitor connected to it or
when performance is preferred to UI.

## Standard Ubuntu 16.04 Server Install

This is a standard legacy install with a drive smaller than 2 TB.

- Boot from disc or network.
- Press enter five times to set the language and keyboard configuration
  (English, United States, No, English (US), English (US))
- Select the Network Interface to use with the arrow keys and press enter.  I
  selected ```eno1``` in my example.
- Set the hostname.  I chose the default ```ubuntu```.  Continue.
- Choose the network mirror.  I chose ```United States```.
- Confirm network mirror.  I chose ```us.archive.ubuntu.com```.
- Choose proxy information.  I leave this blank for none.  Continue.
- Enter the full name of a new user.  When setting up a system for a client, I
  choose ```Default User```.
- Enter a username for the new user with all lowercase letters.  When setting up
  a system for a client, I choose ```user```.
- Enter a password.  When setting up a system for a client, I choose
  ```password```.
- Enter the password again.
- Decide if you would like to encrypt your home directory.  When setting up a
  system for a client, I choose ```No```.
- NTP will be set based on your location.  Verify it is correct with ```Yes```.
- Choose a partitioning method.  For this example, I will choose a standard
  configuration using ```Manual```.
- Choose the device for the OS.  In my example, I will use ```/dev/sda```.
  - Create a new empty partition table on this device? Yes
  - Select FREE SPACE under sda.
    - Create a new partition
    - New partition size: ```500 MB```
    - Primary
    - Beginning
    - Use as: Ext2 file system
    - Mount point: /boot
    - Done setting up the partition
  - Select FREE SPACE under sda
    - Create a new partition
    - New partition size: ```20 GB```
    - Primary
    - Beginning
    - Use as: Ext4 file system
    - Mount point: /
    - Done setting up the partition
  - Select FREE SPACE under sda
    - Create a new partition
    - New partition size: ```8 GB```
    - Primary
    - Beginning
    - Use as: swap area
    - Done setting up the partition
  - Select FREE SPACE under sda
    - Create a new partition
    - Press enter to select all of the remaining space on the drive.
    - Primary
    - Use as: Ext4 file system
    - Mount point: /home
    - Done setting up the partition
  - If you have more disks, you can partition them as Ext4 as well with custom
    mountpoints.
  - Finish partitioning and write changes to disk
- Write the changes to disks? ```Yes```
- Wait for the base system to install.  This will take a moment.
- How do you want to manage upgrade on this system? ```No automatic updates```
- Choose software to install: This menu gives you the option to install
  metapackages.  Use tab enter to skip installing extra packages.
  - The ```tasksel``` command will give you this menu on any Debian based system
    if would like to make a change to a workstation.
- Install the GRUB boot loader to the master boot record? ```Yes```
- Installation complete.  Press enter for ```Continue```.
- The system will reboot into your system.

## Ubuntu 16.04 Server with Nvidia video output with a disk smaller than 2TB

- Boot from disc
- English
- (F6) Expert mode (Enter) (Esc)
- Change "vga=788" to "vga=794"
- Choose language
- Configure keyboard
- Detect and mount CD-ROM
- Load debconf preconfiguration file
- Load installer components from CD
  - choose-mirror
  - load-media
- Detect network hardware
- Configure the network
- Choose a mirror of the Ubuntu archive
- Set up users and passwords
- Configure the clock
- Detect disks
- Partition disks
  - Manual
  - msdos
- Install the system
  - normal
- Configure the package manager
  - restricted yes
  - universe yes
  - multiverse no
  - backports no
  - source no
- Select and install software
- Install the GRUB boot loader to a hard disk
  - Force UEFI no
- Finish the installation
  - UTC no

## System configuration

- Update software.

```
sudo apt update && sudo apt upgrade -y && sudo apt-get dist-upgrade -y && sudo apt install -y ledmon build-essential
```

- Add network interfaces to ifconfig.

```
tmux
```

Split the screen with CTRL+b %.

```
ip a
```

Switch the the screen to the left with CTRL+b left arrow.

```
sudo nano /etc/network/interfaces
```

Do not change lo.

Change the default NIC from auto to allow-hotplug.

Add each missing interface from ip a with allow-hotplug instead of auto.

Reboot.

```reboot```

List all configured NICs.

```ifconfig```

Test each NIC by pinging out.

```ping www.google.com```

CTRL+C stops the ping.  Remove the ethernet plug from the NIC.  Release the DHCP
lease with ```sudo ifdown eno1```.  Move the plug to the next NIC, wait a
moment, ping out, and repeat this process until all NICs have been tested.

## Properly add nomodeset to boot.

```
sudo sed -i 's/T=""/T="nomodeset"/' /etc/default/grub
sudo update-grub
reboot
```

## Install Proprietary NVIDIA drivers and cuda

Change to runlevel 3.

```sudo init 3```

See my [nvidia repository](https://github.com/TechnologyClassroom/nvidia) for
bash scripts to complete the installation.

## Remove history

```
exit
# Log back in
sudo su
rm -f /root/.bash_history
history -c
exit
exit
# Log back in
rm .bash_history
history -c
```

## [Ubuntu 17.10 Server networking](https://github.com/TechnologyClassroom/SetupNotes/blob/master/GNULinux/UbuntuServer.md#ubuntu-1710-server-networking)

The workflow for Ubuntu Server networking has changed on 17.10 because it now
uses netplan.  Instead of changing the /etc/network/interfaces file, we change
the /etc/netplan/01-netcfg.yaml file.

List all NICs.

```ip a```

Edit the netplan configuration file.

```sudo nano /etc/netplan/01-netcfg.yaml```

Cut the last two lines and paste them to match the number of network interface
cards (NICs).

Here is an example /etc/netplan/01-netcfg.yaml with two NICs:

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: yes
    eno2:
      dhcp4: yes
```

Save with CTRL+X, y, enter, and enter.

Apply the configuration.

```sudo netplan apply```

Reboot.

```reboot```

List all configured NICs.

```ifconfig```

Test each NIC by pinging out.

```ping www.google.com```

CTRL+C stops the ping.  Move the plug to the next NIC, wait a moment, ping out,
and repeat this process until all NICs have been tested.

Links:

- https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/
- https://wiki.ubuntu.com/Netplan
- https://helpmanual.io/man5/netplan/
- https://askubuntu.com/questions/972955/ubuntu-17-10-server-static-ip-netplan-how-to-set-netmask
- https://insights.ubuntu.com/2017/07/10/netplan-by-default-in-17-10/

## Troubleshooting

Problem: Ubuntu 12.04 Server cannot update.

Solution: Remove the contents of /var/lib/apt/lists/ with this command:

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

From Lorem at https://askubuntu.com/questions/41605


Problem: After installation, only one network device is shown under ifconfig.
Only the device used during install is configured under /etc/network/interfaces
and all others are missing.  All other devices are displayed with the ```ip a```
or ```ipconfig -a``` commands.

Solution: Edit the /etc/network/interfaces file.  Copy the two lines for the
configured device or lo and paste them below.  Change the device name to match
the entries from ifconfig -a or ip a.  Change auto to allow-hotplug for all new
entries.

Example:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

allow-hotplug eth1
iface eth1 inet dhcp

allow-hotplug eth2
iface eth2 inet dhcp
```
