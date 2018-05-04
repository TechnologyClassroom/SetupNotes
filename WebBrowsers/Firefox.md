# Firefox

Firefox is a great browser with a great philosophy.

Download: https://www.mozilla.org/en-US/firefox/

Source code: https://hg.mozilla.org/mozilla-central/

## Extensions

Extensions have significantly changed since Firefox Quantum.  Some of these may
not work, but may work in the future or with a legacy build.

- DownThemAll - If you have a list of links to files, DTA helps you download all
  of them with a few clicks.
  https://addons.mozilla.org/en-US/firefox/addon/downthemall/
  https://addons.mozilla.org/en-US/firefox/addon/downthemall-anticontainer/
- Video Downloadhelper allows you to download streaming videos from popular
  websites.  This is very useful for slow Internet connections and preparing for
  presentations.
  https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/
- uMatrix allows you to control the content of your browser.
  https://addons.mozilla.org/en-US/firefox/addon/umatrix/
- uBlock Origin removes ads and trackers from most webpages.  This is reported
  to decrease your network traffic by about 17% which increases the speed of
  your entire network.
  https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/
- Privacy Badger blocks tracking between websites and automatically builds your
  blocklist as you browse.
  https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/
- HTTPS Everywhere defaults to using the https version of a website
  https://www.eff.org/https-everywhere
- FT DeepDark
  https://addons.mozilla.org/en-US/firefox/addon/ft-deepdark/

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
