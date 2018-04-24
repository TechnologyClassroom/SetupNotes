# SSH remote connection notes

# Michael McMahon

## Change the default password to a strong password

BEFORE PLACING A SYSTEM ON A REMOTE NETWORK, MAKE THE PASSWORDS STRONG.

To change a password use ```passwd```.

```passwd root```

```passwd user```

Enter in the old password and then the new password twice (unless you are root).


## IP addresses and port forwards

SSH uses port 22 by default.  The router configurations can forward the port to
an external facing port.


## Set a static IP on Red Hat Enterprise Linux (RHEL) 7.4 with GNOME

- Right click on the power symbl in the top-right.
- Click on the wrench and screwdriver icon.
- Click on ```Network```.
- Click on the network interface that needs a static IP.
- Click on hte gear icon.
- Click on IPv4.
- Change the '''Addresses``` drop down box from ```Automatic (DHCP)``` to
  ```Manual```.
- Change these settings:
  - ```Address```
  - ```Netmask```
  - ```Gateway```
  - ```DNS Server```
- Click on the ```Apply``` button.
- Open a terminal and test the network connection.

```
ping www.google.com
```

- Log out.
  - Click on the Power symbol in the top-right.
  - Click on the user account.
  - Click on ```Log out```.
- Test the connection on your phone.


## Set a static IP on CentOS 6 with GNOME

- Right click on the network icon in the top-right.
- Edit Connections...
- Click on "System eth0" and the "Edit..." button.  Replace ```eth0``` with the
  network interface that needs a static IP.
- Check the "Connect automatically" box.
- Click on the "IPv4 Settings" tab.
- Change the "Method:" dropdown box to Manual and click the "Add..." button.
- Click in the first box under Address.
- Type in the IP addresses ```10.12.19.221``` tab ```255.255.255.0``` tab
  ```10.12.19.1```.  ```10.12.19.XXX``` should be changed to your subnet.
- Set the ```DNS servers:``` to ```1.1.1.1```.
- Click the ```Apply...``` button.
- Click the ```Close``` button.


## Set a static IP on Ubuntu 16.04 Server

Note: Ubuntu 17.10 and onward use a different method.

- Edit the ```/etc/network/interfaces``` file.

```
sudo nano /etc/network/interfaces
```

Move the cursor using the arrow keys to the line that says:
```iface em1 inet dhcp```

Replace ```em1``` with the network interface that needs a static IP.

Use ```CTRL+K``` to cut the line.
Use ```CTRL+U``` twice to paste the line twice.

Place a pound sign ```#``` before one of the lines.
On the other line, change ```dhcp``` to ```static```.

Add these four indented lines below.  I have been using two spaces for
indents.  Change the address accordingly.

```
  address 10.12.19.224
  netmask 255.255.255.0
  gateway 10.12.19.1
  dns-nameserver 1.1.1.1
```

```10.12.19.XXX``` should be changed to your subnet.

```/etc/network/interfaces``` should look like this:

```
auto em1
#iface em1 inet dhcp
iface em1 inet static
   address 10.12.19.224
   netmask 255.255.255.0
   gateway 10.12.19.1
   dns-nameserver 1.1.1.1
```

CTRL+X, y, enter saves the file.

- Install openssh-server.

```
sudo apt-get update
sudo apt-get install -y openssh-server
```

- Restart the network device.

```
sudo ifdown em1
sudo ifup em1
```

Replace em1 with the name of the Network Interface that was used above.

- Test the network connection.

```
ping www.google.com
```

Use CTRL+C after a moment to stop the test.  Make sure there is no packet loss.

- Test that ssh is listening on port 22.

```
sudo netstat -anp | grep sshd
```

If nothing appears, check that openssh-server is installed and that the server
is running.

- Use an SSH client on your phone to test the connection.  Make sure your phone
  is not connected to wifi.

```
Yes
```

Enter client's password.

You should get a prompt.  Type:

```
exit
```


## Connecting to an openssh-server with openssh-client

- Open a terminal on a machine with access to the same LAN or public IP.
- Install openssh-client on your machine.

Install openssh-client on Debian based systems.

```
sudo apt-get install -y openssh-client
```

Install openssh-client on Red Hat based systems.

```
yum install -y openssh-client
```

- Connect to the client over SSH.

```
ssh username@ipaddress:portnumber
```

Replace username with the username you wish to log in with.  Replace ipaddress
with the IP address of the client.  Replace portnumber with the port that ssh is
running on.  The default port is 22.

The first connection must be verified with a yes or no response.

If a public/private key pair has not been setup, the password must be entered
each time a connection is made.

Note: Windows machines can use (PuTTY](https://ninite.com/putty/) instead of
openssh-client.


## Connecting to an openssh-server on your phone

I have had success with these three apps:

- [ConnectBot(F-Droid)](https://f-droid.org/en/packages/org.connectbot/)
- [ConnectBot(Google Play)](https://play.google.com/store/apps/details?id=org.connectbot)
- [Termius (Apple App Store)](https://itunes.apple.com/us/app/termius/id549039908?mt=8)

These all use the same concept as the command with openssh-client.  The
username, IP address, and port are required for connection.
