# mac_config

All my Mac applications, homebrew, terminal, configs.

- [mac\_config](#mac_config)
  - [MacBook I am using](#macbook-i-am-using)
  - [Homebrew](#homebrew)
  - [Quick Launching](#quick-launching)
  - [Browser](#browser)
    - [Arc](#arc)
  - [Finder](#finder)
  - [Dock](#dock)
  - [Git and SSH](#git-and-ssh)
    - [Configure Git identity](#configure-git-identity)
    - [Generate an SSH key](#generate-an-ssh-key)
    - [Copy the SSH public key](#copy-the-ssh-public-key)
  - [GNU Compiler](#gnu-compiler)
    - [Add the path to vs Code](#add-the-path-to-vs-code)
  - [Window Management](#window-management)
  - [App Switching](#app-switching)
  - [Hidden Bar](#hidden-bar)
  - [Formulae and Casks](#formulae-and-casks)
    - [Formulae](#formulae)
    - [Casks](#casks)

## MacBook I am using

MacBook Air M1, 2020  
Memory 8GB  
macOS 14.5  

## Initial configuration

Trackpad

- Disable Force Click
- Disable Look up
- Secondary Click Click in bottom right corner
- Enable tap to click

- More Gestures
- Off Swipe beteen pages and full screen

  Desktop and Dock
  Remove from Dock all apps
  - Position on screen Right
  - Size Small
  - Automattically hide and show the Dock

  Finder

  New finder Window shows home Directory
Enable the following on SideBar
  Documents
  Downloads
  Home Directory
  Sergios Macbook air
  Create Dev folder inside home directory
  Create Uni folder inside home directory
  Create Obsidian Vault folder inside
  Create ScreenShots folder inside Pictures
  Change where screenShots are save:
  CMD + SHIFT + 5
  - options
  - other location
  - Select screenShots
  Add folders created to your Sidebar

  View Configuration
  Show path bar
  Show status bar
  
## Homebrew

[Homebrew](https://brew.sh/) allows us to install tools and apps from the command line.

To install it, open up the built in `Terminal` app and run this command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Add Homebrew To Path
After installing, add it to the path (replace ”[username]” with your actual username):

```sh
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

- System Settings
  - Keyboard
    - Keyboard Shortcuts
      - Spotlight
        - Disable Show Spotlight search

## Browser

### Arc

```sh
brew install --cask arc
```

## Finder

On `View`, enable the following: `Show status bar`, `Show path bar`.

Create ScreenShots folder. To change where the Screenshots are save, pres `CMD` + `Shift` + `5` then click on `options`, then `other location` and select your desire folder.

## Dock

- System settings
  - Desktop and dock
    - Reduce Size and turn off magnification
    - Enable `automatically hide and show the dock`
    - Disable `suggested apps`

To make the Dock instantly leap back into view when it’s needed use the following comman in the terminal.

```sh
defaults write com.apple.dock autohide-time-modifier -int 0; killall Dock
```

If you’d like the animation for the dock to reappear to last for a split-second, use the following:

```sh
defaults write com.apple.dock autohide-time-modifier -float 0.15; killall Dock
```

For futher info check the following [post](https://apple.stackexchange.com/questions/33600/how-can-i-make-auto-hide-show-for-the-dock-faster).

## Git and SSH

### Configure Git identity

Set the name and email that Git will attach to new commits. Replace the example
values with your own:

```sh
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Verify the global configuration:

```sh
git config --list
```

### Generate an SSH key

Generate an Ed25519 key pair, using the email associated with your Git hosting
account:

```sh
ssh-keygen -t ed25519 -C "you@example.com"
```

Press Enter to accept the default location (`~/.ssh/id_ed25519`) and protect the
private key with a passphrase when prompted.

### Copy the SSH public key

Copy the public key to the macOS clipboard, then add it to your Git hosting
account:

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

## GNU Compiler

Cool tutorial for installing gcc for competitive programming on Mac: <https://youtu.be/CZ7Mf7qxbIU?si=3W3-3xKQRHRpX072>

```sh
brew install gcc
```

Enter the following location

```sh
cd /opt/homebrew/bin
```

The run the following command, the tutorial uses `g++-11` but currently for jul 2026 gcc installs `g++-16`

```sh
ln -s g++-16 g++
```

If done correctly by running `g++ --version` you should see the gcc compiler instead of `clang` compiler.

### Add the path to vs Code

Open Command Palette and search 'C/C++: Edit Configurations (JSON)' and add the following line

```sh
"compilerPath": "/opt/homebrew/bin/g++-14"
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

## Window Management

RayCast has this feature built in, but I am still using a separate app for this.

I use [rectangle](https://rectangleapp.com/) to move and resize windows using keyboard shortcuts.

I highly recommend installing this and memorizing the keyboard shortcuts. Fluid and seamless window management is key to being productive while coding.

```sh
brew install rectangle
```

## Formulae and Casks

### Formulae  

```text
elixir  
gcc  
neovim  
node
uv
```

### Casks  

```text
alt-tab
arc
chatgpt
codex
codex-app
discord
font-jetbrains-mono
font-jetbrains-mono-nerd-font
ghostty
google-chrome
itsycal
karabiner-elements
microsoft-office
obsidian
postman
rectangle
scroll-reverser
spotify
ticktick
visual-studio-code
whatsapp
zen
zoom
```
