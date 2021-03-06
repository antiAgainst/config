macOS Environment Setup
=======================

### Generate SSH Key

```sh
ssh-keygen -t rsa -b 4096 -C "MacBook Pro"
```

### Install Homebrew

```sh
# Following https://brew.sh/ for updated instructions
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install essential tools

```sh
brew install tmux macvim neovim
brew install cmake ninja
brew install htop tree wget
brew install fasd rtags ripgrep
brew install bash go pyenv rbenv
brew install exiftool

brew tap sbdchd/skim
brew install sbdchd/skim/skim
# Or use the following command to also install sk-tmux
git clone --depth 1 git@github.com:lotabout/skim.git $HOME/.skim && $HOME/.skim/install

cargo install lsd
```

### Clone configuration repo

```sh
cd
git clone git@github.com:antiagainst/dotfiles.git .dotfiles
git clone --recursive git@github.com:antiagainst/prezto.git .zprezto
```

### Setup Zsh configuration

```sh
# Launch Zsh
zsh

# Copying the Zsh configuration files
setopt EXTENDED_GLOB
for rcfile in $HOME/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "$HOME/.${rcfile:t}"
done

# Set Zsh as default shell
chsh -s /bin/zsh
```

### Setup tool configuration

```sh
cd $HOME/.dotfiles && ./install.sh
```

### Setup Python

```sh
pyenv install -l
pyenv install <version>
pyenv global <version>
```

### Setup Ruby

```sh
rbenv install -l
rbenv install <version>
rbenv global <version>
gem install bundler
gem install colorls
```

### Setup Tmux

```sh
git clone https://github.com/tmux-plugins/tpm $HOME/.tmux/plugins/tpm
$HOME/.tmux/plugins/tpm/bin/install_plugins
```

### Setup Vim

```sh
git clone https://github.com/VundleVim/Vundle.vim.git $HOME/.vim/bundle/Vundle.vim
vim +PluginInstall +qall
cd $HOME/.vim/bundle/YouCompleteMe
./install.py --clang-completer --racer-completer
```

### Setup theme

[iTerm2, Zsh with Powerlevel9K — Power up your terminal‘s colour scheme and productivity level!](https://medium.com/the-code-review/make-your-terminal-more-colourful-and-productive-with-iterm2-and-zsh-11b91607b98c)

```sh
# Powerline9k
# If not already installed as a submodule of prezto, then
#brew tap sambadevi/powerlevel9k
#brew install powerlevel9k

# Nerd font
brew tap caskroom/fonts
brew cask install font-hack-nerd-font
```

#### Setup Powerline

* Download and install patched font from https://github.com/supermarin/powerline-fonts
* Install Powerline by following https://powerline.readthedocs.io/en/master/installation/osx.html
