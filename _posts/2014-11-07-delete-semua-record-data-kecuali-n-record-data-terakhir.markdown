---
layout: post
title: "Delete Semua record data kecuali N record data terakhir"
date: 2014-11-07 19:45
comments: true
categories: 
- programming
---

Setelah sekian lama ga nulis dan sharing. Kali ini saya coba sharing pengalaman sesuai dengan kebutuhan pekerjaan. karena pekerjaan kali ini banyak berkutat dengan query dan query terutama untuk Oracle dan MySQL. Contoh kasusnya adalah sebagai berikut:
Suatu tabel dalam suatu database memiliki beberapa record data, sebanyak N record data harus tetap ada dalam tabel tersebut, dimana setiap N record data baru terisi setiap 1 jam sekali dan data lamanya akan terhapus. lalu bagaimana querynya? (contoh kasus untuk MySQL)
Ada beberapa metode yang bisa kita lakukan. berikut adalah beberapa logic method yang bisa kita terapkan.

1.meng-count data pada tabel tersebut, hasilnya dikurangi N data yang akan di keep, kemudian selisihnya kita hapus, jika kita ilustrasikan querynya adalah sebagai berikut :

``` sql
DELETE FROM table
ORDER BY id ASC 
LIMIT ((SELECT COUNT(*) FROM table ) - N Data)

```

2.Kita buat subquery untuk mengambil data sebanyak N dan buat inisial tablenya (disini adalah a), setelah itu kita left join dan buat inisial b, kemudian relasikan a dan b, hasilnya kita delete dengan kondisi id untuk tabel b adalah NULL. ilustrasi querynya sebagai berikut

``` sql
DELETE c.*
FROM  table c
LEFT JOIN
        (
        SELECT  id
        FROM table a
        ORDER BY id DESC
        LIMIT N
        ) b
ON      a.id = b.id
WHERE   b.id IS NULL

```


3.Ambil data terakhir sebanyak N, hasilnya kita buat inisialisasi dengan nama lim, setelah itu delete semua record di tabel tersebut dengan kondisi dimana idnya bukan data N yang telah diambil

``` sql
DELETE FROM `table`
WHERE id NOT IN (
  SELECT id
  FROM (
    SELECT id
    FROM `table`
    ORDER BY id DESC
    LIMIT N
  ) lim
);

```

4.Ambil data sebanyak 1 dengan Offset N, hasilnya diambil kembali dan buat inisialisasi tabel, misal lim, setelah itu kita delete semua record pada tabel dengan kondisi dimana idnya adalah lebih kecil sama dengan data dari id yang sudah diperoleh.

``` sql

DELETE FROM `table`
  WHERE id <= (
    SELECT id
    FROM (
      SELECT id
      FROM `table`
      ORDER BY id DESC
      LIMIT 1 OFFSET N
    ) lim
  );

```

5.Metode ini logikanya hampir sama dengan metode ke-4. hanya saja menggunakan JOIN Clause, bukan WHERE clause. dalam metode ini kita tidak perlu lagi menyelect data yang telah dihasilkan untuk diinisialisasi

``` sql
DELETE
FROM 
       `table` AS p
   JOIN
       ( SELECT id 
         FROM `table` 
         ORDER BY id DESC
           LIMIT 1 OFFSET N
       ) AS lim
     ON p.id <= lim.id;

```
Dari ke 5 metode yang telah dijabarkan tersebut, hanya 4 metode yang bisa kita pergunakan yaitu (metode 2 s/d 5). Pertanyaannya mana yang paling efektif dan cocok untuk digunakan dalam berbagai kasus terutama berkaitan dengan masalah performance?
