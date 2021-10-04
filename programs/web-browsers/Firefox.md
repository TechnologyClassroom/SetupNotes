# Firefox

Firefox is a great browser with a great philosophy.

Download: https://www.mozilla.org/en-US/firefox/

Source code: https://hg.mozilla.org/mozilla-central/

There are several Mozilla based browsers that are also worth checking out such
as [abrowser](https://trisquel.info/en/wiki/abrowser-help),
[icecat](https://www.gnu.org/software/gnuzilla/), and
[LibreWolf](https://librewolf-community.gitlab.io/).

## Extensions

Extensions have significantly changed since Firefox Quantum.  Some of these may
not work, but may work in the future or with a legacy build.

## Firefox based browser extensions

Extensions can make Firefox based browsers highly configurable.

### Style

* [DarkReader](https://addons.mozilla.org/en-US/firefox/addon/darkreader/)
  attempts to make dark themes for all websites.  This breaks pages often, but
  can be much easier on your eyes.  Can slow your system down.
* [Stylus](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) can
  customize CSS on individual pages or domains.
* [Matte Black (Red)](https://addons.mozilla.org/en-US/firefox/addon/matte-black-red/)
  is a dark theme for the browser menu bars.

### Privacy/Security
* [JShelter](https://jshelter.org/) minimizes harm caused by JavaScript.  [FSF Blog post about JShelter](https://www.fsf.org/news/fsf-announces-jshelter-browser-add-on-to-combat-threats-from-nonfree-javascript)
* [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/)
  selectively blocks JavaScript by domain.
* [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
  removes most ads and trackers from most webpages.  This is reported to
  decrease your network traffic by about 17% which increases the speed of your
  entire network.
* [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/)
  blocks tracking between websites and automatically builds your blocklist as
  you browse passively.
* [HTTPS Everywhere](https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/)
  goes to the `https` page automatically instead of `http`.
* [AdNauseum](https://addons.mozilla.org/en-US/firefox/addon/adnauseam/) blocks
  ads and clicks on all of the ads to confuse advertisers.
* [Third-party request Blocker](https://addons.mozilla.org/en-US/firefox/addon/tprb/)
  blocks third-party domains.
- [uMatrix](https://addons.mozilla.org/en-US/firefox/addon/umatrix/) allows you
  to control the content of your browser.  This will break website
  functionality until properly configured.  uMatrix is not necessary if you use
  NoScript.
- [KeePassXC-Browser](https://addons.mozilla.org/en-US/firefox/addon/keepassxc-browser/)
  communicates between KeePassXC to store passwords securely.  I would suggest
  not saving passwords in your browser or using this extension, but this is
  preferable if you are too lazy to copy and paste passwords from KeePassXC.

### Ethical
* [Privacy Redirect](https://addons.mozilla.org/en-US/firefox/addon/privacy-redirect/)
  can redirect pages to AGPL alternatives such as Twitter to Nitter.
* [LibreJS](https://www.gnu.org/software/librejs/) blocks JavaScript unless the
  they have LibreJS compatible license information.  This actively control the
  licenses and freedom of your JavaScript while browsing.  This breaks most
  websites that use JavaScript.  See
  [The JavaScript Trap](https://www.gnu.org/philosophy/javascript-trap.en.html)
  for more information.
* [Cloud firewall](https://addons.mozilla.org/en-US/firefox/addon/cloud-firewall/)
  can block domains by their hosting provider.  You could block all Microsoft
  and Azure sites for example.

### Utility
- [Video Downloadhelper](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)
  allows you to download streaming videos from popular websites.  This is very
  useful for archival, slow Internet connections, and preparing for
  presentations.
* [New Tab Override](https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/)
  sets the page that opens when you open a new tab.  Great to enable before
  giving a presentation.  Set it to `about:blank` for example.
* [Cookie Quick Manager](https://addons.mozilla.org/en-US/firefox/addon/cookie-quick-manager/)
  backup or restore cookies.
* [Link Gopher](https://addons.mozilla.org/en-US/firefox/addon/link-gopher/)
  extracts all links from a page.
* [DownThemAll](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)
  downloads files in bulk.  If you have a list of links to files, DTA helps you
  download all of them with a few clicks.
    * [DownThemAll-Anticontainer](https://addons.mozilla.org/en-US/firefox/addon/downthemall-anticontainer/)
* [User-Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/uaswitcher/)
  changes the user-agent string that you send to websites.
* [CORS Everywhere](https://addons.mozilla.org/en-US/firefox/addon/cors-everywhere/)
  can enable CORS everywhere by altering http responses.
* [Pinger](https://addons.mozilla.org/en-US/firefox/addon/pinger/) checks a
  page for broken links.

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
