---
title: Tips and more
authors:
  - Alexander Serowy
---

## Fonts

Fira Code is a free monospaced font containing ligatures for common programming multi-character combinations. This is just a font rendering feature: underlying code remains ASCII-compatible. This helps to read and understand code faster. For some frequent sequences like .. or //, ligatures allow us to correct spacing.

Install on windows with `choco install firacode -y`. After installation you can use fira with

- [Visual Studio](https://github.com/tonsky/FiraCode/wiki/Visual-Studio-Instructions)
- [VS Code](https://github.com/tonsky/FiraCode/wiki/VS-Code-Instructions)

## Shell

Install nerd fonds for better powerlevel10k support on windows. Download them from [powerlevel10k git](https://github.com/romkatv/powerlevel10k) and follow the install instructions. After installation, change the default settings of the your terminal to use `MesloGS NF`. For e.g. windows terminal edit `settings.json` with the following defaults:

```json
"profiles":
{
    "defaults":
    {
        // Put settings here that you want to apply to all profiles.
        "colorScheme": "Solarized Dark",
        "fontFace": "MesloLGS NF"
    },
```

Now install zsh on your linux shell (e.g. debian in wsl2) and upgrade zsh with ohmyzsh. Both commands regarding ohmyzsh and powerlevel10k must not executed with sudo. Otherwise you would install the extensions for root and not for the current user.

```sh
sudo apt update && sudo apt install git zsh curl -y
```

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

After both extensions are installed, you can install the beloved [POWERLEVEL10K](https://github.com/romkatv/powerlevel10k) theme. Follow the instructions to set the theme as default in `~/.zshrc` and make sure, the new fonts are installed and used in your terminal!

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

While editing `~/.zshrc` you can add plugins to your new shell as well. You can find a list of available plugins [here](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins).

```ini
ZSH_THEME="powerlevel10k/powerlevel10k"
```

```ini
plugins=(git docker docker-compose debian)
```
