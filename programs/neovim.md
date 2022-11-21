# Neovim notes

[Website](https://neovim.io/) - [Documentation](https://neovim.io/doc/) - [Source](https://github.com/neovim/neovim) Apache-2.0

Neovim is a fantastic tool for writing, programming, and system administration.

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

# Configuration

Note that settings of neovim are kind of personal and do not just copy others settings without understanding how things work. Using neovim without any configuration is fine and might be preferable if you find yourself working on remote systems often.

## If you prefer vim script

```
cd  ~/.config
mkdir nvim
nvim init.vim
```

## vim-plug

[Website](https://github.com/junegunn/vim-plug)

vim-plug is a plugin manager for neovim.

```
# Installation of plug manager: vim-plug
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

For global install, mv the the `plug.vim` file into the `/usr/share/nvim/runtime/autoload/` directory.

Example `~/.config/nvim/plug` file:

```
call plug#begin('~/.config/nvim/plug')

Plug 'iamcco/markdown-preview.nvim', { 'do': 'cd app && yarn install' }
Plug 'itchyny/lightline.vim'
Plug 'gruvbox-community/gruvbox'
Plug 'nvim-lua/plenary.nvim'
Plug 'nvim-telescope/telescope.nvim'
Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}
Plug 'frazrepo/vim-rainbow'
Plug 'chun-yang/auto-pairs'
Plug 'luochen1990/rainbow'
Plug 'dhruvasagar/vim-table-mode'
Plug 'neoclide/coc.nvim', {'branch': 'master', 'do': 'yarn install --frozen-lockfile'}
Plug 'mbbill/undotree'
Plug 'Shougo/unite.vim'
Plug 'rafaqz/citation.vim'
Plug 'godlygeek/tabular'
Plug 'preservim/vim-markdown'
Plug 'sirver/ultisnips'
Plug 'honza/vim-snippets'
call plug#end()
```

```
and press <ESC> input ':source %' to source the file.
then press <ESC> input ':PlugInstall' to install the plug
```

## Additional sources

* YouTube
** [Theprimeagen on configuration](https://www.youtube.com/watch?v=DogKdiRx7ls&t=1250s)
** [Theprimeagen on lua configuration](https://www.youtube.com/watch?v=x2QJYq4IX6M&t=76s)
