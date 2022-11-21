# Neovim notes

Neovim is a fantastic tool for writing and even coding after proper setting.

The notes are meant to provide serious of steps, which anyone may follow by just    
copying and paste without suffering from hours of tutorials online.

**What is worthy noticing is that settings of neovim is kind of personal and don't just copy others settings without understanding how things work.**

***The notes are mainly for ubuntu but I will steps are more or less likely on other GNU/Linue distro or even Windows(which is not recommended for privacy issues)***

# Installation

## Ubuntu/Debian based
```
for unstable version of neovim
sudo add-apt-repository ppa:neovim-ppa/unstable

for stable version of neovim
sudo add-apt-repository ppa:neovim-ppa/stable

sudo apt-get update
sudo apt-get install neovim
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

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script the first time
irm get.scoop.sh | iex
scoop install neovim
```

# Configuration    

## If you prefer vim script

```
cd  ~/.config
mkdir nvim
nvim init.vim
```

```
# installation of plug manager: vim-plug
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'       

# somehow this won't work on any of my OS. So I just manually dowloand the plug.vim file.

And put the plug.vim file into my /usr/share/nvim/runtime/autoload file

The file can be found at https://github.com/junegunn/vim-plug.
```

```
# put these in your init.vim file and these are just some exmaples.
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

## Further settings 

Actually, the configuration of neovim or vim is super personal.

But there are some excellent tutorials on ***youtube***

I highly recommand **Theprimeagen** and the video below 

https://www.youtube.com/watch?v=DogKdiRx7ls&t=1250s


## If you prefer lua

The lua version of configurations of lua is kind of complicated to cover in just 
one markdown file but it is actually  more straightforward and easy-to-understand when one has many lines of configurations.

Again, I hignly recommend **Theprimeagen** and another viedo below where he makes outstanding illustrations of how these things work.

https://www.youtube.com/watch?v=x2QJYq4IX6M&t=76s
