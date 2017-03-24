# FreeNAS

WARNING: FreeNAS is for advanced users only.  If you are not very comfortable with UNIX-like command line usage, I would suggest using Debian, Ubuntu, CentOS, or Arch instead of FreeNAS.

FreeNAS is a UNIX distro built for network storage solutions that you can install for free.

A client uses FreeNAS so I have started teaching myself.  These are notes as I am learning.  Much of my GNU/Linux knowledge carries over, but there are plenty of differences.  If you see I have made a mistake or know of a better way of doing things, add an issue to the SetupNotes repository or send me an email.

Official documentation: http://doc.freenas.org/

Download: http://www.freenas.org/download-freenas-release/

# Installation

I found the installation of FreeNAS to be extremely easy compared to other GNU/Linux and UNIX distros.

Set the BIOS to legacy mode.

Boot from FreeNAS installation media.

FreeNAS Installer

1 Install/Upgrade

Choose the drive you want to install on with the up and down arrow keys and select your choice with the space bar.  Press enter to continue.

Yes

Boot with BIOS

Enter your password twice.  Use tab to get to the second password box.  Press enter to continue.

OK

3 Reboot System

Yes, that is really how simple the installation is.  Installation media can be removed.

# First boot

The first boot takes a long time as it generates random numbers.  If you miss the first prompt informing you of this, it may appear broken.

If all goes well, it will display an IP address.  If no IP address is shown, go to Troubleshooting networking.

Using another computer on the network, open a browser to the IP address shown in FreeNAS.

My answers were:

Language: English
Console Keyboard Map:	United States of America ISO-8859-1
Timezone: America/New_York
Next

Pool Name: data
Automatic
Next

Exit?

System > General > Updates
Check Now
Update

# Troubleshooting networking

If the IP does not display use 9 Shell to acquire an IP address with the dhclient command.

List your network interfaces:

ifconfig

Use dhclient to assign yourself an IP (My NIC is ix0 in this example):

dhclient ix0
