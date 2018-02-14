# Ubuntu Server

[Ubuntu Server webpage](https://www.ubuntu.com/download/server)

Ubuntu Server is Ubuntu without a Graphic User Interface (GUI).  This leaves your server with only a Command Line Interface (CLI).  Ubuntu Server or Ubuntu Minimal are a good choice when a system will have no monitor connected to it or when performance is preferred to UI.

# Ubuntu 16.04 Server with Nvidia graphics card video output with a disk that is smaller than 2TB

* Boot from disc

* English

* (F6) Expert mode (Enter) (Esc)

* Change "vga=788" to "vga=794"

* Choose language

* Configure keyboard

* Detect and mount CD-ROM

* Load debconf preconfiguration file

* Load installer components from CD

  * choose-mirror

  * load-media

* Detect network hardware

* Configure the network

* Choose a mirror of the Ubuntu archive

* Set up users and passwords

* Configure the clock

* Detect disks

* Partition disks

  * Manual

  * msdos

* Install the system

  * normal

* Configure the package manager

  * restricted yes

  * universe yes

  * multiverse no

  * backports no

  * source no

* Select and install software

* Install the GRUB boot loader to a hard disk
	
  * Force UEFI no

* Finish the installation
	
  * UTC no



* Boot into recovery mode

* resume

* Update software
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get install -y ledmon build-essential
```
* Properly add nomodeset to boot

```
sudo sed -i 's/T=""/T="nomodeset"/' /etc/default/grub
sudo update-grub
reboot
```

* Add network interfaces to ifconfig
```
ip a
sudo nano /etc/network/interfaces
```
* Do not change lo.

Add each missing interface from ip a with allow-hotplug instead of auto.

Change the default NIC from auto to allow-hotplug.

* Install proprietary nvidia drivers and cuda toolkit
```
# THIS IS PORTION IS OUT OF DATE
sudo su
init 3
wget -q http://us.download.nvidia.com/XFree86/Linux-x86_64/375.66/NVIDIA-Linux-x86_64-375.66.run
wget -q https://developer.nvidia.com/compute/cuda/8.0/prod2/local_installers/cuda_8.0.61_375.26_linux-run
sh NVIDIA-Linux-x86_64-375.66.run --accept-license -q -X
sh cuda_8.0.61_375.26_linux-run --toolkit -silent --override
echo export 'PATH=/usr/local/cuda/bin:$PATH' >> /etc/bashrc
echo /usr/local/cuda/lib64 >> /etc/ld.so.conf
echo /usr/local/cuda/lib >> /etc/ld.so.conf
echo blacklist nouveau >> /etc/modprobe.d/blacklist.conf
ldconfig
```
* Remove history
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

* Login
```
rm .bash_history
history -c
```

# Problems

Problem: Ubuntu 12.04 Server cannot update.

Solution: Remove the contents of /var/lib/apt/lists/ with this command:

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

From Lorem at https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error


Problem: After installation, only one network device is shown under ifconfig.  Only the device used during install is configured under /etc/network/interfaces and all others are missing.  All other devices are displayed with the ip a or ipconfig -a commands.

Solution: Edit the /etc/network/interfaces file.  Copy the two lines for the configured device or lo and paste them below.  Change the device name to match the entries from ifconfig -a or ip a.  Change auto to allow-hotplug for all new entries.

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
