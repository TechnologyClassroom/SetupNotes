# Mac Setup

Michael McMahon

## Clean install

- Boot from USB
- Insert flash drive with OSX installer.
- Insert wired keyboard.
- Press the power button, then hold OPTION or ALT when you hear the sound.
- Select usb.
- Wait.
- Install OSX.
- Continue.  Continue.  Agree.  Agree.
- Macintosh HD.  Continue.
- Wait ~24min.
- Don't sign in.
- Continue.
- Skip

## System Preferences

Click the Apple icon in the top left.  System Preferences.

- Dock
  - 50%
  - Check Magnification  75%
- Mission Control
  - Mission control -
  - Application Windows -
  - Show Dashboard -
  - Change all hotcorners to -
- Security & Privacy
  - radio Anywhere > Allow from anywhere
- Energy Saver
  - Unlock to make changes.
    - Schedule...
      - Check Start up or wake Weekdays at 12:30PM
      - Check Shut Down Every Day at 7:50PM
      - OK
- Keyboard > Shortcuts
  - Mission Control Uncheck mission control
  - Accessibility Uncheck all
- Mouse
  - Uncheck Scroll direction: Natural
  - Track speed > fast
- Network
  - Turn Wi-Fi off
  - Advanced options
  - Check Create computer...
  - Check Change Network
  - Check Turn Wi-Fi..
  - Apply
- Sharing
  - Give the computer a name here.
  - Check File sharing
- Users & Groups
  - Make a standard account
    - Login Options
    - Automatic login: standard account
- App Store
  - Check all

Reboot

Click the Apple icon in the top left.

- App Store...
  - Update
  - Update all
  - Download & restart

## Safari Preferences

Safari > Preferences

- General
  - Homepage: khanacademy or another educational webpage
  - Remove history items: manually
  - File Download location: Ask for each download
  - Uncheck Open "safe" file after download
- Autofill
  - Uncheck all
- Passwords
  - Uncheck all
- Search
  - Search DuckDuckGo or Google
- Privacy
  - Check Ask websites not to track me.
- Advanced
  - Check Show full website address
  - Check Show Develop menu in menu bar

## Additional software

Install extra software:

- Audacity
- Avira or Avast
- Blender
- Chrome
- Firefox
- GIMP
- Google Earth
- Inkscape
- Krita
- LibreOffice
- SketchUp
- Synfig Studio
- Xquartz

## Dock

Place everything you want in the dock the way you want it.

Lock the dock

Click on the magnifying glass in the top right, type terminal.  Open terminal.

```defaults write com.apple.Dock contents-immutable -bool true```

```killall Dock```

To unlock, change true to false.
