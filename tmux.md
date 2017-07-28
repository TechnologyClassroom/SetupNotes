# tmux

<a href="https://github.com/tmux/tmux/wiki">tmux</a> is a small terminal multiplexer that greatly enhances the terminal for GNU/Linux and macOS.

# Install tmux

tmux is available for most GNU/Linux distros and can be easily downloaded with a simple command.

Debian based systems

```
apt-get install -y tmux
```

Red Hat based systems

```
yum install -y tmux
```

# Starting tmux

Start tmux.

```
tmux
```

A green bar will appear on the bottom of the terminal.

# List all keystrokes

```CTRL+b ?``` will show all keystrokes.  ```CTRL+b``` is necessary for entering all tmux keystrokes.  After pressing ```CTRL+b```, release both CTRL and b and then press the next key.  ```q``` will quit help and revert back to the previous terminal pane.

# Page up

When you are in a TTY, the information above the current view is gone after new information pushes it out of the way.  This information can be viewed if you sent that data to a log file or piped with less, but that requires prior planning.

tmux allows you to page up and down.

```CTRL+b Page Up``` enters copy mode.  This allows you to use the page up and down keys to view more of the previous output.

# Splitting windows

```CTRL+b "``` will split the window into two shells one on top of the other.

```CTRL+b %``` will split the window into two shells side by side.

```CTRL+b up arrow key``` Change focus to the pane above the current position.

```CTRL+b down arrow``` Change focus to the pane below the current position.

```CTRL+b left arrow key``` Change focus to the pane on the left of the current position.

```CTRL+b right arrow key``` Change focus to the pane on the right of the current position.

# Resize pane

```CTRL+b CTRL+up arrow key``` Resize the current pane by expanding the top edge.

```CTRL+b CTRL+down arrow``` Resize the current pane by expanding the bottom edge.

```CTRL+b CTRL+left arrow key``` Resize the current pane by expanding the left edge.

```CTRL+b CTRL+right arrow key``` Resize the current pane by expanding the right edge.

# Customize your tmux configuration

Stick with the defaults until you know what you would like to change.  Create a new file and add more binding.

```
nano ~/.tmux.conf
```

My config can be found <a href="https://github.com/TechnologyClassroom/dotfiles/blob/master/tmux.conf">here</a>.  Example configurations can be found in the ```/usr/share/doc/tmux/examples``` directory.

Reload a new config in an active session with ```CTRL+b :source-file ~/.tmux.conf```.

# Load predefined tmux layouts with shell scripts

I have three typical tmux layouts that I commonly use.  Instead of manually workflow such as open tmux, split window, change pane, split window, change pane, and get started, I launch tmux with a shell script.  These shells scripts can be launched with my window manager session.

<a href="https://github.com/TechnologyClassroom/bash/blob/master/tmux.sh">tmux.sh</a> has three panes.  One long on the left.  Two on the right.  The monitoring tool top runs in the bottom right automatically.

<a href="https://github.com/TechnologyClassroom/bash/blob/master/tmux2.sh">tmux2.sh</a> has three panes.  One wide on top.  Two on the bottom.  The monitoring tool top runs in the bottom left automatically.  This is my personal favorite.

<a href="https://github.com/TechnologyClassroom/bash/blob/master/tmux4.sh">tmux4.sh</a> has four panes.