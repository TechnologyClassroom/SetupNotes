# Neovim notes

[Website](https://neovim.io/) - [Documentation](https://neovim.io/doc/) - [Source](https://github.com/neovim/neovim) Apache-2.0

Neovim is a hyperextensible Vim-based text editor.

The notes are meant to provide a series of steps, which anyone may follow quickly.

# Installation

## Debian-based systems

```
sudo apt update
sudo apt install -y neovim
```
## Arch

```
sudo pacman -S neovim
```

## Fedora

```
sudo dnf install neovim
```

## Windows

### Scoop

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script the first time
irm get.scoop.sh -outfile 'install-scoop.ps1'
```

Verify install-scoop.ps1 contains what it should.

```
.\install-scoop.ps1
scoop install neovim
```

# Run

Run `nvim` from the command line usually with a filename after.

    nvim file.txt

# Exit

To save and exit, use esc key, `:wq`, and the enter key. `w` stands for write. `q` stands for quit.

To quit without saving, use `:q!` instead.

# Learning how to use neovim

Once inside `nvim` type `:Tutor` and enter to start the tutorial.

# Configuration

Note that settings of neovim are kind of personal and do not just copy others settings without understanding how things work. Using neovim without any configuration is fine and might be preferable if you find yourself working on remote systems often.

My simple neovim config is in [dotfiles](https://github.com/TechnologyClassroom/dotfiles/blob/master/nvim.rc).

Another neovim config with Lazy.nvim [dotfiles](https://github.com/wujackwill/nvim)

## Additional sources

* YouTube
  * [Theprimeagen on lua configuration of Neovim](https://www.youtube.com/watch?v=w7i4amO_zaE&t=589s)
