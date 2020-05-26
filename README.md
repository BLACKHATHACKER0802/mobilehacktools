# Mobile Security Toolchain

[![Build Status](https://travis-ci.org/xebia/mobilehacktools.svg?branch=master)](https://travis-ci.org/xebia/mobilehacktools)

This is the mobile security toolchain project. It is loosely based on the MSTG testing tools section (https://github.com/OWASP/owasp-mstg/blob/master/Document/0x08-Testing-Tools.md).

## Current status

The project is in early beta stage. Feel free to contribute!
Note that developments are currently slow as the primary focus is now on developing the MSTG.
There are quiet a few bugs when running this on Catalina. We hope to resolve them in 2021 (as Corona outbreak made our work a little harder) unless a volunteer arrives earlier ;-).

## Pre-requisites

Have a Mac OS X based system (needs 10.13.x) with about 4 GB of RAM and 4 GB of free space. Next, install Docker for Mac on it and then:

- if you want to have both the iOS and Android tools, as well as all the scaffolding, just use `./install.sh`
- if you want to have the iOS tools only: install brew and Ansible, then type:

  ```sh
   ansible-galaxy install -r requirements.yml
    ansible-playbook -K ./iOS/generic_items.yml
  ```

- if you want to have the Android tools only: install brew and Ansible, then type:

```sh
  ansible-playbook ./Android/generic_items.yml
```

Please note: the iOS part requires you to install XCode using the Mac App Store (MAS) which will ask you to authenticate with a popup.

## Tools

Brew, pip and Ansible will be installed first, if not available. Then generic, iOS and Android tools will be installed:

### Generic Tools

- autoconf
- bash-completion
- dependency-check
- doxygen
- git
- go
- gpg
- httpie
- ideviceinstaller
- libimobiledevice
- mcrypt
- mitmproxy
- nmap
- node
- python #python 3
- testssl.sh
- openssl
- wget
- atom
- burp-suite
- chromedriver
- docker
- dropbox
- firefox
- google-chrome
- java
- owasp-zap
- sequel-pro
- vagrant
- virtualbox
- Frida
- Radare2
- Objection
- MobSF
- Appmon
- zsh //sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"


### Tools for Android

- apktool
- dependency-check
- dex2jar
- ideviceinstaller
- jadx
- libimobiledevice
- mcrypt
- node
- android-studio
- java
- jd-gui
- Nathan
- super analyzer
- Drozer
- Qark

### Tools for iOS

- cmake
- usbmuxd
- libimobiledevice
- qt@4
- class-dump
- itms
- idb
- java

## Quirks

As we are still in development of 1.0, there are the following quirks:

- Some applications might not work the first time as you will first have to start them from your Applications folder, such as: Android Studio (including ADB) & Docker for Mac. After that you have to run the runbooks once more. You should have , after 2 runs of the android runbook (e.g. run android runbook, run android studio, run android runbook, a working adb, given that you use .bash_profile)
- iOS has not been tested on the buildserver (only general and android are, so please test them)
- Some of the output of ansible seems very "drastic": in red/green/yellow. Please wait for it to finish and then see if something failed.
- For iOS you need to run things twice: once to start the installation, while being logged in into the Apple store with your account (actual active state can be achieved by installing any app from the app-store), second time with an active developer account in xCode.
- Lastly, it could be the case when you are testing this on a separate account, which does not have the correct rights for the brew folders. See Issue [#30](https://github.com/xebia/mobilehacktools/issues/30) reported by [@TheDauntless](https://github.com/TheDauntless). When you are on High Sierra you need to do:

```
  chgrp -R admin /usr/local/*
  chmod -R g+w /usr/local/*
```

and otherwise you can follow [this fix](https://gitlab.com/alyda/dotfiles/snippets/19654).

## Contribution

Does something not work? Create an issue, or even better: create a pull-request!

## Special thanks to

[@clviper](https://github.com/clviper) (reviewing), [@andreaslindeboom](https://github.com/andreaslindeboom) for a lot of ansible improvements, [@meetinthemiddle-be](https://github.com/meetinthemiddle-be) for testing & [@sushi2k](https://github.com/sushi2k) for contributing & [@hierynomus](https://github.com/hierynomus) for fixing travis issues & [@RiieCco](https://github.com/RiieCco) for motivating me to get the project started.
[@geerlingguy](https://github.com/geerlingguy) for creating awesome Ansible roles that speeded up the development tremendously.
Xebia, as a company from which I used an private repo to start hacking at the project.
My wife for supporting me in doing mobile security open source projects in my spare time.
