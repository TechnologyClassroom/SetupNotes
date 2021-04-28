# Thunderbird/Icedove notes

Mozilla Thunderbird or Icedove is a great free and open source email program and
works for GNU/Linux, Mac, and Windows.

https://www.mozilla.org/en-US/thunderbird/

https://wiki.debian.org/Icedove

## Add-ons

- TT DeepDark - Elegant dark theme for Thunderbird based on FF DeepDark.  In my
  opinion this is easier on the eyes.
  https://addons.mozilla.org/en-US/thunderbird/addon/tt-deepdark/
- QuickText - Quickly retrieve your commonly used text blocks with a keystroke.
  I often copy and paste blocks of text for my work.
  https://addons.mozilla.org/en-US/thunderbird/addon/quicktext/
- Send Later - Queue emails to send at reasonable, professional hours with Send
  Later.  Alternative to "Boomerang for Gmail" without giving your login details
  to strangers.
  https://addons.mozilla.org/en-US/thunderbird/addon/send-later-3/
- EnigMail - Adds encryption options to Thunderbird
  https://addons.mozilla.org/en-US/thunderbird/addon/enigmail/
- Paranoia - Shows who read your email in transit.
  https://addons.mozilla.org/en-US/thunderbird/addon/paranoia/
- Markdown Here - Write emails in markdown and convert before sending. 
  https://addons.mozilla.org/en-US/thunderbird/addon/markdown-here-xul/
- ThunderHTMLEdit - Adds the ability to edit the html of an email directly in
  the compose window.
  https://addons.mozilla.org/en-US/thunderbird/addon/thunderhtmledit/

## Adding an email signature

- Menu Icon (Sandwich) > Hover over the arrow to the right of Preferences >
  Account Settings
- Click on the email address in the left side to bring up the options for that
  address.
- In the `Signature test:` box add your email signature.
- Repeat the last two steps for any other email addresses you may want to
  configure.
- Click on the `OK` button.

## Remove the dashes before your email signature

From https://support.mozilla.org/en-US/questions/1019583

- Menu Icon (Sandwich) > Preferences > Preferences > Advanced > General tab
- Click on the "Config Editor..." button.
- Click on the "I accept the risk!" button.
- In top search, type: ```separator```
- Look for the entry:
  ```mail.identity.default.suppress_signature_separator; false```
- Double click to toggle ```false``` to ```true```.
- Close config editor with CTRL+W.
- Click on the "Close" button to save changes.

## Move signature above quoted text for replies and forwards

From http://www.pctips4u.com/2016/10/add-email-signature-above-quoted-text.html

- Menu Icon (Sandwich) > Preferences > Account Settings > Composition &
  Addressing
- Use the ```[...] and place my signature:``` pull down box to change: ```below
  the quote (recommended)``` to ```below my reply (above the quote)```
- Click on the "OK" button to save changes.

## Open links in the browser of your choice

Problem: I have to use Google Chrome for many of the websites I need at work.
On Ubuntu, Thunderbird would open a new Chrome window and would not open the
link.

Based on Vitaly Kazakov and Kevin Bowen at
https://askubuntu.com/questions/130158

- Menu Icon (Sandwich) > Preferences > Preferences > Advanced > General tab
- Click on the "Config Editor..." button.
- Click on the "I accept the risk!" button.
- In top search, type: ```network.protocol-handler.warn-external.```
- Look for the entries:

```
network.protocol-handler.warn-external.ftp; false
network.protocol-handler.warn-external.http; false
network.protocol-handler.warn-external.https; false
```

- Double click each of them to toggle ```false``` to ```true```.
- Close config editor with CTRL+W.
- Click on the "Close" button to save changes.
- Send an email to yourself with ftp, http, and https links.
- Click on one of the links.
- Click on the ```Choose...``` button.
- Navigate to ```/opt/google/chrome/google-chrome``` or the location of the
  browser of your choice.
- Click on the ```Open``` button.
- Check the ```Remember my choice for X links.``` box.
- Click on the ```Open Link``` button.
- If the link opens correctly, repeat the last seven steps until ftp, http, and
  https are configured.

## Message Filters and Folders

I would recommend creating local folders and using `Message Filters` to sort
incoming mail into different categories.

After years of use, Thunderbird/IceDove does slow down.  Purging old mailing
list archives and subscriptions every once in a while helps which can be
automated through `Message Filters`.

Example filter to delete a mailing list after ~2 months:

`Match all of the following`
`From, To, CC, or BCC` `contains` MAILINGLISTADDRESSHERE
`Age in Days` `is greater than` `60`
Perform these actions:
`Delete Message`
