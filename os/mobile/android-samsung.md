# Android Samsung

[Android](https://www.android.com/) is the
[#1](https://en.wikipedia.org/wiki/Usage_share_of_operating_systems#Mobile_devices)
mobile phone operating system and uses the
[Linux kernel](https://www.kernel.org/).

The majority of Android is free and open source through the
[Android Open Source Project (AOSP)](https://source.android.com/), but the phone
manufacturers (including Google) frequently add proprietary apps and drivers that cannot be audited
or removed.

Samsung modifies their images further and this page is specifically for the
Samsung variation of Android. See my regular
[Android page](https://github.com/TechnologyClassroom/SetupNotes/blob/master/os/mobile/android.md)
for more general information.

## Galaxy Tab A9+

This tablet was chosen for some kids over a new iPad or a Google Tablet because
it had external SD card for storage and a headphone jack. Both of these are
rare features on new hardware now. There is some progress on alternative ROMs
over on XDA forums, but we will see if there are alternative operating systems
available in the future.

I generally recommend not purchasing devices at mobile phone stores and these
were purchased directly from Samsung.


### First boot and setup

"Secured by Knox" eyeroll

#### Welcome screen

Select language: English (United States)

Tap on the `Start` button.

#### For your review screen

Tap the check next to `I agree to Samsung Terms and Conditions [...]` and `I agree to the samsung Privacy Policy.` options, but do not check `I agree to the sending of diagnostic data to Samsung. (optional)` or `Agree to all (optional)` options.

Tap on the `Agree` button.

#### Easy setup with another device

I am going to setup these by themselves so I am choosing the `Set up manually` option.

#### Choose a Wi-Fi network

This sometimes shoe-horns your next choices so I am going to skip this option for now by tapping the `Skip` button twice.

#### Date & time

Manually set the time.

Tap on the `Next` button.

#### Google services

Your preferences may vary.

Use location: Enable

Allow scanning: Disable

Send usage and diagnostic data: Disable

Tap the `Accept` button.

#### Protect your tablet

I would not recommend using Face recognition.

I am choosing pin.

#### Samsung service permissions

Customization Service: Disable

Smart suggestions: Disable

Tap on the `Agree` button. (Which doesn't make sense.)

#### Choose your display mode

Tap on `Dark` mode.

Tap on the `Next` button.

#### Please wait

Wait.

#### You're all set up!

Tap on the `Finish` button.

The tablet now brings you to the default Android home screen.

Installed apps are as follows:

* Samsung
  * Galaxy Shop
  * Voice recorder
  * Contacts
  * Flow
  * Members
  * TV
  * Health
  * Messages
* Google
  * Google
  * Chrome
  * Gmail
  * Maps
  * YouTube
  * Drive
  * Google TV
  * Meet
  * Photos
* Microsoft
  * Microsoft 365
  * OneDrive
  * Outlook
* Play Store
* Store
* Notes
* My Files
* Phone
* Messages
* Internet
* Gaming Hub
* Camera
* Gallery
* Calculator
* Calendar
* Clock
* Settings
* YT Music
* Netflix
* Spotify
* Samsung Free
* Global Goals
* Kids

### adb

`adb` is a command line program to interact with Android based mobile phones. I will start by pairing the device to my computer in case there is a problem with the screen and I need to pull files off of it.

#### Enabling developer mode

* Open the `Settings` app.
* Select the `About tablet` option.
* Tap on the `Software information` option.
* Find the `Build number`. Tap on that several times until it asks for you to enter your pin and says that you enabled developer mode.
* Below `About tablet`, there is now a new option.
* Select the `Developer options` option.
* Enable the `USB debugging` option.
* Exit the settings app.

### Connect to WiFi

### Install F-Droid

* [Download F-Droid](https://f-droid.org/).
* Install F-Droid. You will have to allow installation of APK files through Chrome source.
* Update F-Droid. You will have to allow installation of APK files through F-Droid.
* Install Neo Store, open it, give it all of the permissions it asks for. Open the gear icon, repositories tab, and disable everything except for F-Droid. Back out of the settings, and tap on the refresh icon.
* Install more apps from F-Droid through Neo Store.

### Update the OS

Keep updating until Settings > Software update says, "Your software is up to date."
