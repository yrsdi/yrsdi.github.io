---
published: true
layout: post
title: "Install Homebrew di Linux Ubuntu 20.04 LTS"
date: 2023-01-08 07:00
comments: true
categories: 
- brew
- ubuntu
- package manager
---

[Homebrew](https://docs.brew.sh/) adalah package manager yang awalnya dikembangkan untuk Mac OSX dan menjadi package manager yang populer setalahnya. Homebrew saat ini tidak hanya tersedia di lingkungan OSX tetapi bisa juga di install di Linux dan Windows (WSL).

Bagi teman-teman yang terbiasa di linkungan OSX dan menggunakan homebrew sebagai package manager, akan sangat membantu ketika beralih ke linux atau Window (WSL).

Alasan menggunakan homebrew selain flexibelitasnya adalah karena Homebrew dirancang untuk menyediakan fungsionalitas per user, dapat di install di home direktori teman-teman sebagai <i>third-party</i> yang artinya tidak perlu menggunakan `sudo` saat proses instalasi packagenya. Homebrew juga dapat digunakan bersama package manager bawaan dari OS tanpa menimbulkan konflik.

<!--more-->

Dalam tutorial kali ini, akan di jelaskan cara instalasi dan cara menggunakan Homebrew di lingkungan Linux Ubuntu 20.4. Berikut adalah step by stepnya:

1). Buka terminal dan jalankan perintah berikut untuk proses update cache package managers :

```
$ sudo apt update
```
2). Install required packages yang diperlukan

```
$ sudo apt install build-essential curl file git

```
3). Download Homebrew installation script dengan menjalankan running perintah berikut:

```
$ curl -fsSL -o install.sh https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh

```
4). Install Script

```
$ /bin/bash install.sh
```

5). Tambahkan direktori instalasi Homebrew ke variabel lingkungan PATH teman-teman dengan menjalankan perintah berikut:

```
$ echo 'export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"' >>~/.bashrc

```
6). Reload konfigurasi

```
$ source ~/.bashrc
```
7). Cek proses instalasi sudah sesuai atau belum dengan menjalankan perintah berikut
```
$ brew --version  && brew doctor
```

Jika proses instalasi berhasil dan benar, Teman-teman akan melihat pesan berikut "Your system is ready to brew."

8). Instalasi package

```
$ brew install tree

```

Notes: Jika mendapatkan error berikut "permission denied" saat menjalankan perintah brew, coba jalankan sudo chown -R $USER:$USER /home/linuxbrew/.linuxbrew untuk mengubah owner dari direktori instalasi Homebrew.
