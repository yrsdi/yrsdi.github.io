---
published: false
---
---
layout: post
title: "WARNING: IPython History requires SQLite, your history will not be saved"
date: 2018-07-25 06:45
comments: true
categories: 
- python
---

Recently, i've got warning message while compiling python code on Emacs after install _ipython_. Here are the step, how to fix it.
1. Install **package libsqlite3-dev** (_sudo apt install libsqlite3-dev_).
2. Rebuild your python installation. Since i use [asdf](https://github.com/asdf-vm/asdf) for installing python : _asdf uninstall python 3.x.x_ & _asdf install python 3.x.x_   

