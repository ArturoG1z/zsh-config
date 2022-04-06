# Guide for install and configure zsh and oh-my-zsh with powerlevel10k on a new linux machine

## 1. First you have to update your linux distribution.

```zsh
sudo dnf update && sudo dnf upgrade
```
OR
```zsh
sudo apt update && sudo apt upgrade
```
You need to have installed git

*On Oracle Linux, I install devtools*

```zsh
sudo yum group install "Development tools"
```

## 2. Then you have to install zsh and oh-my-zsh.


```zsh
sudo dnf install zsh && sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

You have to change your default shell to zsh.

```zsh
chsh -s /bin/zsh
# For oracle linux on wsl I needed to use the following command to install chsh
# dnf install util-linux-user
```

## 4. Clone the powerlevel10k repo and change the theme to powerlevel10k.

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
sed -i 's/^ZSH_THEME=.*/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc
```

***You need to have a nerd font installed to see all the icons.***


To start the powerlevel10k you can restart your terminal or run the following command.

```zsh
source ~/.zshrc
```

If you want that the shown path only show the last folder you can change the following line to your .p10k.zsh.

```zsh
typeset -g POWERLEVEL9K_SHORTEN_STRATEGY=truncate_to_unique
TO 
typeset -g POWERLEVEL9K_SHORTEN_STRATEGY=truncate_to_last
```

## 5. The next plugins are the basic ones that I use.

First add the plugins list to your .zshrc with the following commands, these commands only work if you didn't add any plugins before.

```zsh
sed -i 's/^plugins=(.*)/plugins=(/g' ~/.zshrc
sed -i '/^plugins=(/a \
  git \
  sudo \
  web-search \
  alias-finder \
  jsontools \
  copypath \
  copyfile \
  copybuffer \
  dirhistory \
  history \
  extract \
  zsh-autosuggestions \
  zsh-syntax-highlighting \
)\
' ~/.zshrc
```

Then add the repos needed for these two plugins.

```zsh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

For more information about the plugins check the documentation or this video
https://www.youtube.com/watch?v=LEOqiyxx16c&t=577s
https://lobogit.unm.edu/blue/linux-cfg/-/tree/master/.oh-my-zsh/plugins/extract 

