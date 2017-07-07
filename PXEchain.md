# [Setting up two PXE servers on the same network: WDS and GNU/Linux PXE Server](#twopxeservers)

Work in progress!

Michael McMahon

Rewrite/update based on Eric Gray's 2011 article http://www.vcritical.com/2011/06/peaceful-coexistence-wds-and-linux-pxe-servers/

There are many guides on setting up a Windows Deployment Server (WDS) and GNU/Linux PXE servers.  I will not go into the specifics of setting up a general PXE server.  Setting up a WDS server or a GNU/Linux PXE server is simple by following guides availabe online, but there are very few articles about configuring multiple PXE servers on the same network.

Scenario: My organization has a WDS server configured on our network.  We use GNU/Linux regularly and want to use a GNU/Linux PXE server.  Our options are creating a new network with new cable drops or use the prexisting network.  Using the preexisting network would be easier and cheaper.

Configure and test this entire process in a test environment before implementing this on a production environment.

Requirements:

* A working WDS server with DHCP and DNS configured.  This needs to be tested with PXE booting before starting.
* Another server to configure as a GNU/Linux PXE server.  I am using CentOS 7 Minimal.
* A third machine that can boot into PXE
* A switch
* Network cables to connect the four boxes

# Configuring the WDS server with syslinux

- <a href="https://www.kernel.org/pub/linux/utils/boot/syslinux/6.xx/syslinux-6.03.zip">Download syslinux 6.03</a> to both PXE servers and extract these files to your tftp locations C:\RemoteInstall\Boot\x64\ for WDS and /var/lib/tftpboot for CentOS 7.
/bios/com32/chain/

- Create a new folder C:\RemoteInstall\Boot\x64\pxelinux.cfg and make a new file in that folder called default.

- Change the contents of the C:\RemoteInstall\Boot\x64\pxelinux.cfg\default file.

```
DEFAULT menu.c32
MENU TITLE WDS PXE Server
PROMPT 0
TIMEOUT 100 # 10 seconds
 
LABEL wds
  MENU DEFAULT
  MENU LABEL ^Windows Deployment Services (WDS)
  KERNEL pxeboot.0
 
LABEL gnulinuxpxe
  MENU LABEL GNU/^Linux PXE Server
  KERNEL pxechn.c32
  APPEND 192.168.1.15::pxelinux.0

LABEL abort
  MENU LABEL ^Abort PXE
  Kernel abortpxe.0

LABEL local
  MENU LABEL Boot from ^Local Computer
  LOCALBOOT 0
```
The default first choice continues booting the WDS server as usual.  The second choice chains into a second PXE server.  The third choice exits PXE and boots with the next available boot option according to your boot order.  The fourth choice attempts to boot from the local disk.

```menu.c32``` can be changed to ```vesamenu.c32``` for a better look, but compatibility may decrease.

- Change 192.168.1.15 to an available IP address outside of your DHCP server's scope.  Assign your GNU/Linux PXE server a static IP that matches.


```
wdsutil /set-server /bootprogram:boot\x64\pxelinux.0 /architecture:x64
wdsutil /set-server /N12bootprogram:boot\x64\pxelinux.0 /architecture:x64
```
