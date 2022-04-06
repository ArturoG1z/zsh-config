# Guide for install and configure zsh and oh-my-zsh with powerlevel10k on a new linux machine
First you have to update your linux distribution.

```zsh
sudo dnf update && sudo dnf upgrade
# OR
sudo apt update && sudo apt upgrade
```
You need to have installed git

*On Oracle Linux, I install devtools*

```zsh
sudo yum group install "Development tools"
```

Then you have to install zsh and oh-my-zsh.


```zsh
sudo dnf install zsh && sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

You have to change your default shell to zsh.

```zsh
chsh -s /bin/zsh
# For oracle linux on wsl I needed to use the following command to install chsh
# dnf install util-linux-user
```

Then clone the powerlevel10k repo and change the theme to powerlevel10k.

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
sed -i 's/^ZSH_THEME=.*/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc
```

***You need to have a nerd font installed to see all the icons.***


To start the powerlevel10k you can restart your terminal or run the following command.

```zsh
source ~/.zshrc
```


