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

Settings > Connections > Wi-Fi

Select your network, enter your password, and get connected.

### Update the OS

Settings > Software update > Download and install

While waiting for the download, you can continue on.

Keep updating until Settings > Software update says, "Your software is up to date."

### Install F-Droid

* Open Chrome
  * Select `Use without an account` option.
  * At the ad privacy settings prompt, select the `Settings` button.
  * Select `Ad topics` and disable the `Ad topics` option. Tap on the back arrow.
  * Select `Site-suggested ads` and disable the `Site-suggested ads` option. Tap on the back arrow.
  * Select `Ad measurement` and disable the `Ad measurement` option. Tap on the back arrow.
* In the URL bar, enter `fdroid.org` and tap enter.
* [Download F-Droid](https://f-droid.org/). There may be a warning that the file may be harmful and tap on the `Download anyway` button.
* After the download has finished, tap on the `Open` button.
* It will give another warning that your phone currently isn't allowed to install unknown apps from this source. Tap on the `Settings` button.
* Enable `Allow permission` option to be able to install apk files from Chrome.
* Tap on the `Install` button to install F-Droid.
* Another warning will open that F-Droid was built for an older version of Android. Tap more details and `Install anyway` option and enter your password.
* Open F-Droid once it is installed. Give it any permissions it asks for such as sending notifications.
* Go to the Updates tab, and update F-Droid. You will have to allow installation of APK files through F-Droid.
* It will give another warning that your phone currently isn't allowed to install unknown apps from this source. Tap on the `Settings` button.
* Enable `Allow permission` option to be able to install apk files from Chrome.
* Tap on the `Update` button to update F-Droid.
* Open F-Droid again, tap on the `Latest` tab and search for `Neo Store`.
* Install Neo Store, open it, give it all of the permissions it asks for. Open the gear icon, repositories tab, and disable everything except for F-Droid. Back out of the settings, and tap on the refresh icon.
* Install more apps from F-Droid through Neo Store such as Mull, VLC, OSMAnd, Markor, Hacker's Keyboard, Termux, Dicio, and Luanti.

### Configure Firefox

* Set as default browser.
* Add widget.
* Tap `Not now` when asked about syncing between devices.
* Tap `Turn on notifications` option. Tap the `Allow` button.
* Tap on the ellipsis and the `Extensions` option.
* Install `uBlock Origin` and `Dark Reader` extensions. Allow them in private browsing and tap on the `Add` and `OK` buttons.
* Tap on `uBlock Origin` and tap on the `Settings` option. Tap on the `Filter lists` tab. Enable both `Cookie notices` lists. Expand `Annoyances` > `EasyList - Annoyances` and enable `EasyList - Chat Widgets` lists. Expand `AdGuard - Annoyances` and enable `Mobile App Banners` and `Popup overlays` lists. Tap on the `Update now` button. Close the `uBlock Origin` settings tab.

### Configure OSMAnd

Start the app and download the map of the place where you are.

### Retro Games

(Optionally) install RetroArch through Mull.

### Rearrange icons
