# tmux notes

[tmux](https://github.com/tmux/tmux/wiki) is a small terminal multiplexer that
greatly enhances the terminal for GNU/Linux and macOS.

## Install tmux

tmux is available for most GNU/Linux distros and can be easily downloaded with a
simple command.

Debian based systems

```
apt-get install -y tmux
```

Red Hat based systems

```
yum install -y tmux
```

## Starting tmux

Start tmux.

```
tmux
```

A green bar will appear on the bottom of the terminal.

## List all keystrokes

`CTRL+b ?` will show all keystrokes. `CTRL+b` is necessary for entering
all tmux keystrokes. After pressing `CTRL+b`, release both CTRL and b and
then press the next key. `q` will quit help and revert back to the previous
terminal pane.

## Page up

When you are in a TTY, the information above the current view is gone after new
information pushes it out of the way. This information can be viewed if you
sent that data to a log file or piped with less, but that requires prior
planning.

tmux allows you to page up and down.

`CTRL+b Page Up` enters copy mode. This allows you to use the page up and
down keys to view more of the previous output. `q` will quit copy mode and
revert back to the previous terminal pane.

Once you are in copy mode, you can go all the way to the top with the `ALT+<`
keystroke and all the way to the bottom with the `ALT+>` keystroke.

## Preserve work during remote connections

This is also very useful if you want to share a screen with two people that both
have SSH access to the same server. Even if you are in the same room, this is
preferred to looking over a physical shoulder.

If you are familar with SSH connections, you have probably ran into the scenario
where you were working on a long process and lost connection or closed the
terminal window. The process cancels at that point on the remote server and can
be very tedious to clean up.

tmux can fix this scenario. SSH into a remote server, install tmux, and run
tmux. If you lose connection or close the terminal, SSH back in and run

```
tmux attach
```

Your tmux session will be exactly as you left it.

You can also run this abbreviation to do the same thing.

```
tmux a
```

You can also use the keystroke `CTRL+b, d` to disconnect purposefully if you want
to leave a long process running in the background.

## tmux in tmux

![Screenshot](https://github.com/TechnologyClassroom/SetupNotes/blob/master/Images/tmux.jpg?raw=true "Screenshot")

When you have tmux inside of tmux, use `CTRL+b` twice to control the inside
instance of tmux. This is useful when you are using tmux on your workstation to
ssh into a remote system with tmux in case you lose your connection.

For example, if you want to split a window horizontally inside of tmux inside of
tmux, use `CTRL+b CTRL+b "` or `CTRL+bb "`.

![Screenshot](https://github.com/TechnologyClassroom/SetupNotes/blob/master/Images/tmux2.png?raw=true "Screenshot")

In this image, I am using my host machine with tmux to ssh into two different
machines that also have tmux.

## Splitting windows

`CTRL+b "` will split the window into two shells one on top of the other.

`CTRL+b %` will split the window into two shells side by side.

`CTRL+b up arrow key` Change focus to the pane above the current position.

`CTRL+b down arrow` Change focus to the pane below the current position.

`CTRL+b left arrow key` Change focus to the pane on the left of the current
position.

`CTRL+b right arrow key` Change focus to the pane on the right of the
current position.

Windows can be closed with `exit` or the `CTRL+b x` keystroke.

## Resize pane

`CTRL+b CTRL+up arrow key` Resize the current pane by expanding the top
edge.

`CTRL+b CTRL+down arrow` Resize the current pane by expanding the bottom
edge.

`CTRL+b CTRL+left arrow key` Resize the current pane by expanding the left
edge.

`CTRL+b CTRL+right arrow key` Resize the current pane by expanding the right
edge.

## Zoom or fullscreen one pane

`CTRL+b z` Resize the current pane to fullscreen.

`CTRL+b z` Revert fullscreen changes to their original state.

## Customize your tmux configuration

Stick with the defaults until you know what you would like to change. Create a
new file and add more binding.

```
nano ~/.tmux.conf
```

My config can be found
[here](https://github.com/TechnologyClassroom/dotfiles/blob/master/tmux.conf).
Example configurations can be found in the `/usr/share/doc/tmux/examples`
directory.

Reload a new config in an active session with
`CTRL+b :source-file ~/.tmux.conf`.

## Customize the colors of tmux on different machines

I ssh into several different servers on a regular basis. I keep my workstation
on the default tmux colors. I change my production server to bright warm
colors. I change my development server to cool colors.

Example .tmux.conf files for color
[Solarized color palette](https://github.com/altercation/solarized/tree/master/tmux)

Display all of the standard tmux colors using this one-liner:

```
for i in {0..255}; do printf "\x1b[38;5;${i}mcolor%-5i\x1b[0m" $i ; if ! (( ($i + 1 ) % 8 )); then echo ; fi ; done
# From 12431234123412341234123 at https://superuser.com/questions/285381
```

## Start tmux with your terminal

Add these lines to your .bashrc file:

```
# Run tests and run tmux automatically. Connect to an existing session if it is available.
# From George Udosen, yosefrow, hzh, AdminBee, and user7089 at https://unix.stackexchange.com/a/490830
if command -v tmux &> /dev/null && [ -n "$PS1" ] && [[ ! "$TERM" =~ screen ]] && [[ ! "$TERM" =~ tmux ]] && [ -z "$TMUX" ]; then
  tmux a -t default || exec tmux new -s default && exit;
fi
```

This does not work if you are SSHing from a machine that is already running tmux. I SSHed into a terminal session for a job interview once and they must have had something similar setup, but they did not expect me to already be running tmux. If that scenario happens, you can run `tmux a` to connect to an existing tmux or `tmux` to start a new session.

## Sync panes

synchronize-panes is useful for manually making one change to many servers at once.
Ansible, Puppet, and other configuration managers are better at scale, but this
is useful for two or three quick changes.

1. SSH into as many servers as you want to change in separate panes.
2. Synchronize panes
   `CTRL+b :set-window-option synchronize-panes on`
3. Type commands into all windows at once.
4. Turn off synchronize panes
   `CTRL+b :set-window-option synchronize-panes off`

This can be added to a keybind with a
[custom config](https://github.com/TechnologyClassroom/dotfiles/blob/master/tmux.conf).

## Load predefined tmux layouts with shell scripts

I have three typical tmux layouts that I commonly use. Instead of a manual
workflow such as open tmux, split window, change pane, split window, change
pane, and get started, I launch tmux with a shell script. These shells scripts
can be launched with my window manager session init.

- [tmux.sh](https://github.com/TechnologyClassroom/bash/blob/master/tmux.sh) has
  three panes. One long on the left. Two on the right. The monitoring tool
  top runs in the bottom right automatically.
- [tmux2.sh](https://github.com/TechnologyClassroom/bash/blob/master/tmux2.sh)
  has three panes. One wide on top. Two on the bottom. The monitoring tool
  top runs in the bottom left automatically. This is my personal favorite.
- [tmux4.sh](https://github.com/TechnologyClassroom/bash/blob/master/tmux4.sh)
  has four panes.

## Break and join panes

A pane can be disconnected into the background with `CTRL+b !`.

A pane can be brought back with `CTRL+b :join-pane -s :0`

## Copy and paste text

Copying and pasting text with the mouse or keyboard can be frustrating and
difficult to keep track of at times. Why buffer did I have that saved in?
Will the paste add trailing spaces? tmux copy mode can be confusing too, but
it generally does not have trailing spaces at least.

For this practical example, I will be copying some SSH public keys. Start by
printing a file with cat.

```
cat ~/.ssh/authorized_keys
```

`CTRL+b [` enters copy mode.

Navigate to the text that you want to copy with the arrow keys or however you
navigate.

`CTRL+SPACE` starts highlighting.

Navigate to the other side of the text that you want to copy with the arrow
keys or however you navigate. Make sure that all that you want to copy is
highlighted with a different color. If you need to try again, press `ESC` to
start over.

`ALT+w` copies the highlighted text to a tmux copy buffer.

Get into a position where you want to paste such as another terminal that you want to paste all of those SSH public keys to.

```
ssh user@192.168.50.80
mkdir -p ~/.ssh
vim ~/.ssh/authorized_keys
# Press i to get into insert mode in vim.
```

`CTRL+b ]` pastes.

Then save the file. `ESC` `:wq` saves and quites from `vim`.
