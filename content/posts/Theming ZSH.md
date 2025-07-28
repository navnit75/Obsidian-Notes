I have used

- [Tutorial](https://www.the-digital-life.com/awesome-wsl-wsl2-terminal/) to come up with these commands.
-  Start with installing zsh and cloning `oh-my-zsh` repo.  

```shell
sudo apt update
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Theme Installation
 - My personal favourite theme is Powerlevel10k you can choose yours, by going on oh-my-zsh home page.
- You can use the below command
```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
- To activate the theme you need to edit your `~/.zshrc` file in your personal folder and replace  `ZSH_THEME=”robbyrussel”` with `ZSH_THEME=”powerlevel10k/powerlevel10k”`.
- You might also like `ZSH_THEME="eastwood"` if you like simplicity

## Plugin Installation
- Lets install `zsh-autosuggestion` by cloning it inside the plugins folder of `.oh.my.zsh`.
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
-  To enable the auto-suggestion plugin or any other plugins in “zsh”, edit your “~/.zshrc” file in your personal folder.
-  Simply change the default line `plugins=(git)` to `plugins=(git zsh-autosuggestions)`.

## Virtual Box SSH setup
-  Additionally setting up to ssh into the Virtual Box created system is pretty hectic. 
- You can create a port forwarding option in the network settings of your virtual box and edit your host machine's ssh config as provided in below file.
``` title=".ssh/config"
Host localhost
  HostName localhost
  Port 2222
  User <username>
  PreferredAuthentications publickey
  IdentityFile "/Users/<location of id_rsa>/id_rsa"
```
-  To generate the rsa private and public keys `ssh-keygen -t rsa -b 4096`
-  Add the `id_rsa.pub` to `authorized_keys` in the remote .ssh folder. If its not there rename the `id_rsa.pub` of local system to the `authorized_keys` also change the permission to 600.