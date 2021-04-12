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

Install nerd fonds for better powerlevel10k support on windows. Download them from [nerdfonts](https://www.nerdfonts.com/font-downloads). My favorite is FiraCode with `Fira Code Light Nerd Font Complete Mono`. After installation, change the default settings of the your terminal to use the installed font. For e.g. windows terminal edit `settings.json` with the following defaults:

```json
"profiles":
{
    "defaults":
    {
        // Put settings here that you want to apply to all profiles.
        "bellStyle": "none",
        "colorScheme": "Solarized Dark",
        "fontFace": "FiraCode NF",
        "fontSize": 14,
        "fontWeight": "light",
        "padding": "0"
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

To get the same keybindings like in vi, install [zsh-vi-mode](https://github.com/jeffreytse/zsh-vi-mode). Like the commands for e.g. ohmyzsh you should not use sudo.

```sh
git clone https://github.com/jeffreytse/zsh-vi-mode $HOME/.oh-my-zsh/custom/plugins/zsh-vi-mode
```

My standard configuration for `.zshrc` is currently extreme lean. Important to note: you should replace ssh key ids with keys existing in your `~/.ssh/` folder, if you want to load them on startup by default.

```zsh
# instant prompt
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# zsh
export ZSH="/home/serowy/.oh-my-zsh"

ZSH_THEME="powerlevel10k/powerlevel10k"

# ohmyzsh
plugins=(
  docker
  docker-compose
  git
  ssh-agent
  ubuntu
  zsh-vi-mode
)

zstyle :omz:plugins:ssh-agent identities ssh_name01 ssh_name02

source $ZSH/oh-my-zsh.sh

# zvm configuration
ZVM_LINE_INIT_MODE=$ZVM_MODE_NORMAL

# user configuration
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
```

## Windows Terminal

Some of my favorite themes for windows terminal. These are not default themes. Thus, you have to add them in your settings.

```json
[
  {
    "name": "Solarized Dark Higher Contrast",
    "black": "#002831",
    "red": "#d11c24",
    "green": "#6cbe6c",
    "yellow": "#a57706",
    "blue": "#2176c7",
    "purple": "#c61c6f",
    "cyan": "#259286",
    "white": "#eae3cb",
    "brightBlack": "#006488",
    "brightRed": "#f5163b",
    "brightGreen": "#51ef84",
    "brightYellow": "#b27e28",
    "brightBlue": "#178ec8",
    "brightPurple": "#e24d8e",
    "brightCyan": "#00b39e",
    "brightWhite": "#fcf4dc",
    "background": "#001e27",
    "foreground": "#9cc2c3"
  },
  {
    "name": "Sundried",
    "black": "#302b2a",
    "red": "#a7463d",
    "green": "#587744",
    "yellow": "#9d602a",
    "blue": "#485b98",
    "purple": "#864651",
    "cyan": "#9c814f",
    "white": "#c9c9c9",
    "brightBlack": "#4d4e48",
    "brightRed": "#aa000c",
    "brightGreen": "#128c21",
    "brightYellow": "#fc6a21",
    "brightBlue": "#7999f7",
    "brightPurple": "#fd8aa1",
    "brightCyan": "#fad484",
    "brightWhite": "#ffffff",
    "background": "#1a1818",
    "foreground": "#c9c9c9"
  }
]
```

Besides theming, it is important to modify the default setting to ensure `C-v` reacts correctly. You have to comment the following passage out.

```json
  "actions": [
      // Copy and paste are bound to Ctrl+Shift+C and Ctrl+Shift+V in your defaults.json.
      // These two lines additionally bind them to Ctrl+C and Ctrl+V.
      // To learn more about selection, visit https://aka.ms/terminal-selection
      { "command": { "action": "copy", "singleLine": false }, "keys": "ctrl+c" },
      { "command": "paste", "keys": "ctrl+v" }
```

