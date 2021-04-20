# Firefox

Firefox is a great browser with a great philosophy.

Download: https://www.mozilla.org/en-US/firefox/

Source code: https://hg.mozilla.org/mozilla-central/

## Extensions

Extensions have significantly changed since Firefox Quantum.  Some of these may
not work, but may work in the future or with a legacy build.

- Video Downloadhelper allows you to download streaming videos from popular
  websites.  This is very useful for slow Internet connections and preparing for
  presentations.
  https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/
- LibreJS - Actively control the licenses and freedom of your JavaScript while
  browsing.  See [The JavaScript Trap](https://www.gnu.org/philosophy/javascript-trap.en.html)
  for more information.
  https://addons.mozilla.org/en-US/firefox/addon/librejs/
- uMatrix allows you to control the content of your browser.  This will break
  website functionality until properly configured.
  https://addons.mozilla.org/en-US/firefox/addon/umatrix/
- uBlock Origin removes ads and trackers from most webpages.  This is reported
  to decrease your network traffic by about 17% which increases the speed of
  your entire network.
  https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/
- KeePassXC-Browser communicates between KeePassXC to store passwords securely.
  https://addons.mozilla.org/en-US/firefox/addon/keepassxc-browser/
- Privacy Badger blocks tracking between websites and automatically builds your
  blocklist as you browse.
  https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/
- HTTPS Everywhere defaults to using the https version of a website
  https://www.eff.org/https-everywhere
- Dark background light text is a dark theme for webpages.  This will break
  website functionality.
  https://addons.mozilla.org/en-US/firefox/addon/dark-background-light-text/
- DownThemAll (Not available for Firefox Quantum yet) - If you have a list of
  links to files, DTA helps you download all of them with a few clicks.
  https://addons.mozilla.org/en-US/firefox/addon/downthemall/
  https://addons.mozilla.org/en-US/firefox/addon/downthemall-anticontainer/
- FT DeepDark (Not available for Firefox Quantum yet) is a dark theme for
  Firefox.
  https://addons.mozilla.org/en-US/firefox/addon/ft-deepdark/
  A dark theme is now installed by default and can be enabled through settings.

## Troubleshooting

Problem: Google Docs does not support copy and paste.  Reason: This is a
purposeful security implementation as all website could pull from your
clipboard.

Solution: Set your URL bar to this address: ```about:config```

Do a search for clipboard, and change these values to true:

```
clipboard.plainTextOnly
dom.event.clipboardevents.enabled
```