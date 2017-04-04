# ESXi

Michael McMahon

ESXi (VMware vSphere Hypervisor) is a proprietary system using the vmkernel.

A client uses ESXi so I have started teaching myself.  I am not interested in this subject so I will only focus on installation and initial configuration.  If you see I have made a mistake or know of a better way of doing things, add an issue to the SetupNotes repository or send me an email.

Official documentation: https://www.vmware.com/support/vsphere-hypervisor.html

v6.5 documentation: https://www.vmware.com/support/pubs/vsphere-esxi-vcenter-server-6-pubs.html

v6.0 documentation: http://pubs.vmware.com/vsphere-60/index.jsp

Hardware Compatibility: https://www.vmware.com/resources/compatibility/search.php

Product Compatibility and Interoperability Matrixes: http://partnerweb.vmware.com/comp_guide2/sim/interop_matrix.php

Download (free account required): http://www.vmware.com/go/get-free-esxi

# Installation

The installation of ESXi to be extremely easy compared to GNU/Linux and UNIX distros.

Set the BIOS to legacy mode.

Boot from ESXi installation media.

There are two moments where you can press enter to speed up the boot process.

Loading takes a few minutes.

(Enter) Continue

(F11) Accept and Continue

Choose the drive you want to install on with the up and down arrow keys.  (Enter) Continue

Note: If you configure a fake RAID, ESXi will see all of the drives instead of the RAID.  ESXi does not allow fake RAID or software RAID.  There is not a way to have RAID 1 with SATADOM and ESXi.  Hardware RAID works fine on supported hardware.

Choose the language with the up and down arrow keys.  (Enter) Continue

Enter your password twice.  Use tab to get to the second password box.  (Enter) Continue

(F11) Install

(Enter) Reboot

# First boot

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Configure Management Network

Network Adapters

Press down, space, and repeat until all network adapters have an 'X' beside them.

Note: If all of your network adapters are not shown, reinstall with a different version of ESXi.

Press enter.  Press escape.  Press Y.  Press escape.

An IP address should be shown.  To access the web portal, open the address listed with a web browser from another computer on the network.  Example: http://555.555.555.555/ (DHCP)

<F12> Shut Down/Restart

Press tab.  Enter password.  Press enter.

<F2> Shut Down
