# Ubuntu Server

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
