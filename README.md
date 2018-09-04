# AfterInstall
Cheatsheet for a Linux after install steps

## Checklist
 - [ ] Git
 - [ ] Terminator
 - [ ] Virtualenv
 - [ ] Oh My Zsh
 - [ ] Vim
    - [ ] Vim Plugins
 - [ ] Iptables Persistent

## Install Process

### Git
```
sudo apt-get install git
```
 * Setup name and email
 ```
 git config --global user.email <email>
 git config --global user.name <Full Name>
 ```

 * Setup new SSH key
 ```
 ssh-keygen -t rsa 4096 -C "<email>"
 ```

### Terminator
```
sudo apt-get install terminator
sudo update-alternatives --config x-terminal-emulator
gsettings set org.gnome.desktop.default-applications.terminal exec gnome-terminal
gsettings set org.gnome.desktop.default-applications.terminal exec-arg ''
```

### Virtualenv
```
sudo apt-get install virtualenv
pip install --user virtualenvwrapper
```

### ZSH
Be sure to read the official repo docs found at [https://github.com/robbyrussell/oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
```
sudo apt-get install zsh
sudo apt-get install git
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

 * Copy the dotfiles
 * Adapt the dotfile to the current machine
 * Check for missing fonts

 **IMPORTANT**
 ```
 When switching to root zsh bash will be loaded. To keep the same aesthetics,
 the same procedure should be followed with the root username (bear in mind it
 might be a security hazard)
 ```

### Vim
Official repo found at [https://github.com/rmariano/vim-config](https://github.com/rmariano/vim-config)
```
mkdir -p ~/.vim && wget -O ~/.vim/Makefile -N https://raw.github.com/rmariano/vim-config/master/Makefile && make -C ~/.vim install
```

#### Vim Plugins (optional)

 * Install Pathogen-vim [https://github.com/tpope/vim-pathogen](https://github.com/tpope/vim-pathogen)
    ```
    mkdir -p ~/.vim/autoload ~/.vim/bundle && \
    curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
    ```
 * Flake 8 [https://github.com/nvie/vim-flake8](https://github.com/nvie/vim-flake8)
    ```
    git clone https://github.com/nvie/vim-flake8.git ~/.vim/bundle/vim-flake8
    ```
 * Vim Fugitive (Blame) [https://github.com/tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
    ```
    git clone https://github.com/tpope/vim-fugitive.git ~/.vim/bundle/vim-fugitive
    ```

 **IMPORTANT**

 ```
 The root user will keep another configuration. To use the same vim config with
 root (perhaps desiring to edit system files) it is a good idea to symlink .vim
 and .vimrc to a user config
 ```

### Iptables
```
sudo apt-get install iptables-persistent
```
