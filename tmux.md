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

```CTRL+b ?``` will show all keystrokes.  ```CTRL+b``` is necessary for entering all tmux keystrokes.  After pressing ```CTRL+b```, release both CTRL and b and then press the next key.

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
