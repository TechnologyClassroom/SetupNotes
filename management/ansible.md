# Ansible

[Ansible](https://github.com/ansible/ansible) is a free and open source
configuration tool for system automation.

[Official Ansible Documenation](http://docs.ansible.com/ansible/latest/)

[AWX](https://github.com/ansible/awx) is the free and open source equivalent to
Ansible Tower.

## Install Ansible

Install the latest ansible with pip on Debian 9 that will control the other
machines.

```
apt update
apt install -y python3-pip
apt install -y openssh-client
pip3 install ansible
```

All of the clients need openssh-server.

```
apt update
apt install -y openssh-server
systemctl start ssh.service
systemctl enable ssh.service
```

## Establishing initial SSH connections

Generate a new key.

```
ssh-keygen -t rsa -C "TechnologyClassroom"
```

You can choose a different filename, but do not add a password.

Copy your key to the host machines.

```
ssh-copy-id user@192.168.50.51
ssh-copy-id user@192.168.50.78
ssh-copy-id user@192.168.50.123
```

You will have to enter the host's password each time.

Root by password is disable by default on Debian 9.

## Inventory

[Working with Inventory](http://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

Keep track of your inventory of machines with a hosts file in INI syntax or
YAML.

The default location is in /etc/ansible/hosts and you can use arbitrary hosts
files in a different folder to keep them together for version control.  Call an
individual file with the -i switch.

Make a new working directory.

```
mkdir ansible
```

Change to the directory.

```
cd ansible
```

Create a new blank file called hosts.

```
nano hosts
```

Fill the hosts file with group names and the IP addresses of the client
machines.

Group names should be descriptive of their defined goal.  Machines can be in
multiple groups.  Some common group name examples are dev, prod, webservers,
database, compute, cluster, and client.

Variables can be held in the hosts file or in a separate group_vars folder. 

```
[database]
192.168.50.51

[webserver]
192.168.50.51
192.168.50.78
192.168.50.123

[webserver:vars]
ansible_ssh_user=user
```

Machines can be aliased to a more meaningful name in INI format.

```
web1 ansible_user=user ansible_port=2222 ansible_host=192.0.2.50
```

Machines can be aliased to a more meaningful name in YAML format.

```
web1:
  ansible_user: user
  ansible_port: 2222
  ansible_host: 10.12.17.78
```

The default ansible_port is set to 22.

## Send individual tasks to GNU/Linux machines

Ansible is meant to send entire workflows to machines.  Before understanding how
how to utilize Ansible for playbooks or roles, start with single tasks which is
referred to as
[Ad-Hoc commands](http://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html)
throughout Ansible documentation.

Syntax:

```
ansible group -i hostsfile -m module -a arguments -u username
```

The all group is built into ansible and sends the task to every host listed in
the hosts file.

Test a connection to hosts with the ping module.  

```
ansible all -i hosts -m ping -u user
```

Each machine should receive a ping and return a pong resulting in ```SUCCESS```.

Send a simple command to hosts with the command module.  The command module is
the default so we do not need to specify with an -m switch.

```
ansible webservers -i hosts -a "uname -a" -u root
```

The command module cannot handle pipes or I/O redirects.

Run a command with a pipe using the shell module.

```
ansible all -i hosts -m shell -a "find / 2>/dev/null | grep Nacho" -u user
```

Run a command with sudo.

```
ansible all -i hosts -a "shutdown -r now" -u user -s
```

Run a script with the script module.

```
ansible all -i hosts -m script -a bashscriptname.sh -u root
```

Control how many commands are sent at once.  By default, five separate ssh
connections are made at once.  This can be controlled with the --forks switch or
with the ansible configuration file.

```
ansible all -i hosts -m script -a bashscript.sh -u root --forks=2
```

Gather all information from a server.

```
ansible all -i hosts -m setup -u user
```

Manage a service with the service module.

```
ansible webservers -i hosts -m service -a "name=nginx state=restarted" -u user -s --fork=2
```

## Send tasks without indicating the user with the -u switch

Make a group_vars folder.

```
mkdir group_vars
```

Create a file for the group.

```
nano group_vars/webservers
```

Start a YAML file with three dashes ```---```.  The file could look like this:

```
---
ansible_ssh_user: root
```

Run the script without the -u switch.

```
ansible webservers -i hosts -m script -a bashscript.sh
```

## Update software on Debian based machines with the apt module

From http://docs.ansible.com/ansible/latest/modules/apt_module.html

apt module can install software with apt.

```
- name: Upgrade all packages to the latest version
  apt:
    name: "*"
    state: latest

- name: Update all packages to the latest version
  apt:
    upgrade: dist

- name: Run the equivalent of "apt-get update" as a separate step
  apt:
    update_cache: yes

- name: Only run "update_cache=yes" if the last one is more than 3600 seconds ago
  apt:
    update_cache: yes
    cache_valid_time: 3600
```

Use the apt module to install dep packages with dpkg.

```
- name: Install a .deb package
  apt:
    deb: /tmp/mypackage.deb

- name: Install the build dependencies for package "foo"
  apt:
    pkg: foo
    state: build-dep

- name: Install a .deb package from the internet.
  apt:
    deb: https://example.com/python-ppq_0.1-1_all.deb
```

Run apt autoremove and auto clean.

```
- name: Remove useless packages from the cache
  apt:
    autoclean: yes

- name: Remove dependencies that are no longer required
  apt:
    autoremove: yes
```

## Updating CentOS, Scientific Linux, and OSs that use the yum package manager

From http://docs.ansible.com/ansible/latest/modules/yum_module.html

## More modules

See the links section below for more modules.

## Managing Windows systems

https://docs.ansible.com/ansible/devel/user_guide/windows_winrm.html

Instead of SSH, Ansible uses WinRM to connect to Windows machines.

See the links section below for useful Windows modules.

## Playbooks

Playbooks are coded in YAML format.

Run playbooks with the ```ansible-playbook``` command.

Files can be placed from source templates in jinja2 format.

Run an ansible playbook.

```
ansible-playbook site.yml
```

Run an ansible playbook on one group.

```
ansible-playbook site.yml --limit compute
```

## Roles

Roles defined sets of plays that may be reused multiple times.

Roles can be gathered from the ```ansible-galaxy``` command or through the
galaxy.ansible.com website.

Create an empty role template.

````
ansible-galaxy init security
```

Run a series of roles from a playbook by defining the roles in a play.

```
---
- hosts: client
  sudo: yes
  serial: 7
 
  pre_tasks:
    - name: Description of task
    - command: ledctl locate=/dev/sda

  roles:
    - software
    - users
    - qualitycontrol

  task:
    -

  post_tasks:
    -
```	

## Links

[Official Ansible Documenation](http://docs.ansible.com/ansible/latest/)
- [Inventory](http://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)
- [modules](http://docs.ansible.com/ansible/devel/user_guide/modules_intro.html)
  - [Modules by Category](http://docs.ansible.com/ansible/devel/modules/modules_by_category.html)
  - [Command modules]()
    - [command](http://docs.ansible.com/ansible/devel/modules/command_module.html)
    - [expect](http://docs.ansible.com/ansible/devel/modules/expect_module.html)
    - [script](http://docs.ansible.com/ansible/devel/plugins/inventory/script.html)
    - [shell](http://docs.ansible.com/ansible/devel/modules/shell_module.html)
  - [Database modules](http://docs.ansible.com/ansible/devel/modules/list_of_database_modules.html)
  - [File modules](http://docs.ansible.com/ansible/devel/modules/list_of_files_modules.html)
    - [archive](http://docs.ansible.com/ansible/devel/modules/archive_module.html)
    - [copy](http://docs.ansible.com/ansible/devel/modules/copy_module.html)
    - [fetch](http://docs.ansible.com/ansible/devel/modules/fetch_module.html)
    - [file](http://docs.ansible.com/ansible/devel/plugins/lookup/file.html)
    - [find](http://docs.ansible.com/ansible/devel/modules/find_module.html)
    - [lineinfile](https://docs.ansible.com/ansible/devel/modules/lineinfile_module.html)
    - [patch](http://docs.ansible.com/ansible/devel/modules/patch_module.html)
    - [replace](http://docs.ansible.com/ansible/devel/modules/replace_module.html)
    - [stat](http://docs.ansible.com/ansible/devel/modules/stat_module.html)
    - [synchronize](http://docs.ansible.com/ansible/devel/modules/synchronize_module.html)
    - [template](http://docs.ansible.com/ansible/devel/plugins/lookup/template.html)
    - [unarchive](http://docs.ansible.com/ansible/devel/modules/unarchive_module.html)
  - [Net Tool Modules](http://docs.ansible.com/ansible/devel/modules/list_of_net_tools_modules.html)
    - [nmcli](http://docs.ansible.com/ansible/devel/modules/nmcli_module.html)
    - [get_url](http://docs.ansible.com/ansible/devel/modules/get_url_module.html)
    - [slurp](http://docs.ansible.com/ansible/devel/modules/slurp_module.html)
    - [ldap_attr](http://docs.ansible.com/ansible/devel/modules/ldap_attr_module.html)
    - [ldap_entry](http://docs.ansible.com/ansible/devel/modules/ldap_entry_module.html)
  - [Network Modules](http://docs.ansible.com/ansible/devel/modules/list_of_network_modules.html)
    - [net_interface](http://docs.ansible.com/ansible/devel/modules/net_interface_module.html)
  - [Packaging Modules](http://docs.ansible.com/ansible/devel/modules/list_of_packaging_modules.html)
    - [gem](http://docs.ansible.com/ansible/devel/modules/gem_module.html) (Ruby)
    - [npm](http://docs.ansible.com/ansible/devel/modules/npm_module.html) (node.js)
    - [pip](http://docs.ansible.com/ansible/devel/modules/pip_module.html) (Python)
    - [apt](http://docs.ansible.com/ansible/devel/modules/apt_module.html)
    - [apt_repository](http://docs.ansible.com/ansible/devel/modules/apt_repository_module.html)
    - [dnf](http://docs.ansible.com/ansible/devel/modules/dnf_module.html) (Fedora)
    - [dpkg_selections](http://docs.ansible.com/ansible/devel/modules/dpkg_selections_module.html)
    - [openbsd_pkg](http://docs.ansible.com/ansible/devel/modules/openbsd_pkg_module.html)
    - [package](http://docs.ansible.com/ansible/devel/modules/package_module.html)
    - [package_facts](http://docs.ansible.com/ansible/devel/modules/package_facts_module.html)
    - [pacman](http://docs.ansible.com/ansible/devel/modules/pacman_module.html) (Arch)
    - [pkgng](http://docs.ansible.com/ansible/devel/modules/pkgng_module.html) (FreeBSD)
    - [portage](http://docs.ansible.com/ansible/devel/modules/portage_module.html) (Gentoo)
    - [portinstall](http://docs.ansible.com/ansible/devel/modules/portinstall_module.html) (FreeBSD)
    - [redhat_subscription](http://docs.ansible.com/ansible/devel/modules/redhat_subscription_module.html) (RHEL)
    - [rhn_channel](http://docs.ansible.com/ansible/devel/modules/rhn_channel_module.html) (RHEL)
    - [rhsm_repository](http://docs.ansible.com/ansible/devel/modules/rhsm_repository_module.html) (RHEL)
    - [slackpkg](http://docs.ansible.com/ansible/devel/modules/slackpkg_module.html) (Slackware)
    - [sorcery](http://docs.ansible.com/ansible/devel/modules/sorcery_module.html) (Source Mage)
    - [yum](http://docs.ansible.com/ansible/devel/modules/yum_module.html)
    - [yum_repository](http://docs.ansible.com/ansible/devel/modules/yum_repository_module.html)
    - [zypper](http://docs.ansible.com/ansible/devel/modules/zypper_module.html) (OpenSUSE)
    - [zypper_repository](http://docs.ansible.com/ansible/devel/modules/zypper_repository_module.html) (OpenSUSE)
  - [Source Control](http://docs.ansible.com/ansible/devel/modules/list_of_source_control_modules.html)
    - [bzr](http://docs.ansible.com/ansible/devel/modules/bzr_module.html)
    - [git](http://docs.ansible.com/ansible/devel/modules/git_module.html)
    - [git_config](http://docs.ansible.com/ansible/devel/modules/git_config_module.html)
    - [github_key](http://docs.ansible.com/ansible/devel/modules/github_key_module.html)
    - [github_release](http://docs.ansible.com/ansible/devel/modules/github_release_module.html)
    - [hg](http://docs.ansible.com/ansible/devel/modules/hg_module.html) (mercurial)
    - [subversion](http://docs.ansible.com/ansible/devel/modules/subversion_module.html)
  - [Storage](http://docs.ansible.com/ansible/devel/modules/list_of_storage_modules.html)
    - [lvg](http://docs.ansible.com/ansible/devel/modules/lvg_module.html) (LVM)
    - [lvol](http://docs.ansible.com/ansible/devel/modules/lvol_module.html) (LVM)
    - [zfs](http://docs.ansible.com/ansible/devel/modules/zfs_module.html)
    - [zfs_facts](http://docs.ansible.com/ansible/devel/modules/zfs_facts_module.html)
    - [zpool_facts](http://docs.ansible.com/ansible/devel/modules/zpool_facts_module.html) (ZFS)
  - [System modules](http://docs.ansible.com/ansible/devel/modules/list_of_system_modules.html)
    - [authorized_key](http://docs.ansible.com/ansible/devel/modules/authorized_key_module.html)
    - [cron](http://docs.ansible.com/ansible/devel/modules/cron_module.html)
    - [filesystem](http://docs.ansible.com/ansible/devel/modules/filesystem_module.html)
    - [firewalld](http://docs.ansible.com/ansible/devel/modules/firewalld_module.html)
    - [group](http://docs.ansible.com/ansible/devel/modules/group_module.html)
    - [hostname](http://docs.ansible.com/ansible/devel/modules/hostname_module.html)
    - [interfaces_file](http://docs.ansible.com/ansible/devel/modules/interfaces_file_module.html)
      controls the /etc/network/interfaces file.
    - [kernel_blacklist](http://docs.ansible.com/ansible/devel/modules/kernel_blacklist_module.html)
    - [make](http://docs.ansible.com/ansible/devel/modules/make_module.html)
    - [modprobe](http://docs.ansible.com/ansible/devel/modules/modprobe_module.html)
    - [mount](http://docs.ansible.com/ansible/devel/modules/mount_module.html)
    - [parted](http://docs.ansible.com/ansible/devel/modules/parted_module.html)
    - [ping](http://docs.ansible.com/ansible/devel/modules/ping_module.html)
    - [selinux](http://docs.ansible.com/ansible/latest/modules/selinux_module.html)
    - [seboolean](http://docs.ansible.com/ansible/devel/modules/seboolean_module.html)
    - [setup](http://docs.ansible.com/ansible/devel/modules/setup_module.html)
    - [sysctl](http://docs.ansible.com/ansible/devel/modules/sysctl_module.html)
    - [systemd](http://docs.ansible.com/ansible/devel/modules/systemd_module.html)
    - [user](http://docs.ansible.com/ansible/devel/modules/user_module.html) can
      create and modify users.
  - [Utility modules](http://docs.ansible.com/ansible/devel/modules/list_of_utilities_modules.html)
    - [debug](http://docs.ansible.com/ansible/latest/modules/debug_module.html
    - [fail](http://docs.ansible.com/ansible/devel/modules/fail_module.html)
    - [pause](http://docs.ansible.com/ansible/devel/modules/pause_module.html)
    - [set_fact](http://docs.ansible.com/ansible/devel/modules/set_fact_module.html)
    - [set_stats](http://docs.ansible.com/ansible/devel/modules/set_stats_module.html)
    - [wait_for](http://docs.ansible.com/ansible/devel/modules/wait_for_module.html)
    - [wait_for_connection](http://docs.ansible.com/ansible/devel/modules/wait_for_connection_module.html)
  - [Windows modules](https://docs.ansible.com/ansible/latest/modules/list_of_windows_modules.html)
    - [win_chocolatey](http://docs.ansible.com/ansible/latest/modules/win_chocolatey_module.html)
      installs a package through Chocolatey
    - [win_package](https://docs.ansible.com/ansible/latest/modules/win_package_module.html#win-package)
      installs an executable file.
    - [win_reboot](http://docs.ansible.com/ansible/latest/modules/win_reboot_module.html)
      can reboot Windows.
    - [wait_for_connection](http://docs.ansible.com/ansible/latest/modules/wait_for_connection_module.html)
      waits for a connection if a reboot occured. The wait_for_connection module
      is not Windows specific, but it is useful when paired with win_reboot.
    - [win_regedit](https://docs.ansible.com/ansible/devel/modules/win_regedit_module.html)
      edits an individual registry value.
    - [win_regmerge](http://docs.ansible.com/ansible/latest/modules/win_regmerge_module.html)
      installs multiple registry changes through a .reg file.
    - [win_service](http://docs.ansible.com/ansible/devel/modules/win_service_module.html)
      makes changes to services.
    - [win_updates](http://docs.ansible.com/ansible/latest/modules/win_updates_module.html)
      manages Windows Updates across reboots until finished.
  - [Developing modules](http://docs.ansible.com/ansible/latest/dev_guide/developing_modules.html)
- [User Guide](http://docs.ansible.com/ansible/latest/user_guide/)
- [Playbooks Templating (Jinja2)](http://docs.ansible.com/ansible/latest/user_guide/playbooks_templating.html)
- [Playbooks Variables](http://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)
- [Best Practices](http://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html)
- [become](http://docs.ansible.com/ansible/devel/user_guide/become.html)
- [YAML Syntax](http://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html#yaml-syntax)

Ansible Github
- [ansible](https://github.com/ansible/ansible)
- [ansible-examples](https://github.com/ansible/ansible-examples) - examples and
  best practices for building Ansible Playbooks.
- [ansible-modules-core](https://github.com/ansible/ansible-modules-core)
- [galaxy](https://github.com/ansible/galaxy)

Tutorials and third-party examples
- https://www.youtube.com/watch?v=ZNB1at8mJWY
- https://github.com/geerlingguy/raspberry-pi-dramble
- https://github.com/geerlingguy/ansible-vagrant-examples
- Cleaning up Ansible
  - https://github.com/ryanlelek/ansible-role-logout
  - https://github.com/yu0819ki/ansible-playbook-bash-history-settings
  - https://stackoverflow.com/questions/38200732
  - https://serverfault.com/questions/612017
- https://github.com/bertvv/ansible-role-pxeserver
- https://github.com/PacktPublishing/OpenStack-Administration-with-Ansible-2

Linters
- [ansible-lint](https://github.com/willthames/ansible-lint)
- [yaml-lint](https://github.com/rasshofer/yaml-lint)
