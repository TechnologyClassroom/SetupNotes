# OpenBSD

Michael McMahon

WARNING: OpenBSD is for advanced users only.  If you are not very comfortable
with UNIX-like command line usage, I would suggest using Debian, Ubuntu, CentOS,
or Arch instead of FreeBSD.

[IRCNow](https://wiki.ircnow.org/?n=Minutemin.Bootcamp) has a large collection
of tutorials focusing on OpenBSD.

## Remove non-free firmware

During the installation, a script is run that installs non-free firmware.  Use
this command to remove the non-free firmware.

    fw_update -da

An unmaintained fork of OpenBSD called
[LibertyBSD](https://web.archive.org/web/20210914024648/https://libertybsd.net/)
had [a script](https://notabug.org/LibertyBSD/libertybsd-scripts) to remove all
non-free firmware from OpenBSD.  HyperbolaBSD plans to be another free BSD fork
in the future.
