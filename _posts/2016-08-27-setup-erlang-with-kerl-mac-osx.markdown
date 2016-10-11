---
layout: post
title: "Install & Setup Local Erlang Environment with Kerl on Mac OS X"
date: 2016-08-27 19:45
comments: true
categories: 
- programming
---

To install erlang on Mac OSX is so easier, you just go to download from this site and installing it by one click or using homebrew by using `brew install erlang` command and tada your erlang will live on your system. But Installing by using it. It will force you to have only one version of the language to use at any point in time, when you need a specific language version of erlang for one of your projects, you will have to break. Versioned language management is the way to avoid the hassle of it.

Kerl is a versioned management tool to building and installing of Erlang/OTP instances. Here are Prerequisites, before installing it on Mac OS X.

* XCode Developer Tools
* Homebrew – Package Manager

<!--more-->

If you are running OS X 10.9 (Mavericks) or Later, you may need to install autoconf. Run below command to check the presence of it on your terminal:

```
$ which autoconf 
```
If the returns like below, you are already to install kerl

```
$ /usr/local/bin/autoconf
```

If the returns is autoconf not found, run this command to install it :

```
$ brew install autoconf
```
Once you’ve installed the necessary dependencies found in Mac OS X Prerequisites. Next, the first thing to do is get kerl and installing it.

### Install Kerl ###

you can get kerl from github source using curl

```
$ curl -O https://raw.githubusercontent.com/yrashk/kerl/master/kerl
```
and then move to `local/bin`

```
$ mv kerl /usr/local/bin/
```
and make it executeable

```
$ chmod a+x /usr/local/bin/kerl
```

you can view and see what kerl can do

```
$ kerl
```

Which gives

```
erl: build and install Erlang/OTP
usage: /usr/local/bin/kerl [options ...]

Command to be executed

Valid commands are:
build Build specified release or git repository
install Install the specified release at the given location
deploy Deploy the specified installation to the given host and location
update Update the list of available releases from erlang.org
list List releases, builds and installations
delete Delete builds and installations
active Print the path of the active installation
status Print available builds and installations
prompt Print a string suitable for insertion in prompt
cleanup Remove compilation artifacts (use after installation)
```
Before installing erlang, let’s see what releases list available

```
$ kerl list releases
```

This will give you output like the following:

```
R10B-0 R10B-10 R10B-1a R10B-2 R10B-3 R10B-4 R10B-5 R10B-6 R10B-7 R10B-8 R10B-9 R11B-0
R11B-1 R11B-2 R11B-3 R11B-4 R11B-5 R12B-0 R12B-1 R12B-2 R12B-3 R12B-4 R12B-5 R13A R13B01
R13B02-1 R13B02 R13B03 R13B04 R13B R14A R14B01 R14B02 R14B03 R14B04 R14B R14B_erts-5.8.1.1 R15B01 R15B02 R15B02_with_MSVCR100_installer_fix R15B03-1 R15B03 R15B R16A_RELEASE_CANDIDATE R16B01 R16B02 R16B03-1 R16B03 R16B 17.0-rc1 17.0-rc2 17.0 17.1 17.3 17.4 17.5 18.0 18.1 18.2 18.2.1
Run "/usr/local/bin/kerl update releases" to update this list from erlang.org
```
To install one, you need to choose a release version and come up with a name for out installation for it.

In this guide, we’re going to install R16B03 version as our primary erlang

```
$ kerl build R16B03 erlang-16B03
```

This will takes view minutes to complete, just wait for it.

> Note: that kerl supports passing options to the build so you can enable/disable various features. For more details, see the github README for kerl.

Once that’s done, it’s time to actually install it. Here, we use the name we chose when we built our particular Erlang. In this case, erlang-16b03:

```
$ kerl install erlang-16B03 /Users/erlang/R1603/
```

> Note: if you leave off the path, kerl will install Erlang in your current directory.

You can also install multiple Erlang version for that path

```
$ kerl list installations
```

which will gives output like below:

```
erlang-16b03 /Users/erlang
erlang-15B02 /Users/erlang
```

for a sanity check

```
$ which erl
```

if you get output with nothing result after run that command, you need to active the one of erlang that has installed.

```
$ . /Users/erlang/R16B03/activate
```

and check again erl

```
$ which erl
```

if no any error, the output will result like following

```
$ /Users/erlang/R16B03/bin/erl
```

To deactivate the current active version and change to other version use this command

```
$ kerl_deactivate
```

Now, you can play with erlang

```
$ erl

Erlang R16B03 (erts-5.10.4) [source] [64-bit] [smp:2:2] [async-threads:10] [kernel-poll:false]

Eshell V5.10.4 (abort with ^G)
1>
```


