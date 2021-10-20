# Argos Translate

[Website](https://www.argosopentech.com/)

[GitHub](https://github.com/argosopentech/argos-translate)

[FSD](https://directory.fsf.org/wiki/Argos_Translate)

Argos Translate is a free software translation tool that runs offline and can translate 20+ languages into English.  Argos Translate acts as a free alternative to Google Translate.

A self-hosted version exists as [LibreTranslate](https://directory.fsf.org/wiki/LibreTranslate), but can be run without SaaS very easily.

## Install

Argos Translate was very simple to install if you have `pip3`.

    python3 -m pip install argostranslate

Run the GUI version of Argos Translate.

    argos-translate-gui

I prefer to add this line to my `~/.bashrc` file so less typing is required.

    alias translate='argos-translate-gui'

## Language pairs

Language pairs are approximately 100MB each.

### Installing new pairs through the GUI

1. Open Argos Translate: `argos-translate-gui`
1. Click on the `Manage Packages` menu item.
1. Click on the `Download packages` button.
1. Click on the down arrow beside a language pair that you want to add.
1. Wait for the hourglass icon to change into a check mark icon.
1. Repeat the last two steps until you have all of the language pairs that you want.
1. Click on the `X` in the top right to close the `Download packages` window.
1. Click on the `X` in the top right to close the `Manage Packages` window.

Note: The `Download packages` screen does not seem to have a scroll bar so you will probably need to follow the next set of instructions to import new pairs through the GUI.

### Importing new pairs through the GUI

1. Download or make new pairs.  Model links can be downloaded from [this JSON file](https://raw.githubusercontent.com/argosopentech/argospm-index/main/index.json) without JavaScript or [this page](https://www.argosopentech.com/argospm/index/) with trivial nonfree JS.
1. Open Argos Translate: `argos-translate-gui`
1. Click on the `Manage Packages` menu item.
1. Click on the `Install package file` button.
1. Navigate to where you downloaded the new language pairs, click on the `.argosmodel` file, and click on the `Open` button.
1. Repeat the last two steps until you have all of the language pairs that you want.
1. Click on the `X` in the top right to close the `Manage Packages` window.

### Removing a pair

1. Open Argos Translate: `argos-translate-gui`
1. Click on the `Manage Packages` menu item.
1. Click on the trash can icon besides the pair you want to remove.
1. Click on the `X` in the top right to close the `Manage Packages` window.

## Usage

Languages are chosen as drop down choices.

The left text box translates into the right box.

Example workflow translating from Vietnamese into English:

1. Set the left drop down to `Vietnamese` and the right drop down to `English`.
1. Replace the default text `Text to translate from` in the left text box with some text in Vietnamese.  A quick way to do this is to click in the left text box and press the keyboard shortcut `CTRL+a`.
1. Wait patiently.
1. When text appears in the right text box, read it.

If the output looks similar to the input, try changing the origin language as some languages appear similar if you are unfamiliar with them.
