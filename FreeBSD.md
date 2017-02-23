# FreeBSD

WARNING: FreeBSD is for advanced users only.  If you are not very comfortable with UNIX-like command line usage, I would suggest using Debian, Ubuntu, CentOS, or Arch instead of FreeBSD.

FreeBSD is a general purpose UNIX distro that you can install for free at home.

A client uses FreeBSD so I have started teaching myself.  These are notes as I am learning.  Much of my GNU/Linux knowledge carries over, but there are plenty of differences.  If you see I have made a mistake or know of a better way of doing things, add an issue to the SetupNotes repository or send me an email.

# After installation

You are brought to a command line shell upon first boot.  This is similar to minimal and server GNU/Linux distro installations.

The file system can be viewed with this command:

ls /

# Installing packages

The ports system automates package compilation and dependency resolution.  ports can be installed during installation.

tmux is very useful to continue exploring while software compiles.  I would suggest installing tmux first.



Update all of your ports at once:

portupgrade -a
