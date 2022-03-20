---
published: true
layout: post
title: Belajar Pemrograman Clojure
date: 2021-08-30  09:00
comments: true
categories: 
- clojure
- programming
---

![](https://i.imgur.com/Af51QU8.png)

### Sedikit Sejarah Tentang Clojure
* Nama Clojure berasal dari plesetan konsep pemrograman 'closure', yang menggabungkan huruf C, L, dan J untuk C#, Lisp, dan Java, dimana ke-3 bahasa pemrograman tersebut memiliki pengaruh besar pada desain Clojure.
* Di buat dan di desain oleh Rich Hickey.
* Rilis pertama kali pada 16 oktober 2007.
* Hickey menginginkan Lisp modern untuk pemrograman fungsional yang bisa bersimbiosis dengan platform Java yang sudah established, dan dirancang untuk konkurensi.

### Apa itu bahasa pemrograman Clojure ?
* Clojure adalah bagian dari keluarga Lisp, yg memanfaatkan dan mempertahankan fitur2 terbaik dari Lisp-1.
* Di Hosted di JVM (Java Virtual Machine).
* Dynamic, general-purpose programming language.
* Lebih dominan sebagai functional programming language tetapi tidak pure seperti hal Haskell.
* Memiliki Struktur data yang persisten dan tidak dapat diubah (Immutable), tetapi, jika Mutable state dibutuhkan, clojure menawarkan sistem memori transaksional dan sistem Agen reaktif yang memastikan desain multi-thread yang bersih.
* Compiled language.
* Menganut filosofi 'code-as-data' (Homoiconic), seperti Lisp dialek lainya.
* Powerful macro system.

<!--more-->

### Kenapa harus belajar Clojure ?
* Dibangun dari perpaduan unik dan fitur-fitur terbaik dari sejumlah bahasa pemrograman : C#, Lisp, Ruby, Python, Java, Haskell, dll.
* Bisa menggunakan library Java apapun begitupun sebaliknya (vice versa), tanpa mengurangi performance.
* Java runtime adalah clojure runtime.
* Clojure support makro dan kemampuanya terhadap metaprogramming.
* simplicity and powerfull.
* Easy, fast Java interoperability.
* Mengambil kekuatan dari Lisp, *code as data*.
* Elegan, expresif code
* Functional programming to encourage reusable, correct code.
* Homoiconicity, maksudnya kode yg ditulis di encode sebagai struktur data.
* Clojure merupakan superset dari EDN (*Extensible Data Notation*), sebuah format data transfer seperti halnya JSON, Manfaat utama EDN atas JSON dan YAML adalah dapat diextend.

### Instalasi Clojure
Untuk mencoba syntak dari clojure ada beberapa cara:

**1. Online plyground**

Ada banyak online playground yg bisa kita gunakan untuk mencoba sintak dari clojure ini, diantaranya; 

*  [replit.com](https://replit.com/@KirillRyabin/clojure-playground)
*  [codebeautify.org](https://codebeautify.org/alleditor/cb224598)
*  [code.labstack.com](https://code.labstack.com/clojure)
*  [app.klipse.tech](http://app.klipse.tech)
    
**2. Instalasi di lokal PC/laptop.**

   Instalasi di PC/Laptop diperlukan java runtime, jadi pastikan java sudah terinstall sebelum instalasi clojure. Namun jika anda menggunakan leiningen, saat instalasi java secara otomatis akan ikut terinstall.

```
$ java --version
$ openjdk 11.0.2 2019-01-15
OpenJDK Runtime Environment 18.9 (build 11.0.2+9)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.2+9, mixed mode

```   
   Ada beberapa metode instalasi:
   * Menggunakan metode dari offcialnya [clojure.org](https://clojure.org/guides/getting_started)
   * Instalasi langsung dengan [leiningen.org](https://leiningen.org). Leiningen adalah projek automation, support integrasi ke maven. Leiningen menangani manajemen dan dependensi dari projek package dan dikonfigurasi menggunakan sintaks Clojure itu sendiri.
   * Menggunakan asdf version manager [asdf-vm.org](https://asdf-vm.com)

Saya sendiri merekomendasikan untuk menggunakan cara ke-3, alasannya karena asdf support hampir semua bahasa pemrograman dan mudah untuk manage versi jika ingin switch ke versi yg lebih rendah atau tinggi dan mudah untuk instalasi tentunya. Kalian bisa juga install java & leiningen menggunakan asdf ini.

Jadi, pastikan sudah terinstall asdfnya

```
$ asdf --version
$ v0.8.1
```

Misal disini kita kan coba untuk install leiningen

* Tambahkan dulu pluginnya

```
$ asdf plugin-add leiningen
```

* View versi yg tersedia

```
$ asdf list-all leiningen
```

* Pilih versi yg akan kita install

```
$ asdf install leiningen 2.9.6 
```

* Set config, bisa setting untuk semua kebutuhan (global) atau untuk kebutuhan tertentu (local)

```
$ asdf global leiningen 2.9.6
```

* Pastikan leiningan sudah terinstall

```
$ lein --version
$ Leiningen 2.9.6 on Java 11.0.2 OpenJDK 64-Bit Server V
```

* Jika sudah dipastikan leiningan sudah terinstall dengan benar, kita bisa mulai bermain.

```
$ lein repl
$ nREPL server started on port 52289 on host` `127.0.0.1 - nrepl://127.0.0.1:52289
    REPL-y 0.4.4, nREPL 0.8.3
    Clojure 1.10.1
    OpenJDK 64-Bit Server VM 11.0.2+9
        Docs: (doc function-name-here)
             (find-doc "part-of-name-here")
      Source: (source function-name-here)
     Javadoc: (javadoc java-object-or-class-here)
        Exit: Control+D or (exit) or (quit)
     Results: Stored in vars *1, *2, *3, an exception in *e
    user=>
```

### Membuat Proyek baru
Untuk memulai membuat proyek baru menggunakan leiningan, ada baiknya kita tau beberapa template proyek yang bisa   kita gunakan sesuai tujuan dari proyek yang akan kita buat. 

Ada beberapa opsi template yang bisa digunakan, diantaranya:

* **app** – Digunakan untuk membuat aplikasi
* **default** – Digunakan untuk membuat struktur proyek umum, biasanya untuk membuat library
* **plugin** – Digunakan untuk membuat Plugin Leiningen
* **template** – Digunakan untuk membuat template Leiningen baru.

Ok, jika kita sudah paham, langsung saja kita buat simple project

```
$ lein new app hello-world
```
Setelah menjalankan perintah tersebut, sekejap project template clojure akan terbentuk
```
$ ls
hello-world
```
Jika kita expand, kita bisa lihat struktur projectnya seperti apa. Yang penting dan paling utama adalah `project.clj` , folder `src` dan `test` karena nantinya kita akan lebih sering ngoprek disini.

```
➜ tree hello-world
hello-world
├── CHANGELOG.md
├── LICENSE
├── README.md
├── doc
│   └── intro.md
├── project.clj
├── resources
├── src
│   └── hello_world
│       └── core.clj
└── test
    └── hello_world
        └── core_test.clj

6 directories, 7 files
```

`project.clj` merupakan manifest atau metadata yg berisi informasi terkait project tersebut, seprti license, dependensi, nama project, deskripsi project dll.

### Menjalankan Aplikasi
Untuk menjalankan aplikasi clojure, pastikan kita berada di project di direktori aplikasi yg sebelumnya kita buat, kemudian ketikan `lein run'.
Pada saat pertamakali menjalankannya, clojure akan download semua dependensi dari project kita sebelum menampilkan hasilnya.
```
➜  lein run
Hello, World!
```
### Menjalankan Unit Testing
Untuk menjalankan unit testing dengan perintah `lein test`

```
➜  hello-world lein test

lein test hello-world.core-test

lein test :only hello-world.core-test/a-test

FAIL in (a-test) (core_test.clj:7)
FIXME, I fail.
expected: (= 0 1)
  actual: (not (= 0 1))

Ran 1 tests containing 1 assertions.
1 failures, 0 errors.
Tests failed.
```
### Bermain dengan REPL
REPL (Read Eval Print Loop), Sesuai dengan pengertiannya, REPL adalah alat bantu untuk menjalankan langsung code kita dan menampilkan langsung hasilnya.

REPL bisa dijalankan dengan mengetikan perintah `lein repl`

```
➜ lein repl
nREPL server started on port 49770 on host 127.0.0.1 - nrepl://127.0.0.1:49770
REPL-y 0.4.4, nREPL 0.8.3
Clojure 1.10.1
OpenJDK 64-Bit Server VM 11.0.2+9
    Docs: (doc function-name-here)
          (find-doc "part-of-name-here")
  Source: (source function-name-here)
 Javadoc: (javadoc java-object-or-class-here)
    Exit: Control+D or (exit) or (quit)
 Results: Stored in vars *1, *2, *3, an exception in *e

hello-world.core=> (+ 3 5)
8
hello-world.core=> (* 3 5)
15
hello-world.core=> (+ (* 3 5) 5)
20
hello-world.core=>
```
### Memilih IDE text Editor dan plugin
Ada banyak text editor yang sudah mendukung clojure, yang paling dikenal diantaranya :
1. [IntelliJ] (https://cursive-ide.com/)+ Cursive
2. Emacs + Cider
3. VS Code + Calva
4. Atom + proto-repl
Dari beberapa text editor tersebut, mungkin adalah salah satu text editor yang menjadi daily use teman-teman. Jadi saran saya gunakan yang sudah pernah teman-teman gunakan sebelumnya, supaya teman-teman bisa fokus ke belajar clojurenya. Saya pribadi mengunakan VS Code atau sesekali menggunakan Emacs.

