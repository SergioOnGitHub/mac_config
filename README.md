# mac_config
All my Mac applications, homebrew, terminal, configs.


- [mac\_config](#mac_config)
  - [MacBook I am using](#macbook-i-am-using)
  - [Homebrew](#homebrew)
  - [Quick Launching](#quick-launching)
  - [Browser](#browser)
    - [Arc](#arc)
    - [Firefox Developer Edition](#firefox-developer-edition)
    - [Firefox](#firefox)
  - [Finder](#finder)
  - [Dock](#dock)
  - [Terminal](#terminal)
    - [Install Oh My Zsh](#install-oh-my-zsh)
    - [Install PowerLevel10K Theme for Oh My Zsh](#install-powerlevel10k-theme-for-oh-my-zsh)
      - [Update VSCode Terminal Font](#update-vscode-terminal-font)
    - [Configure PowerLevel10K](#configure-powerlevel10k)
    - [Install ZSH Plugins](#install-zsh-plugins)
      - [Install zsh-autosuggestions:](#install-zsh-autosuggestions)
      - [Install zsh-syntax-highlighting:](#install-zsh-syntax-highlighting)
  - [GNU Compiler](#gnu-compiler)
    - [Add the path to vs Code](#add-the-path-to-vs-code)
  - [Window Management](#window-management)
  - [App Switching](#app-switching)
  - [Hidden Bar](#hidden-bar)
  - [Menu Bar Calendar](#menu-bar-calendar)
  - [Formulae, Casks and Apps from the web](#formulae-casks-and-apps-from-the-web)
    - [Apps downloaded from the web](#apps-downloaded-from-the-web)
      - [Cisco Packet Tracer](#cisco-packet-tracer)
    - [Formulae](#formulae)
    - [Casks](#casks)


## MacBook I am using
MacBook Air M1, 2020  
Memory 8GB  
macOS 14.5  



## Homebrew

[Homebrew](https://brew.sh/) allows us to install tools and apps from the command line.

To install it, open up the built in `Terminal` app and run this command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Add Homebrew To Path
After installing, add it to the path (replace ”[username]” with your actual username):

```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/[username]/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

You can install all your apps in one go by placing them all into a text file and then running brew install:

```sh
xargs brew install < apps.txt
```

## Quick Launching

```sh
brew install raycast
```

I disable the shortcut for spotlight by doing the following
* System Settings
  * Keyboard
    * Keyboard Shortcuts
      * Spotlight
        * Disable Show Spotlight search

## Browser
### Arc
```
brew install --cask arc
```

### Firefox Developer Edition
```
brew install --cask firefox@developer-edition
```

### Firefox
```
brew install --cask firefox
```


## Finder
On `View`, enable the following: `Show status bar`, `Show path bar`.

Create ScreenShots folder. To change where the Screenshots are save, pres `CMD` + `Shift` + `5` then click on `options`, then `other location` and select your desire folder.


## Dock
* System settings
  * Desktop and dock
    * Reduce Size and turn off magnification
    * Enable `automatically hide and show the dock`
    * Disable `suggested apps`

To make the Dock instantly leap back into view when it’s needed use the following comman in the terminal.
```
defaults write com.apple.dock autohide-time-modifier -int 0; killall Dock
```
If you’d like the animation for the dock to reappear to last for a split-second, use the following:

```
defaults write com.apple.dock autohide-time-modifier -float 0.15; killall Dock
```



For futher info check the following [post](https://apple.stackexchange.com/questions/33600/how-can-i-make-auto-hide-show-for-the-dock-faster).





## Terminal

```
brew install --cask iterm2
```

Once installed, launch it and customize the settings / preferences to your liking. These are my preferred settings:

* Appearance
  * Theme
    * Minimal
* Profiles
  * Default
      * General -> Working Directory -> Reuse previous session's directory
      * Colors -> Disable `Use different colors for light mode and dark mode` -> Editing: Dark Mode
      * Keys -> Key Mappings -> Presets -> Natural Text Editing


### Install Oh My Zsh

Run this to install Oh My Zsh:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Install PowerLevel10K Theme for Oh My Zsh
Run this to install PowerLevel10K:

```
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Now that it’s installed, open the ”~/.zshrc” file with your preferred editor, I will use Vim as shown below:
```
vim ~/.zshrc
```

Change the value of “ZSH_THEME” as shown below:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

If using VIM use **i** to enter **insert** mode(edit), use **esc** to return to **normal** mode, use **:** to enter **command** mode then type **w** to save and **q** to exit.

To reflect this change on your terminal, restart it or run this command:

```
source ~/.zshrc
```

Install Meslo Nerd Font
Install the font by pressing “y” and then quit iTerm2.

#### Update VSCode Terminal Font

Open settings.json and add this line:
```
"terminal.integrated.fontFamily": "MesloLGS NF"
```

### Configure PowerLevel10K
Restart iTerm2. You should now be seeing the PowerLevel10K configuration process. If you don’t, run the following:

```
p10k configure
```


### Install ZSH Plugins
#### Install zsh-autosuggestions:

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### Install zsh-syntax-highlighting:

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Open the ”~/.zshrc” file in your desired editor and modify the plugins line to what you see below.

```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)
```

Load these new plugins by running:

```
source ~/.zshrc
```



## GNU Compiler
Cool tutorial for installing gcc for competitive programming on Mac: https://youtu.be/CZ7Mf7qxbIU?si=3W3-3xKQRHRpX072

```
brew install gcc
```

Enter the following location
``` 
cd /opt/homebrew/bin
```
The run the following command, the tutorial uses `g++-11` but currently for aug 2024 gcc installs `g++-14`
```
ln -s g++-14 g++
```
If done correctly by running `g++ --version` you should see the gcc compiler instead of `clang` compiler.



### Add the path to vs Code
Open Command Palette and search 'C/C++: Edit Configurations (JSON)' and add the following line
```
"compilerPath": "/opt/homebrew/bin/g++-14"
```




## Window Management
RayCast has this feature built in, but I am still using a separate app for this.

I use [rectangle](https://rectangleapp.com/) to move and resize windows using keyboard shortcuts. 

I highly recommend installing this and memorizing the keyboard shortcuts. Fluid and seamless window management is key to being productive while coding.

```
brew install rectangle
```


## App Switching
I use an app switcher called [AltTab](https://alt-tab-macos.netlify.app/). It shows full window previews, and has an option to show a preview for every open window in all applications.

```sh
brew install alt-tab
```
I replace the built-in `CMD + TAB` shortcut with AltTab.

I change the select previous window shortcut to `SHIFT + TAB`. To do this enter configuration, hit controls and search for the shortcut, is in the section `While open, press:`. 


## Hidden Bar

If you have several apps running that have menu bar icons, [Hidden Bar](https://github.com/dwarvesf/hidden) will let you choose which ones should be hidden after a timeout. This cleans things up if you have a ton of background apps running.

```sh
brew install hiddenbar
``` 

## Menu Bar Calendar

I like to have a calendar in the menu bar that I can quickly look at. stats does not include one, so I found [itsycal](https://www.mowglii.com/itsycal/).

```sh
brew install itsycal
```





## Formulae, Casks and Apps from the web

### Apps downloaded from the web
#### Cisco Packet Tracer
Log in inside [Cisco Packet Tracer](https://www.netacad.com/es/courses/packet-tracer). 
On menu bar, click resources, install packet tracer

### Formulae  
```
elixir  
gcc  
neovim  
node
```

### Casks  
``` 
alt-tab  
rectangle  
anaconda  
scroll-reverser  
discord  
spotify  
firefox@developer-edition  
visual-studio-code  
google-chrome  
whatsapp  
iterm2  
zoom  
obsidian  
itsycal
stats
hiddenbar
```











