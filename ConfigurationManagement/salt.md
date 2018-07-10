# Salt

Salt is a configuration management tool written in python similar to ansible,
puppet, and chef.  Scripts are written in YAML and Jinja.

Salt is free and open source and licensed under the Apache 2.0 license.

[Website](https://saltstack.com/)

[github](https://github.com/saltstack/salt)

Concepts in this file mostly from the Linux Academy course
[Using Salt for Configuration Management and Orchestration](https://linuxacademy.com/cp/modules/view/id/190),
and I made the commands more script friendly with sed.

## Ports

Minions listens to Master on port 4505.
Minions send to Master on port 4506.

## Terms

All of the configuration management tools are very similar and use different
terms to further brand their product.

- Configuration Management - see states
- A grain is a static fact about the systemsuch as OS, kernel, and CPU
  architecture.  Custom grains can be set such as physical location in data
  center or role.  Grains are lowercase.
- Master(s) rule(s) Minions
- Orhestration is the act of running commands on several systems at once.
- Pillar is user-defined variables.  Data is stored on the salt master and only
  accessible by minions.  Often pillar distributes secrets.
- States are the declaritive way that the server should be configured.
- YAML Ain't Markup Language is a human friendly data serialization standard for
  all programming languages.

## Ad-hoc example

```
salt '*' user.add user home=/home/user shell=/bin/bash
```

## Declaritive example

```
user:
  user.present:
    - home: /home/user
    - shell: /bin/bash
```

## Managing Windows

Modules specific to Windows start with ```win_```.

## Management options

- Single Master
  - Traditional setup with one master.
- Multi-Master
  - Redundant
    - All masters run simutaneously.
    - Any masters can be accessed.
    - Masters share the same public key.
    - All minions must be added to all masters.
    - Masters must be synced separately through git, rsync, or another method.
    - ```file_roots``` and ```pillar_roots``` must be the same across all masters.
  - Failover
    - Single master at a time.
    - When the current master cannot be reached, the next master is called.
- Masterless
  - In minion config, set ```file_client``` line to ```local```.
  - ```--local``` is not necessary.
  - Good for testing before pushing to production or configuring masters.
- Agentless
  - Install the salt-ssh package.
  - Do not install agents on the minions.
  - Similar to Ansible or Puppet Bolt.

## Installing Salt

Here are four methods:

- Bootstrap master
- Bootstrap minion
- Install through SaltStack apt repository
- Install through SaltStack yum repository

### Bootstrap the Master

The bootstrap method is most common.

- Install the dependencies ```curl``` and ```python3-pip``` using your package manager.

```
yum install -y curl 2>/dev/null
apt update 2>/dev/null
apt install -y curl 2>/dev/null
```

Note: The above three lines would work in a script for both Red Hat based distributions and Debian based distributions.

- Download the script.

```
curl -L https://bootstrap.saltstack.com -o install_salt.sh
```

- View the script to make sure the website was not compromised.

```
less install_salt.sh
```

- Run the script as root.

```
sh install_salt.sh -P -M
```

```-P``` allows the usage of pip.  ```-M``` configures a master server.

- Salt expects the hostname to be salt.  Update the /etc/hosts file with this
  command as root.

```
sed -i 's/127.0.0.1/127.0.0.1 salt /' /etc/hosts
```

- Salt is installed.

### Bootstrap the Minions

The bootstrap method is most common.

- Install the dependencies ```curl``` and ```python3-pip``` using your package
  manager as root.

```
yum install -y curl 2>/dev/null
apt update 2>/dev/null
apt install -y curl 2>/dev/null
```

Note: The above three lines would work in a script for both Red Hat based
distributions and Debian based distributions.

- Download the script.

```
curl -L https://bootstrap.saltstack.com -o install_salt.sh
```

- View the script to make sure the website was not compromised.

```
less install_salt.sh
```

- Run the script as root.

```
sh install_salt.sh -P
```

```-P``` allows the usage of pip.  ```-M``` is not used like in the master.

- The minion needs the master added to its hosts file.  Update the
  ```/etc/hosts``` file with this command as root.

```
echo "192.168.50.207 salt" >> /etc/hosts
```

- Salt is installed.

### Install Through Apt Repository

This is specific to Ubuntu 16.04, but other Debian based distributions can
follow this section by modifying addresses when noted.

- Add the key.

```
wget -O https://repo.saltstack.com/apt/ubuntu/16.04/amd64/latest/SALTSTACK-GPG-KEY.pub | sudo apt-key add -
```

Note: This key is specifically for Ubuntu 16.04.  Change the address accordingly
for a different Debian based distribution or version.

- Add the repsitory to the sources list as root.

```
echo "deb https://repo.saltstack.com/apt/ubuntu/16.04/amd64/latest xenial main" >> /etc/apt/sources.list.d/saltstack.list
```

Note: This repo is specifically for Ubuntu 16.04.  Change the address
accordingly for a different Debian based distribution or version.

- Update the repositories.

```
sudo apt update
```

- Install salt.

```
sudo apt install -y salt-minion
```

Note: salt-minion can be replaced with salt-master, salt-ssh, salt-syndic,
salt-cloud, or salt-api depending on your use case.

- Salt is installed.

### Install Through Yum Repository

This works for almost all Red Hat based distributions such CentOS, RHEL, Fedora,
and Scientific Linux.

- Add the repo as root.

```
yum install https://repo.saltstack.com/yum/redhat/salt-repo-latest-2.el7.noarch.rpm
```

- Update yum repositories as root.

```
yum clean expire-cache
```

- Install salt.

```
yum install -y salt-minion
```

Note: salt-minion can be replaced with salt-master, salt-ssh, salt-syndic,
salt-cloud, or salt-api depending on your use case.

- Salt is installed.

## Masterless Configuration

- Install salt-minion with any of the above methods.

- Stop the salt-minion service as root.

```
systemctl stop salt-minion
```

- Change the ```file_client``` from the default ```remote``` to ```local``` in
  the ```/etc/salt/minion``` config file.

```
sed -i 's/#file_client: remote/file_client: local/' /etc/salt/minion
```

- Uncomment the ```file_roots``` section below ```file_client```.

```
sed -i 's/#file_roots:/file_roots:/' /etc/salt/minion
sed -i 's/#  base:/  base:/' /etc/salt/minion
sed -i 's/#    - /srv/salt/    - /srv/salt/' /etc/salt/minion
```

## Key management

- View configured keys as root.

```
salt-key -L
```

Note: If you see one extra, the master acts as a minion to itself.

- View the master's public key.

```
salt-key -F master
```

- Add the ```master.pub``` key to the ```/etc/salt/minion``` file to pair the
master with itself.

```
sed -i "s/#master_finger: /x27/x27/master_finger: /x27$(salt-key -F master | grep master.pub | cud -d' ' -f3)/x27/" /etc/salt/minion
```

Note: This same command will not work for minions.  ```\x27``` is an alternative
for apostraphe.  ```$(salt-key -F master | grep master.pub | cud -d' ' -f3)```
expands into the public key.

- Restart the salt service as root.

```
systemctl restart salt-minion
```

- View fingerprints of available keys as root.

```
salt-key -F
```

- Find our local fingerprint as root.

```
salt-call --local key.finger
```

```salt-call --local``` can be used to run nearly any salt command on your local
machine to test custom configurations.

- Match the fingerprints from the last two commands.  Copy the hostname.

- Accept the minion id as root.

```
salt-key -a debian -y
```

Note: debian is my hostname in my example.

- (Optionally) Accept all keys as root.

```
salt-key -A -y
```

- All minions can communicate at this point.

- (Optional) Reject all keys as root.

```
salt-key -R
```

## Renaming a minion

- Edit or overwrite the contents of the ```minion_id``` file as root.

```
echo "newminionname" > /etc/salt/minion_id
```

- Remove the ```minion.pem``` and ```minion.pub``` keys that are associated with
  the old minion name from the minion as root.

```
cd /etc/salt/pki/minion
rm minion.pem
rm minion.pub
```

Alternatively, you could run this command as root:

```
rm -f /etc/salt/pki/minion/minion.p*
```

- List the salt keys as root.

```
salt-key -L
```

- Remote the old minion key from the salt-master as root.

```
salt-key -d oldminionidhere
```

- (Optionally) Remove all of the minion keys from the salt-master as root.

```
salt-key -D -y
```

- Verify the keys have been removed.

```
salt-key -L
```

- Regenerate minion keys by restarting the salt-minion service as root.

```
systemctl restart salt-minion
```

- The keys are now listed as ```Unaccepted keys```.

```
salt-key -L
```

- View fingerprints of available keys as root.

```
salt-key -F
```

- Find our local minion fingerprint as root.

```
salt-call --local key.finger
```

- Match the fingerprints from the last two commands.  Copy the hostname.

- Accept the minion id as root.

```
salt-key -a debian -y
```

Note: debian is my hostname in my example.

- (Optionally) Accept all keys as root.

```
salt-key -A -y
```

- All minions can communicate at this point.

## Execution modules

Execution modules run an action on many systems at once.

[List of execution modules](https://docs.saltstack.com/en/latest/ref/modules/all/index.html)

[Remote Execution Tutorial](https://docs.saltstack.com/en/latest/topics/tutorials/modules.html)

- Remote execution syntax

```
salt 'TARGET(S)' FUNCTION ARGUMENTS
```

### test module

- Ping all targets.

```
salt '*' test.ping
```

- Echo command

```
salt '*' test.echo 'This is a test!'
```

- Run multiple functions at once.

```
salt '*' test.ping,test.echo ,'This is a test!'
```

### cmd module

- Run arbitrary commands.

```
salt '*' cmd.run "whoami" runas=user
```

Note: ```runas=``` allows you to specify the user that runs the command.
```root``` is the default and does not require explicitly using ```runas=```.

- Run which.

```
salt '*' cmd.which "whoami"
```

- Set vim to use 2 spaces for tabs.

```
salt 'salt' cmd.run 'echo "set softtabstop=2\nset tabstop=2\nset shiftwidth=2\nset extendtaib\nretab" >> .vimrc' runas=user
```

From https://linuxacademy.com/cp/courses/lesson/course/1826/lesson/3/completed/2/module/190

### sys module

- List all installed modules on the salt master.

```
salt 'salt' sys.list_modules
```

- List all functions of an installed module on the salt master.

```
salt 'salt' sys.list_functions user
```

- View documenation for a module.

```
salt 'salt' sys.doc user
```

- View documenation for a function.

```
salt 'salt' sys.doc user.add
```

### pkg module

- Upgrade all software.

```
salt '*' pkg.upgrade
```

- Install a program.

```
salt '*' pkg.install vim
```

- Remove a program.

```
salt '*' pkg.remove vim
```

## Targeting

[Targeting Minions](https://docs.saltstack.com/en/latest/topics/targeting/index.html)

Targets can be identified by:

- Grains
- Pillars
- [Nodegroups](https://docs.saltstack.com/en/latest/topics/targeting/nodegroups.html#targeting-nodegroups)
- minion_id
- regular expressions

Compound Targeting is the act of using multiple methods of targeting at once.

- Target everything.

```
salt '*' cmd.run "whoami" runas=user
```

- Target by minion_id.

```
salt 'database01' cmd.run "whoami" runas=user
```

- Target by grain.

```
salt -G 'os:Ubuntu' cmd.run "whoami" runas=user
```

- Compound targeting with grains and regular expressions.

```
salt -C 'G@os:Ubuntu or E@web*' cmd.run "whoami" runas=user
```
