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

# TODOs
- Try out and add HTTPie
- Zsh as first-class citizen
- Include my macOS install notes into README
- Replace keybinds.json and settings.json

- Things to add:
	- nvim nightly
	- yabai/spacebar/skhd
	- vagrant
	- httpie

- Add kubernetes k-on magic stuff as install to ~/bin

- Sync files
	- iterm2 profile
	- .dotfiles (or get via git?)

- Figure out how to configure/do:
	- Firefox login to account
	- macOS desired preferences

- Clean up .zshrc
	- dotnet install location
	- figure out openssl
	- coreutils from brew?
	- double check FZF_DEFAULT_COMMAND
	- remove all linux references

- PR to Brad's repo
	- Insync instead of Google Drive
	- Support iTerm2?
	- coreutils in git
	- update go path to use $GOPATH
	- add README note about VScode
