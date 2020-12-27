---
layout: post
title: My Linux Backpack
comments: true
tags : ["personal","linux"]
---
![my linux backpack](https://i.imgur.com/5Nc4PL2.jpg)(photo grabbed from internet)

I'm a MacOS guy for several years until my MBP died on me last year and haven't got a replacement for it. However, my 8 to 5 job revolves around Windows. Recently, Win10 has been working great for me. But, I always wanted a development environment that is different from what I use every day at work, change of scenery of some sort. So for 3 to 4 months I was reviewing the different flavors of Linux has to offer. Ubuntu has always got a soft spot for me, I have been on and off the platform since 2006. However, the current interface has put me off. Either my system lags using it or I just need a more efficient OS. I'm not into games or the fancy graphics stuff anyway, I just need a reliable development machine. Eventually, I have decided to go with Bunt, an Ubuntu flavor utilizing a more resource friendly xfce interface. I never looked back since then.

Fast forward to now, I'm moving to the  Focal Fossa 20.04 LTS release. I finally found time to migrate and wanted to start with a clean install. And with that, I have to re-install everything I needed. Been looking for a way to automate this process but for now I'll go the manual route.

## What do I need ?
As I have mentioned, I just need my development tools available and ready to roll. Let me list them down:

The foundations
- gcc
- wget
- curl
- git

The dev kits
- dotnet
- python
- ruby

Editors and others
- vscode
- oh my zsh
- typora
- azure cli
- powershell core

## Lets get down to business

First order of business is to get all the foundations setup. Without these, I cant seem to progress any further.

- **gcc** - the GNU Compiler Collection that includes a lot of libraries for the basic languages in Linux (e.g. C , C++)
```bash
# check if you have gcc installed
$ gcc --version

# install if needed, this will include gcc, g++ and make
$ sudo apt update
$ sudo apt install build-essential

# install the manual
$ sudo apt-get install manpages-dev
```
- **wget** - this is a command-line utility for downloading files from the web. In most cases, if you will be install other packages later on, wget will come in handy.
```bash
# check if you have wget installed
$ wget --version

# install if needed
$ sudo apt update
$ sudo apt install wget
```
- **curl** - is a command-line utility for transferring data from or to a remote server and just like wget, you will be needing this later if you intend to install additional packages.
```bash
# check if you have curl installed
$ curl --version

# install if needed
$ sudo apt update
$ sudo apt install curl
```
- **git** - in this era of open source and gitlabs and githubs, you wont survive without git!
```bash
# check if you have git installed
$ git --version

# install if needed
$ sudo apt update
$ sudo apt install git
```

Then we go to the programming languages I use. 

- **dotnet** - I am a developer that mostly used Microsoft technology ( dotNet, C#, VB.Net  and many more) for my entire developers life. I have longed for using C# in Linux since the day of Mono 1.0. I am just glad with this new dotnet revolution embracing cross platform development.

  Ubuntu support for .NET 5 can be found on this (page.)[https://docs.microsoft.com/en-us/dotnet/core/install/linux-ubuntu]

```bash
# check if you have dotnet installed
$ dotnet --version

# install here
# add the Microsoft package signing key to your list of trusted keys and # add the package repository
$ wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
$ sudo dpkg -i packages-microsoft-prod.deb

# install the SDK
$ sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0

#install the runtime
$ sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```
- **python** - Next to dotnet, python is my next go to language. Python usually comes out of the box with latest Xubuntu. But if you need to, see the steps below.
```bash
# check if you have python installed
$ python --version

# if you must
$ sudo apt update
$ sudo apt install python3.8
```
- **ruby** - Not for actual development purpose for now, I just need it for my blog. Trying out Jekyll as I move on from blogspot.
```bash
# check if you have ruby installed
$ ruby --version

# if you must
$ sudo apt update
$ sudo apt install ruby-full
```
- **more?** - Indeed! Rust and Golang to follow.

Now, we go to my tools.

- **vscode** - My editor of choice. I used the Software app to install VSCode.
- **oh my zsh** - I work with the terminal evernow and then, it is just fitting to use "oh my zsh" with "agnoster" as my cli.
```bash
# make sure zsh is installed
$ zsh --version

# install if you must
$ sudo apt-get update
$ sudo apt upgrade

$sudo apt install zsh

# install the needed powerline font
sudo apt-get install powerline fonts-powerline

# clone and install oh-my-zsh
$ sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

# customize your theme, I use agnoster :)
```
- **typora** - Again, for my blog!
```bash
$ wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

# add Typora's repository
$ sudo add-apt-repository 'deb https://typora.io/linux ./'
$ sudo apt-get update

# install typora
$ sudo apt-get install typora
```
- **azure cli** - For my cloud works. Azure has been my choice, though, I have the option to use Alibaba Cloud as well.
```bash
$ curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```
- **powershell core** - As I have mentioned before, I'm a MS guy, so.
```bash
$ wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
$ sudo dpkg -i packages-microsoft-prod.deb

sudo apt update
sudo apt -y install powershell
```

## What's next?
For basic development work I can roll with the setup above. However, my list above is not complete. Obviously, docker is missing. For my machine, I chose not to install a database directly on the system. I will go with a cloud approach or a container. But for now, I'm all set. 

How about you? Whats on  your Linux backpack?

