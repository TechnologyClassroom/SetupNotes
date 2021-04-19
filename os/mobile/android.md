# Android

[Android](https://www.android.com/) is the
[#1](https://en.wikipedia.org/wiki/Usage_share_of_operating_systems#Mobile_devices)
mobile phone operating system and uses the
[Linux kernel](https://www.kernel.org/).

The majority of Android is free and open source through the
[Android Open Source Project (AOSP)](https://source.android.com/), but the phone
manufacturers frequently add proprietary apps and drivers that cannot be audited
or removed.

## Recommended phones and tablets

The Google line of phones all come with
[stock Android](https://developers.google.com/android/images) and can be
purchased with an unlocked bootloader.

When buying a new phone, consult whether the phone is supported by alternative
operating systems.  Check the
[LineageOS Download page](https://download.lineageos.org/) and
[Replicant Devices](https://www.replicant.us/supported-devices.php) page first
to see what your options are.

Older Google phones can be found cheaper on ebay.

## Alternative versions of Android

I would suggest using [LineageOS](https://lineageos.org/) or
[Replicant](https://www.replicant.us/).

[LineageOS](https://lineageos.org/) is Android without Google.  This is my
favorite version of Android.

[Replicant](https://www.replicant.us/) is Android without any proprietary
software.

Before changing the OS, make a backup of your files and OS.

## App Stores

Unlike iOS, there are many different app stores available for Android.

[F-Droid](https://f-droid.org/en/) is a free and open source app repository for
Android based phones.  Applications that may not have your best interests will
list their antifeatures.  Most applications found in F-Droid contain Richard
Stallman's Four Freedoms.

Most phones will come with Google Play Store preinstalled.  I do not trust
Google and I only use [F-Droid](https://f-droid.org/en/).

## adb

### Install

Install adb on a Debian based GNU/Linux distribution.  `adb` works for other
operating systems, but I am only documenting GNU/Linux.

```
sudo apt update && sudo apt install -y adb
```

### Backup

Connect the phone to the computer.

Start the adb server and list phones.

```
sudo adb devices
```

At this point, the phone asks you for permssion.

Enter the shell on the phone.

```
adb shell
```

List the files on the phone.

```
ls sdcard
```

Exit the adb shell.

```
exit
```

Make a directory to dump the files in.

```
mkdir ebooks
```

Change into that directory.

```
cd ebooks
```

Pull a folder.

```
adb pull /sdcard/ebooks/
```

Make another folder and backup another folder.

```
mkdir ../camera
cd ../camera
adb pull /sdcard/DCIM/OpenCamera/
```

Once you know all of the folders you want to backup, you can build a script to
run through the process.
