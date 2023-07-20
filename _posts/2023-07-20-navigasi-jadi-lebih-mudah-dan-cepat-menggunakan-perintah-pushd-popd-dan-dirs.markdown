---
published: true
layout: post
title: "Navigasi jadi lebih mudah dan cepat menggunakan perintah pushd, popd dan dirs di Linux."
date: 2023-07-19 19:46
comments: true
categories: 
- Linux
---


## Pendahuluan:

Bernavigasi di sistem file Linux dengan efisien adalah kunci bagi pengguna pemula maupun berpengalaman. Perintah bawaan "`pushd`," "`popd`," dan "`dirs`" menyediakan alat bantu kuat untuk menyederhanakan navigasi direktori dan mempermudah alur kerja. Dalam artikel ini, kita akan menjelajahi fungsionalitas perintah ini, bagaimana cara kerjanya secara bersama-sama, dan skenario praktis di mana mereka dapat meningkatkan produktivitas secara signifikan.

1. Pushd:
Perintah "`pushd`" adalah singkatan dari "push directory," dan tujuan utamanya adalah mengubah direktori sambil tetap menjaga tumpukan direktori. Saat "`pushd`" digunakan, ia akan beralih ke direktori yang ditentukan dan mendorong direktori saat ini ke dalam tumpukan. Ini memungkinkan pengguna dengan mudah kembali ke direktori sebelumnya dengan "`popd`" atau beralih antara beberapa direktori dengan mudah.

Penggunaan:
Untuk menggunakan "`pushd`," cukup ketik "`pushd`" diikuti dengan jalur direktori yang diinginkan. Misalnya:
```bash
pushd /path/ke/direktori
```
Setelah menjalankan perintah ini, Anda akan berpindah ke direktori yang ditentukan, dan direktori sebelumnya akan disimpan dalam tumpukan direktori.

2. Popd:
Perintah "`popd`" melengkapi "`pushd`" dengan memungkinkan pengguna untuk kembali ke direktori sebelumnya dalam tumpukan. Ketika "`popd`" dipanggil, ia menghapus direktori teratas dari tumpukan dan mengubah direktori saat ini menjadi direktori teratas baru.

Penggunaan:
Untuk menggunakan "`popd`," cukup ketik:
```bash
popd
```
Perintah ini akan mengubah direktori saat ini kembali ke direktori yang berada di bagian atas tumpukan.

3. Dirs:
Perintah "`dirs`" menyediakan cara sederhana untuk melihat tumpukan direktori. Perintah ini menampilkan daftar direktori yang disimpan dalam tumpukan, menunjukkan direktori teratas dengan tanda "+" dan daftar direktori sesuai urutan penambahan ke dalam tumpukan.

Penggunaan:
Untuk melihat tumpukan direktori, ketik:
```bash
dirs
```
Keluaran akan menampilkan daftar direktori dalam tumpukan, memungkinkan Anda melihat riwayat navigasi dengan sekilas.

4. Contoh Praktis:

a. Beralih antara Dua Direktori:
Gabungan "`pushd`" dan "`popd`" sangat berguna ketika berpindah bolak-balik antara dua direktori. Misalnya:
```bash
pushd /path/ke/direktori1
# Bekerja di direktori1
pushd /path/ke/direktori2
# Bekerja di direktori2
popd
# Kembali ke direktori1
```
Dengan cara ini, Anda dapat dengan mudah beralih antara "*direktori1*" dan "*direktori2*" tanpa harus mengetik jalur lengkap berkali-kali.

b. Membuat Struktur Direktori Bertingkat:
"`pushd`" dan "`popd`" sangat berguna untuk membuat struktur direktori bertingkat. Misalnya:
```bash
mkdir -p parent/child/grandchild
pushd parent
# Bekerja di direktori 'parent'
pushd child
# Bekerja di direktori 'child'
pushd grandchild
# Bekerja di direktori 'grandchild'
popd
# Kembali ke direktori 'child'
popd
# Kembali ke direktori 'parent'
```

## Kesimpulan:
"`Pushd`," "`popd`," dan "`dirs`" adalah alat tak tergantikan untuk mengelola navigasi direktori secara efisien dan cepat di Linux. Dengan memanfaatkan perintah ini, pengguna dapat beralih antara direktori dengan lancar dan menjaga riwayat perubahan direktori. Baik Anda sedang mengerjakan proyek kompleks atau melakukan operasi berkas sederhana, perintah-perintah ini dapat secara signifikan meningkatkan produktivitas dan pengalaman Linux secara keseluruhan.


