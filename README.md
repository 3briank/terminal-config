# terminal-config

I wanted to customize my default Terminal.app to have integration for git and other plugins along with a good color scheme and format. I pulled together everything I did to get it how I want and the color options that I made. 

I've found that a lot of people are using Oh My Zsh themes with iTerm2. It's a popular open source terminal, you can get it with Homebrew `brew cask install iterm2`. If you don't have [Homebrew](https://brew.sh/ "Homebrew Homepage") you should go get it.
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
I prefer to use the default Terminal.app installed with macOS. This is how I customized it.

![Example Image](https://github.com/3briank/terminal-config/blob/master/example.png)

## Install & Setup

### Pre-requireties
With the release of macOS Catalina, Apple set the default shell to zsh. If you're not running the newest version, check your shell `echo $SHELL`. If it's not something like `/bin/zsh` change it to zsh first (below), otherwise you're good.

Install (you need to have Homebrew)
```shell
brew install zsh
```

Set as default
```shell
chsh -s /bin/zsh
```

### Download Oh My Zsh
Oh My Zsh is an open source framework for managing your Zsh configurations. 
You can read about it here https://github.com/ohmyzsh/ohmyzsh or just curl this:

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Install Powerline fonts
Fonts for status bar, you're going to need this. Here's the page of what you're getting https://github.com/powerline/fonts. These are the pre-patched ones.

#### Run this
```shell
# clone
git clone https://github.com/powerline/fonts.git --depth=1
# install
cd fonts
./install.sh
# clean-up a bit
cd ..
rm -rf fonts
```

### Set the theme
This is the theme that I use https://github.com/agnoster/agnoster-zsh-theme. You don't need to do anything there, just edit your `.zshrc` file.

```shell
cd ~
open -a textEdit .zshrc
```

command+F `ZSH_THEME=` and set that line to `ZSH_THEME="agnoster"`, save the file. The default theme is `robbyrussell` which is kind of boring. 

### Change the colors

1. Clone this repo

```shell
cd ~/Desktop
git clone https://github.com/3briank/terminal-config.git
```
2. Open Terminal. Go to Shell -> Import. Select `Terrapin_Dark1.terminal` or `*_Dark2` from the `terminal_config` directory.

3. If the font is not set to 'Meslo LG M Regular for Powerline 11pt.' then open Terminal -> Preferences, select 'Profiles', under 'Font' click 'change'. 

4. Set it to 'All Fonts' -> 'Meslo LG M for Powerline' -> 'Regular' -> 11 (or any size)

5. Under all of the themes, you can select 'Default' to mark it as the default terminal configuration.

## Other changes

### Plugins

Here is a list of the plugins https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview, add them to your `~/.zshrc` file under `plugins=(<plugin_1> <plugin_2> <plugin_3>)`. Don't put commas between them, just white space.

### Shorten Prompt

It defaults to showing `<username>@<host>` in your prompt. It takes up some extra space, so you might want to add this line to the end of your `.zshrc` file `prompt_context(){}`. It will hide it for you.

To see the change either restart terminal or source your `.zshrc` file
```shell
. ~/.zshrc
```

### Git showing with `less`

If you run a command like `git branch` and there are only a few lines it will open as if you used the `less` command instead of just showing the result underneath. I added this to my `.zshrc` file 

`export LESS='-FRX'`

The `LESS` environment variable is defaulted to `-R` with Oh My Zsh, changing the flag to `-FRX` does mess up the scrolling a little, but I like it better then it always opening it with `less`. If you have a better way, let me know.

You could also set the pager to false for git

```shell
git config --global pager.branch false
```

## Uninstall & Revert
If you want to go back to how things were before.

1. Go to Terminal -> Preferences. Select Basic, select Default at the bottom.

2. Uninstall Oh My Zsh by running
```shell
uninstall_oh_my_zsh
```

