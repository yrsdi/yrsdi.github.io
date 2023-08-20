---
published: true
layout: post
title: "Menjalankan MongoDB dengan Podman"
date: 2023-08-12 21:57
comments: false
categories: 
- container
- podman
- mongodb
---


Untuk manjalankan Mongodb dengan Podman pastikan kalian sudah menginstall [podman](https://podman.io/docs/installation). Berikut adalah langkah-langkahnya :


[Menjalankan MongoDB dengan Podman](https://www.yadirosadi.com/images/uploads/2023/podman-logo.png)

<!--more-->
### 1. Ambil *Images* yang paling update 

```
$ sudo podman pull mongo

```
### 2. Pastikan *Images* sudah didapatkan

```
$ sudo podman image ls

```
### 3. Terlebih dulu buatlah *directory* untuk menyimpan data, *in case* kalian men-delete container, kalian masih mendapati datanya tersimpan.

```
$ sudo mkdir ~/mongodb_container/data && cd data

```
### 4. Buat *MongoDB Instance* tanpa *Authentication*

```
$ sudo podman run -dt --name mongo_podman -p 27017:27017 -v '/home/yrsdi/mongodb_container/data:/data/db:Z' docker.io/library/mongo:latest

```

* --name: nama dari container
* -d : untuk menjalankan container di *background mode*
* -p 27017:27017: *mapping* `port 27017` ke *host* `port 27017` dalam *container*
* -v : membuat data penampung yang digunakan oleh container

### 5. Membuat koneksi ke MongoDB container dan membuat `root` user

```
$ sudo podman exec -it mongo_podman mongosh
```

- menampilkan database

```
> show dbs;
admin   0.000GB
config  0.000GB
local   0.000GB
> use admin
> db.createUser(
 {
    user:"root",
    pwd: "root$1234",
    roles: ["root"]
 }
);
Successfully added user: { "user" : "root", "roles" : [ "root" ] }

```
### 6. Delete container dan buat kembali dengan otenkikasi

```
$ sudo podman ps

CONTAINER ID  IMAGE                                 COMMAND     CREATED      STATUS          PORTS                     NAMES
3c17652400g4  docker.io/library/mongo:latest                  3 hours ago  Up 3 hours ago  0.0.0.0:27017->27017/tcp  mongo_podman

```
- Stop dan remove containernya

```
$ sudo podman stop mongo_podman
$ sudo podman rm mongo_podman

```
- Buat kembali container dengan otentikasi

```
$ sudo podman run -dt --name mongo_podman_auth -p 27017:27017 -v '/home/yrsdi/mongodb_container/data:/data/db:Z' docker.io/library/mongo:latest --auth

```
- Kemudian kalian coba testing untuk login mongodb container

```
$ sudo podman exec -it mongo_podman_auth mongosh -u "root" -p "root$1234"

```