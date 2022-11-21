# Zotero notes

[Website](https://www.zotero.org/) - [Documentation](https://www.zotero.org/support/) - [Source](https://github.com/zotero/zotero) AGPLv3

Zotero is a helpful tool for keeping track of papers and sources especially for academic writing.
These notes cover the installation of Zotero for Debian-based systems and highlight some plugins.

## Installation

For general support, visit the [Installation](https://www.zotero.org/support/installation) page of
the Zotero Documentation.

```
sudo apt install -y curl
curl -o zotero-install.sh https://raw.githubusercontent.com/retorquere/zotero-deb/master/install.sh
echo "Check that zotero-install.sh is what it should be."
pause
sudo bash zotero-install.sh
sudo apt update
sudo apt install -y zotero
```

## Recommended Plugins

* [Better Bittex For Zotero(extermly helpful)](https://retorque.re/zotero-better-bibtex/)
* [DOI manager](https://github.com/bwiernik/zotero-shortdoi)
* [Jasminum](https://github.com/l0o0/jasminum/releases)
* [Sci-hub Plugin for zotero](https://github.com/ethanwillis/zotero-scihub)
* [Zotfile](http://zotfile.com/)

Find the .xpi file of each plugin and install them on Zotero.
