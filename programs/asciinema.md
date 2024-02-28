# asciinema

`asciinema` records your terminal session.  This is especially useful for going back and writing documentation for a process or showing someone else a procedure asynchronously.  The name is a combination of `ascii` and `cinema`.

Another practical use case: An intern wanted to see an upgrade process.  Scheduling was difficult.  A security update came and the issue was pressing.  I made a cast file and emailed it to them with instructions.  They still got to see the upgrade even though we could not coordinate a good time for us both.

[Website](https://asciinema.org/)

[GitHub and basic documentation](https://github.com/asciinema/asciinema)

## Install

Install with apt on Debian based operating systems:

    sudo apt update && sudo apt install -y asciinema

Install/upgrade with `cargo`:

    cargo install --git https://github.com/asciinema/asciinema

### Config file

[Config documentation](https://github.com/asciinema/asciinema#configuration-file)

Config file goes here: `$HOME/.config/asciinema/config`

If you are paranoid about accidentally uploading casts to their website, you could set these configs and uploads should not work:

```
[api]
; Override URL environment variable to make sure that
; cast files are not uploaded to their server.
asciinema_api_url = 127.0.0.1
url = 127.0.0.1
```

## Record

### Record locally

Record a session without uploading it to their website. I would suggest using a filename that is descriptive about what you are doing such as `drupalupgrade.cast`.

    asciinema rec FILENAME.cast

Record a session without uploading it to their website with a date stamp.

    asciinema rec FILENAME$(date +%Y-%m-%d).cast

`asciinema` will drop you into a new shell.  Exit the shell with `exit` or `CTRL + d` to stop the recording.

Controls: Temporarily pause asciinema recording with `Ctrl + p`.  This allows executing secret commands during the recording session or pasting secrets such as passwords.  Resume the recording with `Ctrl + p` again.

`asciinema` can record the entire terminal session and what is displayed by text editors and terminal multiplexers including `tmux` or `screen`, but the terminal multiplexers must be started after `asciinema`.

### Record locally and upload

    asciinema rec

Note: Nothing will be published without consent and a prompt asks if you want to upload.

## Playback

Controls: Playback can be paused/resumed with `space` key.  When paused, `.` will step through the recording frame by frame.  `CTRL + c` will stop the playback.

Playback at normal speed (BOOOOORRRRRING):

    asciinema play /path/to/FILENAME.cast

Playback with a idle limit of 2 seconds (MUCH BETTER): 

    asciinema play -i 2 FILENAME.cast

Playback with triple speed (WHOA THAT'S FAST!):

    asciinema play -s 3 FILENAME.cast

Playback from the asciinema website:

    asciinema play https://asciinema.org/a/99999999999999999999

## Sharing cast files

Note: Do not upload any secrets.

If you want to share the asciinema recording with the general public, you can upload it to their website with this command:

    asciinema upload FILENAME.cast

If you only need to share a recording with one person, you could also email the cast file and give them instructions on how to install `asciinema` and playback the file.

# Alternatives to asciinema

## script and scriptreplay

[Tutorial from Seth Kenlon](https://www.redhat.com/sysadmin/record-terminal-script-scriptreplay)

## VHS

VHS is a similar project written in Go that is built to generate gifs from terminal.  <https://github.com/charmbracelet/vhs>
