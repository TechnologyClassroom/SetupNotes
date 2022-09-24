# Arch Linux

Arch is known for a steep learning curve for users that are new to GNU/Linux.  This is not entirely the case anymore, but it does come with it's own set of challenges.  I would
only suggest using Arch if you have used GNU/Linux as your primary operating
system for at least 6 months.  After the installation is complete, the
system is very nice to use.

What makes Arch uniquely different is that most of the software comes unmodified directly from the upstream developers.  This is in stark contrast to stable distributions such as Debian stable, Ubuntu LTS, CentOS, and Red Hat Enterprise Linux who may simultaneously maintain several versions of packages for up to ten years.

[Arch webpage](https://www.archlinux.org/)

[Arch Wiki](https://wiki.archlinux.org/) - an extensive resource for Arch and
other GNU/Linux operating systems

[The Arch Way](https://wiki.archlinux.org/index.php/The_Arch_Way_(%D0%A1%D1%80%D0%BF%D1%81%D0%BA%D0%B8)) -
the philosophy behind Arch

[Arch Packages](https://www.archlinux.org/packages/) - compiled software
available for the system

[Arch User Repository (AUR)](https://aur.archlinux.org/) - a set of build
scripts for more software

## Downloading Arch

[Arch Downloads](https://www.archlinux.org/download/)

Download the latest ISO with through torrents or your closest HTTP direct
source.  HTTP direct downloads are sorted by country.

## Installing Arch

As a right of passage, you should install Arch using only the
[Installation Guide](https://wiki.archlinux.org/index.php/Installation_guide)
and the [Arch Wiki](https://wiki.archlinux.org/).  Take notes as you go.  You
will learn more about the system if you avoid blog posts and youtube videos the
first time.

After installation, look at the
[General recommendations](https://wiki.archlinux.org/index.php/General_recommendations)
for a direction to take.

If you give a full attempt and fail, try using the archinstall script.

On your second install, use your notes or automate the installation.

## AUR and pacaur

As a right of passage, you should install your first AUR packages yourself using
the Arch wiki.  Package managers exist for the AUR.  I would suggest installing
cower and pacaur first.  Once you have pacaur, more software can be easily
installed from the AUR.

On your second install, the installation for pacaur can be automated with this
bash script: https://gist.github.com/Tadly/0e65d30f279a34c33e9b

pacaur builds packages as
~/.cache/pacaur/packagename/packagename-version-arch.pkg.tar.xz

## Customizing a new Arch ISO

[Remastering the Install ISO](https://wiki.archlinux.org/index.php/Remastering_the_Install_ISO)

[archiso](https://wiki.archlinux.org/index.php/archiso)

## Creating a custom repo

[Custom local repository](https://wiki.archlinux.org/index.php/Pacman/Tips_and_tricks#Custom_local_repository)

Create initial repo database

```
cd /location/for/custom/repo
mkdir -p customrepo/x86_64
mv /location/of/custom/package/builds/*.tar.xz .
repo-add customrep.db.tar.gz ./*
```

Update repo database

```
cd /location/for/custom/repo/customrepo/x86_64
mv /location/of/custom/package/builds/*.tar.xz .
repo-add -n customrep.db.tar.gz ./*.xz
```

[Fusion809 shows how to create a custom repo on github](https://fusion809.github.io/how-to-create-archlinux-repository/)

## Free Software and the FSF

Arch Linux contains proprietary software.  The
[Free Software Foundation](http://www.fsf.org/) has approved
[Parabola](https://www.parabola.nu/) as an Arch based
[free distro](https://www.gnu.org/distros/free-distros.html) that does not
include proprietary software at all.

[Parabola](https://www.parabola.nu/) - includes resources to convert your Arch
install to Parabola

[Parabola Downloads](https://wiki.parabola.nu/Get_Parabola)
