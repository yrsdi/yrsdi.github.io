---
published: true
layout: post
title: "Begini cara yang benar install Python di Ubuntu"
date: 2024-05-02 18:00
comments: false
categories: 
- programming
---

## Pendahuluan

Ada beberapa cara menginstall python, tapi yang menurut saya paling benar adalah dengan menggunakan `pyenv` . Kenapa paling benar, karena selain bisa install multi version, bisa di set lokal ataupun global,dan bisa juga set *environment* nya dengan sangat mudah.

<!--more-->

## Persyarat Awal

Adapun persyarat awal yang perlu dipersiapkan sebelum install python, pastikan *package* di bawah ini sudah terinstall (*jika belum, silakan di install*) :

`git,curl,build-essential,python3-openssl,libssl-dev,zlib1g-dev,libbz2-dev,libsqlite3-dev,llvm,libncurses5-dev,libncursesw5-,xz-utils,tk-dev,libffi-dev,liblzma-dev`

### 1. Install *Package*
	
```
sudo apt install git
sudo apt install curl
sudo apt-get install build-essential
sudo apt install python3-openssl
sudo apt install -y libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev 
```

### 2. Install `pyenv`

`curl https://pyenv.run | bash`

Tambahkan code berikut diakhir baris `$HOME/.bashrc`
```
export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
Reload terminal dengan command `bash` atau tutup dan open kembali untuk me-*refresh* perubahan yg sudah ditambakan sebelumnya. Seharusnya setelah itu anda bisa menjalankan *command* `penv` di terminal anda. 

```
yardi@X230:~$ pyenv 
pyenv 2.4.0
Usage: pyenv <command> [<args>]
Some useful pyenv commands are:
activate    Activate virtual environment
commands    List all available pyenv commands
deactivate   Deactivate virtual environment
doctor      Verify pyenv installation and development tools to build pythons.
exec        Run an executable with the selected Python version
global      Set or show the global Python version(s)
help        Display help for a command
hooks       List hook scripts for a given pyenv command
init        Configure the shell environment for pyenv
install     Install a Python version using python-build
latest      Print the latest installed or known version with the given prefix
local       Set or show the local application-specific Python version(s)
prefix      Display prefixes for Python versions
rehash      Rehash pyenv shims (run this after installing executables)
root        Display the root directory where versions and shims are kept
shell       Set or show the shell-specific Python version
shims       List existing pyenv shims
uninstall   Uninstall Python versions
update      Update pyenv, its plugins including the list of available versions
--version   Display the version of pyenv
version     Show the current Python version(s) and its origin
version-file   Detect the file that sets the current pyenv version
version-name   Show the current Python version
version-origin   Explain how the current Python version is set
versions    List all Python versions available to pyenv
virtualenv   Create a Python virtualenv using the pyenv-virtualenv plugin
virtualenv-delete   Uninstall a specific Python virtualenv
virtualenv-init   Configure the shell environment for pyenv-virtualenv
virtualenv-prefix   Display real_prefix for a Python virtualenv version
virtualenvs   List all Python virtualenvs found in `$PYENV_ROOT/versions/*'.
whence      List all Python versions that contain the given executable
which       Display the full path to an executable
```

**Commands overview :**

Berikut adalah penjelasan untuk *command* yang akan sering digunakan
	- pyenv install: To install a new Python version
	- pyenv update: To update pyenv
	- pyenv virtualenv: To create a new Python virtual environment.
	- pyenv activate: To activate a previously created virtual environment.
	- source deactivate: To deactivate the virtual environment currently in use.
	- pyenv uninstall: To uninstall a virtual environment or Python version.
        
Setelah dipastikan `pyenv` terinstall dengan benar. Kalian perlu test apakah *command*  `pyenv virtualenv` dapat dijalankan dengan benar. Ketika dijalankan seharusnya akan menghasilan `no virtualenv name given` . 

```
yardi@X230:~$ pyenv virtualenv
pyenv-virtualenv: no virtualenv name given.
```
Ini menandakan bahwa *environment* belum dibuat. sebelum kita membuat dan menentukan namanya, Kita perlu menginstall python-nya terlebih dulu. 

### 3. Install Python

Dengan menggunakan `pyenv` kalian bisa install python dengan beberapa versi yang bisa kita tentukan. Katakan kita akan menginstall versi 3.12.3. 

**Me-list daftar versi python yang tersedia**
```
pyenv install -l
```
**Menentukan dan menginstall python**

```
pyenv install 3.12.3
```
```
yardi@X230:~$ pyenv install 3.12.3
Downloading Python-3.12.3.tar.xz...
-> https://www.python.org/ftp/python/3.12.3/Python-3.12.3.tar.xz
Installing Python-3.12.3...
Installed Python-3.12.3 to /home/yardi/.pyenv/versions/3.12.3
```

Setelah python berhasil terinstall, tentukan apakah akan di terapkan sebagai *local* atau *global*. *global* maksudnya versi ini akan berlaku untuk semua *environtment* , jika *local* berarti versi yang ditentukan hanya diterapkan untuk *environment* tertentu.

Katakan kita akan menerapkannya kesemua *environment*

```
pyenv global 3.9.7
```

### 4. Membuat *Virtual Environment* 

Setelah python berhasil di install dengan versi yang telah kita tentukan, kini saatnya untuk membuat sebuah *environment*. Katakan kita ingin membuat untuk kebutuhan testing atau development.
 	
```
pyenv virtualenv python 3.12.3 dev_env
```
Terapkan *environtment* yang telah kita buat dengan command berikut 
```
pyenv activate dev_env
```

Setelah python dan environmentnya berhasil terbuat, saatnya memulai coding dengan python. Happy Coding ya !!