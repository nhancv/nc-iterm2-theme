# Default

![Default](https://gist.githubusercontent.com/kevin-smets/9722391f8b3e4fa436b1c1dcf05ecd88/raw/14012c157e280684ae5c75686eef2e302123e51b/agnoster.png)

# Powerlevel9k

![Powerlevel9k](https://gist.githubusercontent.com/kevin-smets/9722391f8b3e4fa436b1c1dcf05ecd88/raw/29389beaa891f939e274b8e20622647357e793d4/powerlevel9k.png)

# How to install

## iTerm2

    brew cask install iterm2
    
Or, if you do not have homebrew (you should ;)): [Download](http://www.iterm2.com/downloads.html) and install iTerm2 

iTerm2 has better color fidelity than the built in Terminal, so your themes will look better.
    
Get the iTerm color settings

- [Solarized Dark theme](https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Solarized%20Dark%20-%20Patched.itermcolors) (patched version to fix the bright black value)
- [Solarized Light theme](https://raw.githubusercontent.com/altercation/solarized/master/iterm2-colors-solarized/Solarized%20Light.itermcolors)
- [More themes @ iterm2colorschemes](http://iterm2colorschemes.com/)
    
Just save it somewhere and open the file(s). The color settings will be imported into iTerm2. Apply them in iTerm through iTerm → preferences → profiles → colors → load presets. You can create a different profile other than `Default` if you wish to do so.

# Oh My Zsh 

More info here: https://github.com/robbyrussell/oh-my-zsh

## Install with curl
    
    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    
When the installation is done, edit `~/.zshrc` and set `ZSH_THEME="agnoster"`

## Powerlevel9k

If you prefer the Powerlevel9k look with added info such as exit codes and timestamps on the right, run:

    git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k

Then edit your `~/.zshrc` and set `ZSH_THEME="powerlevel9k/powerlevel9k"`.

Powerlevel9k offers a whole lot more, best is to [check out these user made configs yourself](https://github.com/bhilburn/powerlevel9k/wiki/Show-Off-Your-Config).

## Install a patched font

- [Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf) (the one in the screenshot). Click "view raw" to download the font.
- [Others @ powerline fonts](https://github.com/powerline/fonts)
    
Open the downloaded font and press "Install Font".

Set this font in iTerm2 (14px is my personal preference) (iTerm → Preferences → Profiles → Text → Change Font).

Restart iTerm2 for all changes to take effect.

### Visual Studio Code config

Installing a patched font will mess up the integrated terminal in VS Code unless you use the proper settings. You'll need to go to settings (CMD + ,) and add or edit the following values:

- for Source Code Pro: `"terminal.integrated.fontFamily": "Source Code Pro for Powerline"`
- for Meslo: `"terminal.integrated.fontFamily": "Meslo LG M for Powerline"`
- for other fonts you'll need to check the font name in Font Book.

You can also set the fontsize e.g.: `"terminal.integrated.fontSize": 14`

For me: (Code -> Pref -> Setting -> User settings
```
    "terminal.integrated.fontFamily": "Source Code Pro for Powerline",
    "terminal.integrated.fontSize": 12,
    "terminal.integrated.shell.osx": "zsh"
```

# Further tweaking

Things like

- auto suggestions
- word jumping with arrow keys / natural text editing
- shorter prompt style
- syntax highlighting

can be found in the section below.

## Auto suggestions (for Oh My Zsh)

![Auto suggestions](http://i66.tinypic.com/b5i9dv.png)

Just follow these steps: https://github.com/tarruda/zsh-autosuggestions#oh-my-zsh

If the auto suggestions do not appear to show, it could be a problem with your color scheme. Under "iTerm → Preferences → Colors tab", check the value of Black Bright, that is the color your auto suggestions will have. It will be displayed on top of the Background color. If there is not enough contrast between the two, you won't see the suggestions even if they're actually there..

## Enable word jumps and word deletion, aka natural text selection

By default, word jumps (option + → or ←) and word deletions (option + backspace) do not work. To enable these, go to "iTerm → Preferences → Profiles → Keys → Load Preset... → Natural Text Editing → Boom! Head explodes"

## Custom prompt styles

By default, your prompt will now show “user@hostname” in the prompt. This will make your prompt rather bloated. Optionally set `DEFAULT_USER` in `~/.zshrc` to your regular username (these must match) to hide the “user@hostname” info when you’re logged in as yourself on your local machine. You can get your exact username value by executing `whoami` in the terminal.

For further customisation of your prompt, you can follow a great guide here: https://code.tutsplus.com/tutorials/how-to-customize-your-command-prompt--net-24083

For me: 
```
ZSH_THEME="agnoster"
DEFAULT_USER="nhancao"
```

## Syntax highlighting

```
brew install zsh-syntax-highlighting
```

If you do not have or do not like homebrew, follow [the installation instructions](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) instead.

After installation through homebrew, add

```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

to **the end** of your `.zshrc` file. After that, it's best to restart your terminal. Sourcing your `~/.zshrc` does not seem to work well with this plugin.

## Include .bash_profile

Push to **the end** of your `.zshrc` file

```
# Add bash.
if [ -f ~/.bash_profile ]; then
    source ~/.bash_profile
fi
```
