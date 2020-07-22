# macOS Developer Machine Setup

This repository contains useful scripts to set up a macOS Unix-y development machine. They have been tested with the following OSes:

| Distro                                                          | SKU     | Version(s)          |
| --------------------------------------------------------------- | ------- | ------------------- |
| [macOS](https://www.apple.com/macos/)                           | Desktop | 10.15               |

Text shell customization assumes you're using zsh (macOS in particular now ships with zsh as the default shell). 

# Pre-Requisites

## macOS

1. Install [Homebrew](https://docs.brew.sh/Installation)

3. Set up Python 3 as the default version of Python:

   ```bash
   $ echo "alias python='python3'" >> ~/.bashrc
   $ echo "export PATH=$HOME/Library/Python/3.7/bin:$PATH" >> ~/.bashrc
   ```

4. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-macos)

# Running

Before running the scripts, please review `_all.yaml` and `_all_no_customization.yaml`, and comment out software you don't want installed. In particular, most folders contain `customization.yaml` files which tend to contain my personal opinions on customizations; feel free to comment out sections of those files, or ignore them entirely.

To run the setup:

```bash
$ ansible-playbook -K _all.yaml
```

You will be prompted for your password, so that administrative-level software can be installed. _**You must be a sudoer to run these scripts, otherwise the installation process will fail.**_ You can also run individual files if you'd prefer to take more control over what's executed.

Since core OS packages are upgraded, it is safest to reboot the PC/VM after running these scripts. At a bare minimum, many UI shell customizations done here will require you to log out and log back in.

## macOS

Most software does work on macOS, with a few exceptions noted below:

* Insync is replaced with the native Google Backup and Sync
* QEMU/KVM is replaced with VirtualBox (note that installing VirtualBox might fail the first time because of required permissions)

### Preferences
#### General
- Sidebar icon size: Small
- Automatically hide and show the menu bar
- Default web browser: Firefox

#### Dock
- Size: 3.5/10
- Magnification: Enabled, 5/10
- Prefer tabs when opening documents: Always
- Animate opening applications: Disabled
- Show recent applications in Dock: Disabled

#### Mission Control
- Automatically rearrange Spaces: Disabled
- Show Desktop: `-`

#### Internet Accounts
Calendars
- Google: `bry-guy@github.com`
- Google: `bryansmi@umich.edu`

#### Touch ID
- Add right index/middle, left index

#### Security & Privacy
General
- Require password `1 hour`

#### Sound
- Alert volume: 10%

#### Keyboard
Keyboard
- Key Repeat: Fast
- Delay Until Repeat: Short
- Touch Bar Shows: F1, F2
- Press Fn key to: Show Control Strip

Text
- Add period with double-space: Disabled
- Touch Bar typing suggestions: Disabled

#### Touchpad
Point & Click
- Look up & data detectors: Disabled
- Tap to click: Enabled
- Click: Light
- Tracking speed: 9/10

Scroll & Zoom
- Scroll direction: Natural: Disabled

More Gestures
- Swipe between pages: Disabled
- Notifcation Center: Disabled
- Launchpad: Disabled

#### Mouse
- Tracking speed: 4/10
- Double-Click speed: 7/10
- Scrolling speed: 7/10

#### Energy Saver
- Battery: 15min

#### Sharing
- Computer Name: Set it


Shortcuts
- Launchpad & Dock - Turn Dock Hiding On/Off: Disabled

# TODOs
- [x] Try out and add HTTPie
- [x] Replace keybinds.json and settings.json
- [x] Zsh as first-class citizen
- [x] Add Karabiner-Elements
- [x] Fix nodeJS install
- [] Determine if I care about Logitech Gaming Software
- [] Add vim-plug install
- [] Add watson install
- [x] Sync Karabiner-Elements file
- [x] Sync iterm2 profile
- [x] Sync .dotfiles 
- [] Write automatic syncing of .dotfiles
- [] Perform plugin install for neovim
- [] Figure out syncing/linking of config/Code folder correctly
- [] Include my macOS install notes into README
- [] Firefox login to account
- [] macOS desired preferences
	- [] system preferences
	- [] text preferences (aliasing settings)
	- [] dock layout (apps/icons/order)
- [x] Create symlinks for sync'd files
- [x] Add cleanup to nvim/core.yaml so that it is idempotent

- Clean up .zshrc
	- [] dotnet install location; figure out if I want to use ~/bin vs /usr/local/bin or something
	- [] python/pyenv install location
	- [] figure out openssl (remove?)
	- [x] remove all linux references

- PR to Brad's repo
	- Insync instead of Google Drive
	- Support iTerm2?
	- coreutils in git
	- update go path to use $GOPATH
	- add README note about VScode
