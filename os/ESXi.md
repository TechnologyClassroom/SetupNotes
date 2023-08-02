# ESXi

Michael McMahon

IMPORTANT NOTE: Use [Proxmox](https://www.proxmox.com/en/) instead of ESXi.

Reasons to use Proxmox instead of ESXi:

* Proxmox is based on the community-run Debian distribution.
* Proxmox seems to generally do things the correct way.
* Hardware compatibility is better with Proxmox.
* Proxmox can optionally use Ceph storage.
* No account is required to download and use Proxmox.
* There is no downside. Use Proxmox instead of ESXi.

Reasons to use ESXi instead of Proxmox:

* Your work refuses to use anything other than ESXi.

ESXi (VMware vSphere Hypervisor) uses the proprietary vmkernel.

Some of my former clients used ESXi so I had started teaching myself. I am not
interested in this subject so Ionly focus on installation and initial
configuration because of VMware's proprietary nature and 
[this](https://sfconservancy.org/copyleft-compliance/vmware-lawsuit-faq.html), 
[this](http://www.zdnet.com/article/vmware-sued-for-failure-to-comply-with-linuxs-license/),
and
[this](https://opensource.com/law/16/8/gpl-enforcement-action-hellwig-v-vmware).
If you see I have made a mistake or know of a better way of doing things, add an
issue to the SetupNotes repository or send me an email.

[Official documentation](https://www.vmware.com/support/vsphere-hypervisor.html)

[v6.5 documentation](https://www.vmware.com/support/pubs/vsphere-esxi-vcenter-server-6-pubs.html)

[v6.0 documentation](http://pubs.vmware.com/vsphere-60/index.jsp)

[Hardware Compatibility](https://www.vmware.com/resources/compatibility/search.php)

[Product Compatibility and Interoperability Matrixes](http://partnerweb.vmware.com/comp_guide2/sim/interop_matrix.php)

[Download (free account required)](http://www.vmware.com/go/get-free-esxi)

Note: At the time of this writing, only the latest iso can be downloaded with a free
account. In January 2017, every available version could be downloaded with a
free account.

## Installation

The installation of ESXi is extremely easy compared to GNU/Linux and UNIX
distros.

Set the BIOS to legacy mode.

Boot from ESXi installation media.

There are two moments where you can press enter to speed up the boot process.

Loading takes a few minutes.

(Enter) Continue

(F11) Accept and Continue

Choose the drive you want to install on with the up and down arrow keys.
(Enter) Continue

Note: If you configure a fake RAID, ESXi will see all of the drives instead of
the RAID.  ESXi does not allow fake RAID or software RAID.  There is not a way
to have RAID 1 with SATADOM and ESXi.  Hardware RAID works fine on supported
hardware.

Choose the language with the up and down arrow keys.  (Enter) Continue

NOTE: As of ESXi 6.7, the password rules have changed.  All passwords require a
lowercase letter, an uppercase letter, a number, and a special character.  The
simplest default password is Password1!

Enter your password twice.  Use tab to get to the second password box.  (Enter)
Continue

(F11) Install

(Enter) Reboot

## Installing through PXE

See [my page on PXE](https://github.com/TechnologyClassroom/pxe) for my syslinux
configs.

The boot.cfg file must be modified once the extracted into the tftp.  This sed
command will remove all of the forward slashes if run from the same directory.

```
cp boot.cfg boot.cfg.bak
sed -i 's/\///g' boot.cfg
```

## Troubleshooting Installation

If the installation fails, enter a different TTY for troubleshooting.
CTRL+ALT+F1 will drop to TTY1.  User is root.  Password is blank.

List the logs.

```ls /var/log/```

View a log.  Replace nameoflog with the log you would like to inspect.

```less /var/log/nameoflog```

List NICs.

```esxcfg-nics -l```

# First boot

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Note: With ESXi 6.7, the password rules have changes and require multiple
character types.

Configure Management Network

Network Adapters

Press down, space, and repeat until all network adapters have an 'X' beside
them.

Note: If all of your network adapters are not shown, reinstall with a different
version of ESXi.

Press enter.  Press escape.  Press Y.  Press escape.

An IP address should be shown.  To access the web portal, open the address
listed with a web browser from another computer on the network.  Example:
http://555.555.555.555/ (DHCP).  Username is root.  Password is set during
installation.

<F12> Shut Down/Restart

Press tab.  Enter password.  Press enter.

<F2> Shut Down

## Updating the system manually

Based on William Lam's article:
https://www.virtuallyghetto.com/2013/06/quick-tip-listing-image-profiles-from.html

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Enable ESXi SHell

Enable SSH

On a machine with openssh-client and scp, open a browser to
https://my.vmware.com/group/vmware/patch#search.

Login or make a free account.

Change the drop down to "ESXi (Embedded and Installable)" and click on the blue
Search button.

Updates are cumulative.  Click on the blue Download button for the latest
update.

Check to see if there is an update.

Open a terminal.  Navigate to the download location.

Use scp to copy the update to the server.  Note: WinSCP can be used on Windows
instead of scp.

In this case, my server is 10.12.17.101.  My update is ESXi650-201803001.zip.

```scp ESXi650-201803001.zip root@10.12.17.101:/vmfs/volumes/datastore1```

Type yes and enter the password.

ssh into the server.  Note: PuTTY can be used on Windows instead of ssh.

```ssh root@10.12.17.101```

Change to the datastore1 directory.

```cd /vmfs/volumes/datastore1```

List the available updates.

```esxcli software sources profile list -d /vmfs/volumes/datastore1/ESXi650-201803001.zip```

Install the version of the update that you want to install.

```esxcli software profile update -d /vmfs/volumes/datastore1/ESXi650-201803001.zip -p $(esxcli software sources profile list -d /vmfs/volumes/datastore1/ESXi650-201803001.zip | awk '{ print $1 }' | tail -n 1)```

Note: The above command will only work if it is run from the shell of the ESXi
machine.  If the ```$(...)``` portion of the script is run from another machine,
the esxcli command will not be understood and the update will not continue.

Remove the update.

```rm ESXi650-201803001.zip```

Reboot the system.

```reboot```

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Disable ESXi SHell

Disable SSH

## Updating the system with a script

Based on William Lam's article:
https://www.virtuallyghetto.com/2013/06/quick-tip-listing-image-profiles-from.html

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Enable SSH

On a machine with openssh-client and scp, open a browser to
https://my.vmware.com/group/vmware/patch#search.

Login or make a free account.

Change the drop down to "ESXi (Embedded and Installable)" and click on the blue
Search button.

Updates are cumulative.  Click on the blue Download button for the latest
update.

Open a terminal.  Navigate to the download location.

Create these scripts and modify the variables for the update.

```
# pushupdates.sh
# Michael McMahon
# Installs ESXi650-201710001.zip to selected server

# Usage: sh pushupdate.sh 10.12.17.71
#   where 10.12.17.71 is the local IP address of the ESXi server.

# Depends on openssh-client, scp, and sshpass.
# Must be run from a directory with the update file.
# Must be run on the same subnet.
# The ESXi machine must have SSH enabled.

update=ESXi650-201803001
password=Password1!

sshpass -p $password scp \
-oUserKnownHostsFile=/dev/null \
-oStrictHostKeyChecking=no \
$update.zip root@$1:/vmfs/volumes/datastore1

sshpass -p $password scp \
-oUserKnownHostsFile=/dev/null \
-oStrictHostKeyChecking=no \
update.sh root@$1:/vmfs/volumes/datastore1

# This segment of python code could parse the same result as updatepackage:
# print(update[0:4] + "-" + update[4:5] + "." + update[5:6] + "." + update[6:])
sshpass -p $password ssh \
-oUserKnownHostsFile=/dev/null \
-oStrictHostKeyChecking=no root@$1 \
sh /vmfs/volumes/datastore1/update.sh
```

```
# update.sh
# Michael McMahon
# Installs ESXi650-201710001.zip to selected server

# Usage: sh update.sh

# Must be run on the ESXi shell.
# Must be run from a directory with the update file.

update=ESXi650-201803001

esxcli software profile update -d /vmfs/volumes/datastore1/$update.zip -p $(esxcli software sources profile list -d /vmfs/volumes/datastore1/$update.zip | awk '{ print $1 }' | tail -n 1)

rm /vmfs/volumes/datastore1/$update.zip

reboot
```

Install sshpass and openssh-client, if you do not have them on your system.

Run the script.

```
sh pushupdates.sh 192.168.1.67
```

Replace ```192.168.1.67``` with the IP address of the ESXi machine.

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Disable SSH

## RAID Notes

ESXi cannot do fake RAID or software RAID.  If you need to install ESXi to a
RAID, you must use a hardware RAID controller such as 3108.

## Installing Broadcom LSI Drivers (Manually)

- Download the LSI drivers.

Unlike LSI drivers for all other operating systems, LSI drivers must be
downloaded from the vmware page.  A free login is required.  Here is a search
link to start your search:

https://my.vmware.com/group/vmware/searchresults#site=my_download&client=my_download&getfields=*&output=xml_no_dtd&filter=0&proxyreload=1&proxystylesheet=my_download_en&sort=date:D:S:d1&num=10&entqr=3&q=SAS+Driver+for+Avago+MegaRAID&dscaf=__&requiredfields=dsca_lang:en&ie=UTF-8&ulang=en&ip=198.0.155.97&access=p&entqrm=0&wc=200&wc_mc=1&oe=UTF-8&ud=1&start=10

- Once you have the package for your version, extract the vib file from the
archive onto your local machine.

- On the ESXi machine, enable SSH.

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Enable SSH

- Copy the vib file to your machine with scp or winscp.

```
scp vmware-esx-provider-lsiprovider.vib root@10.12.17.108:/vmfs/volumes/datastore1/
```

In this case, my ESXi server is located at 10.12.17.108.

- Login to the server with ssh or PuTTY.

```
ssh root@10.12.17.108
```

- Install the vib file.

```
esxcli software vib install -v /vmfs/volumes/datastore1/vmware-esx-provider-lsiprovider.vib
```

- Remove the vib file.

```
rm /vmfs/volumes/datastore1/vmware-esx-provider-lsiprovider.vib
```

- Disable SSH from ESXi.

<F2> Customize System/View Logs

Press tab.  Enter password.  Press enter.

Troubleshooting Options

Disable ESXi SHell

Disable SSH

- Reboot the server.

## Hardware Notes

Intel Ethernet Converged Network Adapter X710-DA4 does not work with v6.0 U2 and
does work with v6.5.

## Installing VMware vSphere Perl SDK on Ubuntu

https://code.vmware.com/web/sdk/67/vsphere-perl

The site says, "The vSphere Perl SDK targets the development of Perl
applications that access the vSphere platform. The SDK exposes the vSphere Perl
APIs that are created as a Perl binding for the vSphere Web Services APIs."

- Make an account and download the sdk using the above link.

I downloaded VMware-vSphere-Perl-SDK-6.7.0-8156551.x86_64.tar.gz and there might
be a new version.

- Extract the file.

```
tar zxvf VMware-vSphere-Perl-SDK-6.7.0-8156551.x86_64.tar.gz
```

- Change directories.

```
cd vmware-vsphere-cli-distrib
```

- Install dependencies.

```
sudo apt update
sudo apt-get install -y libxml2-dev
```

- Run the installer.

```
sudo ./vmware-install.pl
```

Press enter, q, yes, yes to get through the menu.  This can be automated with
heredocs in a bash script.

## Find the moid of your VM

- Install the Perl SDK from the previous section.

- Download the VirtuallyGhetto scripts.

[VirtuallyGhetto](https://www.virtuallyghetto.com/) is William Lam's blog about
VMware, ESXi, and cloud automation.

```
git clone https://github.com/lamw/vghetto-scripts
```

- Change directory.

```
cd vghetto-scripts/perl
```

- Run the script.

```
./moRefFinder.pl --name VM-NAME-HERE --type vm --server ESXI-SERVER-IP-ADDRESS-HERE --username root --password ESXI-SERVER-PASSWORD-HERE
```

- The output should tell you the moid.

```
EntityName: VM-NAME-HERE         MoRefID: 2
```

## Login to VM with vmrc

- Find the moid using the previous two sections.

- Download vmrc.

https://www.vmware.com/go/download-vmrc

I used VMware-Remote-Console-10.0.3-9300449.x86_64.bundle at the time of this
writing.  The file is a plaintext bash script.

- Install vmrc.

```
sudo bash VMware-Remote-Console-10.0.3-9300449.x86_64.bundle
```

- Connect to the VM that is already running.

```
vmrc --moid=2 --host=ESXI-SERVER-IP-ADDRESS-HERE --user=root --password=ESXI-SERVER-PASSWORD-HERE
```

Note: Change moid to the number from the previous section.

Note: I installed proprietary software in the last three sections because the
web portal in ESXi 6.7 could not send CTRL+ALT+DEL to the host system through
the browser.
