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
brew install tmux macvim cmake ninja fasd rtags tree bash htop ripgrep pyenv
brew install exiftool

git clone --depth 1 git@github.com:lotabout/skim.git $HOME/.skim && $HOME/.skim/install
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

Set up Python
```sh
pyenv install -l
pyenv install <version>
pyenv global <version>
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

### Setup Powerline

* Download and install patched font from https://github.com/supermarin/powerline-fonts
* Install Powerline by following https://powerline.readthedocs.io/en/master/installation/osx.html