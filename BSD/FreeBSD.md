# FreeBSD

Michael McMahon

WARNING: FreeBSD is for advanced users only.  If you are not very comfortable
with UNIX-like command line usage, I would suggest using Debian, Ubuntu, CentOS,
or Arch instead of FreeBSD.

FreeBSD is a general purpose UNIX distro that you can install for free at home
or work.

A client uses FreeBSD so I have started teaching myself.  These are notes as I
am learning.  Much of my GNU/Linux knowledge carries over, but there are plenty
of differences.  If you see I have made a mistake or know of a better way of
doing things, add an issue to the SetupNotes repository or send me an email.

Note: if you want a distribution that allows you to start with a GUI environment
that is still built on FreeBSD, [try TrueOS](https://www.trueos.org/downloads/).

## Installation

[Installing FreeBSD](https://www.freebsd.org/doc/handbook/bsdinstall.html)

[Installing with software RAID 1](https://www.ateamsystems.com/tech-blog/installing-freebsd-9-gmirror-gpt-partitions-raid-1/)

## After installation

You are brought to a command line shell upon first boot.  This is similar to
minimal and server GNU/Linux distro installations.

The file system can be viewed with this command:

```ls /```

## Installing software

[Find software packages](https://www.freebsd.org/doc/handbook/ports-finding-applications.html)

[Install binary packages with pkg](https://www.freebsd.org/doc/handbook/pkgng-intro.html)

[Compiling from ports](https://www.freebsd.org/doc/handbook/ports-using.html)

## Updating software

```
freebsd-update fetch
freebsd-update install
```

# Compiling software from Ports (tmux example)

The ports system automates package compilation and dependency resolution.  ports
can be installed during installation.

https://www.freebsd.org/doc/handbook/ports-using.html

The first time you update port configuration, you must download all
configurations (similar to apt-get update on Debian based distros):

```portsnap fetch extract```

tmux is very useful to continue exploring while software compiles.  I would
suggest installing tmux first.

```
cd /usr/ports
find . | grep tmux
```

This reveals ./sysutils/tmux amongst other files.  CTRL+C will stop the search
process.

```cd sysutils/tmux```

The next step is very important.  If we do not configure dependencies first, the
installation will hang between each compilation at each dependency
configuration.  All configurations can be done at once with:

```make configure-recursive```

Up and down arrows move through the menu.  The space bar selects and deselects
options.  The enter key goes to the next package configuration.  Pressing enter
multiple times will choose the default options.

After configuring each package, compile every package necessary with:

```make install```

## Using tmux

Start tmux and a green bar will show up at the bottom of the shell.

To invoke a tmux command use CTRL+B followed by another character.

Character   -   Action
?   -   help
"   -   Split the screen vertically
%   -   Split the screen horizontally

## Updating software from Ports

Update the latest port configurations (similar to apt-get update on Debian based
distros):

```portsnap fetch update```

update only retrieves the new configurations instead of retrieving all
configurations.

Install portupgrade with these commands:

```
cd /usr/ports/ports-mgmt/portupgrade
make config-recursive
make install
```

Update all of your ports at once (this takes a long time with many configuration
prompts):

```portupgrade -a -c -r```

Switch explanations: -a all -c configure before -r recursive

## nano

nano is an easy command line text editor.

```
cd /usr/ports/editors/nano
make config-recursive
make install
```

## Alias

An alias is a shorthand shortcut in the shell.

Check all of the aliases on the user account with this command:

```alias```

Create a new alias with this syntax:

```alias pfu='portsnap fetch update'```

To edit the root user's aliases, run this command:

```nano /root/.cshrc```

## Clearing bash history

```
rm .history
history -c
exit
```

## GNU/Linux Alternatives

lsblk = 'geom disk list | grep Geom'
