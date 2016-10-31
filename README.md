# mac-setup

These are some of the things I install when I setup a Mac for the first time. It's not automated because how often do you do this?

## The Basics

```sh

# brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# xcode select
xcode-select --install

# brew packages
brew install wget curl git python ruby macvim vim

# node
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
nvm install node

# casks
brew cask install \
  google-chrome \
  iterm2 \
  skype \
  vlc \
  keepingyouawake \
  sublime-text \
  1password

```

## SSH

```
ssh-keygen -t rsa -b 4096 -C "adam@admm.io"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

You can then `pbcopy < ~/.ssh/id_rsa.pub` and add your new SSH key to [Github](https://github.com/settings/keys)

## Sublime

First install [Sublime Package Manager](https://packagecontrol.io/installation) and then update _Package Control.sublime-settings_:

```json
{
	"bootstrapped": true,
	"in_process_packages":
	[
	],
	"installed_packages":
	[
		"Babel",
		"ColorPicker",
		"DocBlockr",
		"Emmet",
		"Git",
		"GitGutter",
		"HTML-CSS-JS Prettify",
		"Oceanic Next Color Scheme",
		"Package Control",
		"SideBarEnhancements",
		"SublimeLinter",
		"SublimeLinter-contrib-eslint"
	]
}
```

## NPM

These are some global packages that I use frequently:

```
npm install create-react-app nodemon babel-cli
```

## Vim

First install Vundle

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

Update `~/.vimrc`, heres something super basic:

```
set nocompatible              " be iMproved, required
filetype off                  " required

" Vundle stuff
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'
Plugin 'pangloss/vim-javascript'
Plugin 'mxw/vim-jsx'

" All of your Plugins must be added before the following line
call vundle#end()            " required

filetype plugin indent on    " required

syntax on
colorscheme evening 

let g:jsx_ext_required = 0
```

Then install the plugins: `vim +PluginInstall +qall`
