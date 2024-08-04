# mac_config
All my Mac applications, homebrew, terminal, configs.


- [mac\_config](#mac_config)
  - [MacBook I am using](#macbook-i-am-using)
  - [Homebrew](#homebrew)
        - [Formulae](#formulae)
        - [Casks](#casks)
  - [Quick Launching](#quick-launching)
  - [Terminal](#terminal)
    - [Install Oh My Zsh](#install-oh-my-zsh)
    - [Install PowerLevel10K Theme for Oh My Zsh](#install-powerlevel10k-theme-for-oh-my-zsh)
    - [Configure PowerLevel10K](#configure-powerlevel10k)
    - [Install ZSH Plugins](#install-zsh-plugins)
      - [Install zsh-autosuggestions:](#install-zsh-autosuggestions)
      - [Install zsh-syntax-highlighting:](#install-zsh-syntax-highlighting)
  - [Window Management](#window-management)
  - [App Switching](#app-switching)
  - [Hidden Bar](#hidden-bar)
  - [System Stats Widgets](#system-stats-widgets)
  - [Menu Bar Calendar](#menu-bar-calendar)
  - [Formulae, Casks and Apps from the web](#formulae-casks-and-apps-from-the-web)
    - [Formulae](#formulae-1)
    - [Casks](#casks-1)
    - [Apps downloaded from the web](#apps-downloaded-from-the-web)
      - [Cisco Packet Tracer](#cisco-packet-tracer)


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
##### Formulae
```
elixir  
gcc  
neovim  
node
```
##### Casks
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

```sh
xargs brew install < apps.txt
```

## Quick Launching

```sh
brew install raycast
```


## Terminal

I prefer [iTerm2](https://iterm2.com/) because:
* Lots of customization options
* Clickable links
* Native OS notifications

There are a lot of options for a terminal replacement, but I've been using iTerm2 for years and it works great for my needs.

Checkout their documentation for more info on what iTerm2 can do: [https://iterm2.com/documentation.html](https://iterm2.com/documentation.html)


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
      * Keys -> Key Mappings -> Presets -> Natural Text Editing
          * This allows me to use the [keyboard shortcuts](https://gist.github.com/w3cj/022081eda22081b82c52) I know and love inside of iTerm2


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

Update VSCode Terminal Font

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
```
brew install gcc
```
### Add the path to vs Code
Open Command Palette and search 'C/C++: Edit Configurations (JSON)' and add the following line
```
"compilerPath": "/opt/homebrew/bin/g++-14"
```


## Window Management
RayCast has this feature built in, but I am still using a separate app for this.

I use [rectangle](https://rectangleapp.com/) to move and resize windows using keyboard shortcuts. 

I highly recommend installing this and memorizing the keyboard shortcuts. Fluid and seamless window management is key to being productive while coding.

Search for `rectangle` in RayCast `brew search` or:

```
brew install rectangle
```


## App Switching
I use an app switcher called [AltTab](https://alt-tab-macos.netlify.app/). It shows full window previews, and has an option to show a preview for every open window in all applications (even minimized ones).

I replace the built-in `CMD+TAB` shortcut with AltTab.

Search for `alt-tab` in RayCast `brew search` or:

```sh
brew install alt-tab
```

## Hidden Bar

If you have several apps running that have menu bar icons, [Hidden Bar](https://github.com/dwarvesf/hidden) will let you choose which ones should be hidden after a timeout. This cleans things up if you have a ton of background apps running.

Search for `hiddenbar` in RayCast `brew search` or:

```sh
brew install hiddenbar
``` 

## System Stats Widgets

I use [stats](https://github.com/exelban/stats) to see my network traffic, CPU temp / usage and RAM usage at a glance.

In each widget, a key setting to look for is under "widget settings", choose "merge widgets into one".

Search for `stats` in RayCast `brew search` or:

```sh
brew install stats
```

## Menu Bar Calendar

I like to have a calendar in the menu bar that I can quickly look at. stats does not include one, so I found [itsycal](https://www.mowglii.com/itsycal/).

```sh
brew install itsycal
```

itsycal shows the date, so I hide the date in the system menu bar widget:

* System Preferences
  * Dock & Menu Bar
      * Clock
          * Show Date -> Never
          * Show Day of Week -> No




## Formulae, Casks and Apps from the web
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


### Apps downloaded from the web
#### Cisco Packet Tracer
Log in inside [Cisco Packet Tracer](https://www.netacad.com/es/courses/packet-tracer). 
On menu bar, click resources, install packet tracer










