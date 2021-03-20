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

Install nerd fonds for better powerlevel10k support on windows

<https://github.com/romkatv/powerlevel10k>

Install zsh on linux shell (wsl2) with

```sh
sudo apt update
sudo apt install git zsh -y
```

Install oh my zsh with curl or wget

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install the powerlevel10k schema

<https://github.com/romkatv/powerlevel10k>

Change default settings of windows terminal

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
