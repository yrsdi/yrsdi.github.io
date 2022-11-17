---
layout: post
title: "Install & Setting up Elixir Environment"
date: 2016-09-03 07:05
comments: true
categories: 
- programming
---

### Introduction ###

Programming languages regularly release new versions. As a developer, I need to try that version without breaking our existing application in our local environment. The solution is using the version manager tool. version manager helps developers switch between versions easily, several languages have version managers (like SDKman for Java, NVM for Node.js, or Rbenv/RVM for Ruby, etc). 

Too many tools in our local environment is another obstacle. in my case, I need one tool that can be handling multiple programming languages in multiple versions. so my choice is ASDF.

In this tutorial, you'll learn how to install specific versions of Erlang/OTP and Elixir and use the ASDF as version manager.

### Install asdf ###

[asdf](https://github.com/asdf-vm/asdf) is a version manager tool that supports various programming languages including Ruby, Node.js, Erlang, Elixir and more. Before install asdf you need to install the curl and git utilities as prerequisites.

```
$ brew install coreutils curl git  # on macOS with Homebrew
$ sudo apt install curl git        # on Linux

```
After the prerequisites installed, now ready to install the ASDF:

```
$ git clone https://github.com/asdf-vm/asdf.git ~/.asdf

```
Depending on your OS, in this guide I use OSX. if you are using OSX, open `~/.bash_profile` and put this path. If you are on linux, put on `~/.bashrc`

<!--more-->

```
. $HOME/.asdf/asdf.sh
. $HOME/.asdf/completions/asdf.bash
```

Run following command to make sure, It has already install properly

```
$ asdf -v
```
Output 

```
version: 0.1

MANAGE PLUGINS
  asdf plugin-add <name> <git-url>     Add git repo as plugin
  asdf plugin-list                     List installed plugins
  asdf plugin-remove <name>            Remove plugin and package versions
  asdf plugin-update <name>            Update plugin
  asdf plugin-update --all             Update all plugins


MANAGE PACKAGES
  asdf install <name> <version>        Install a specific version of a package or,
                                       with no arguments, install all the package
                                       versions listed in the .tool-versions file
  asdf uninstall <name> <version>      Remove a specific version of a package
  asdf which <name>                    Display version set or being used for package
  asdf where <name> <version>          Display install path for an installed version
  asdf local [name]                    Display a package local version
  asdf local <name> <version>          Set the package local version
  asdf global [name]                   Display a package global version
  asdf global <name> <version>         Set the package global version
  asdf list <name>                     List installed versions of a package
  asdf list-all <name>                 List all versions of a package


UTILS
  asdf reshim <name> <version>         Recreate shims for version of a package


"Late but latest"
-- Rajinikanth
```

### Install Erlang & Elixir ###
To install Erlang & Elixir. First think first is to get plugin for erlang & elixir. Copy & paste following command on your terminal

```
$ asdf plugin add erlang
$ asdf plugin add elixir

```

Make sure plugin that has added in the list

```
$ asdf plugin-list
```
output 

```
elixir
```

To see Elixir versions which are available

```
$ asdf plugin-update elixir
$ asdf list-all elixir 
```

### Manage Version for Elixir ###

If plugin already added in the list, now you can install it. use this format `asdf install <name> <version`

in this case, I use 1.2.4 version of elixir

```
$ asdf install elixir 1.2.4
```

### Set Current Version ###

To set current version, you can set as local or global

```
asdf global <name> <version>
asdf local <name> <version>

```
In this case I set it on global
```
$ asdf global elixir 1.2.4
```
global writes the version to $HOME/.tool-versions.

local writes the version to $PWD/.tool-versions, creating it if needed.

You can check to make sure it has work properly. If no problem, the result as seen below

```
elixir -v
Erlang/OTP 18 [erts-7.2] [source] [64-bit] [smp:2:2] [async-threads:10] [kernel-poll:false]

Elixir 1.2.4
```

