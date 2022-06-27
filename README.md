## FreshMint
Setup after newly installed Linux Mint:

## Zsh and Oh My Zsh
For the installation of Zsh and Oh My Zsh, we need a number of tools which can be installed using the below command:

```bash
sudo apt-get update
sudo apt install wget curl git -y
```

Zsh is already available in Linux Mint 20 repository making it easy to install. Run the command below:

```bash
sudo apt-get install zsh -y
```

Check the installed version to confirm Zsh installation:

```bash
zsh –version
```

Once installed, change the default shell of root user to zsh by running the below command:

```bash
sudo chsh -s /usr/bin/zsh $USER
```

Now log out from the current shell then log back in. When you switch to root user, you will notice that the shell has changed. To verify which shell you are currently in, run the below command, shoud output `usr/bin/zsh`:

```bash
echo $SHELL
```

As explained before, Oh-My-Zsh is used to manage Z shell and it provides quite a number of functions,themes and plugins. To install Oh-My-Zsh, we first need to install some packages that will enable us to download Oh-My-Zsh installer script:

```bash
sudo apt-get install wget git
```

Now down and execute Oh-My-Zsh installer script:

```bash
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

The output should be as below:

![alt text](https://github.com/ii00/FreshMint/blob/main/img/img1.png)

Just as Bash has .bashrc configuration file, Zsh also needs to have a configuration file called .zshrc which is found in the Oh-My-Zsh template directory if not already on your home directory. To enable the configuration file, run the below commands, first one if .zshrc is not on your home directory or jump to the second command if you have .zshrc in your home directory:

```bash
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc:
source ~/.zshrc
```

Check available themes. The current default theme provided by Oh-My-Zsh is ‘robbyrusell‘ theme.:

```bash
cd ~/.oh-my-zsh/themes/
ls -a
```

To change theme in `~/.zshrc`. Thats the theme I use:

```
ZSH_THEME="agnoster"
```

[Powerlevel10k](https://github.com/romkatv/powerlevel10k#oh-my-zsh) is also nice alternative theme.

To check available plugins:

```bash
cd ~/.oh-my-zsh/plugins/
ls -a
```

To add plugins in `~/.zshrc`. These the plugins I use:

```
plugins=(git gitfast git-open direnv dnf iterm2 kubectl terraform alias-tips aws brew vscode colorize dirhistory extract zsh-completions zsh-autosuggestions history-substring-search zsh-syntax-highlighting colored-man-pages forgit)
```

Git clone needed plugins(`forgit` requires [fzf](https://github.com/junegunn/fzf)):

```bash
cd ~/.oh-my-zsh/custom/plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions
git clone https://github.com/paulirish/git-open
git clone https://github.com/zsh-users/zsh-completions
git clone https://github.com/djui/alias-tips
git clone https://github.com/ael-code/zsh-colored-man-pages
git clone https://github.com/wfxr/forgit
```

## nvm, npm, angular...
Recommended installing node and npm using [nvm](https://github.com/nvm-sh/nvm#git-install).

Then:

```bash
nvm install node
```

## github ssh
The `-o` flag forces the tool to generate SSH keys with the OpenSSH format. The `-t` flag specifies they type of SSH keys to create. The `-C` flag allows for comments that get added as metadata at the end of the public key.

```bash
cd ~/.ssh
ssh-keygen -o -t rsa -C "email@example.com"
cat id_rsa.pub
```

Log into GitHub, Navigate `settings` > `SSH and GPG keys` > `New GitHub SSH key`. Provide a unique name, and paste the value of the private GitHub SSH key you copied earlier. Once you copy the SSH URL of the GitHub repo, you can use it to clone a copy of the remote repo into the local environment. On the initial clone, you might get a message that questions the authenticity of the host. This due to the lack of a third party certificate authority to validate your keys. If you are confident in the validity of the keys you just created — which you certainly should be, because you created them — just type yes to carry on with an SSH clone of the GitHub repo.

