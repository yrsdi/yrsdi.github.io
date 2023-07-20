---
published: false
layout: post
title: "Konsep Dasar Pemrograman Haskell"
date: 2023-07-08 19:46
comments: true
categories: 
- programming
- haskell
---

Haskell adalah salah satu bahasa pemrograman dengan paradigma fungsional, bahkan mungkin satu-satunya bahasa pemrograman yang fungsional murni.

Pemrograman fungsional berarti pemrograman dilakukan dengan berfokus pada pemetaan fungsi dan evaluasi ekspresi. Pemrograman fungsional didasarkan pada konsep matematis *Lambda Calculus*, dimana fungsi dianggap sebagai nilai dan tidak ada perubahan status *mutabel*. Pemrograman fungsional mendorong gaya pemrograman yang deklaratif, tanpa efek samping (*side effect*), dan berfokus pada komputasi yang didasarkan pada ekspresi matematika. 

Ciri dan konsep dasarnya :

1. Powerfull Strong Static Typing:

   Hal ini mengacu pada sistem tipe yang ketat dan tegas yang diterapkan pada semua ekspresi dan fungsi dalam bahasa tersebut. Berikut adalah penjelasan detail mengenai konsep ini beserta contohnya:

	**1.1 Tipe Statis**:
	Dalam Haskell, setiap ekspresi dan fungsi memiliki tipe yang ditentukan secara statis, yang berarti tipe tersebut ditentukan sebelum program dijalankan dan tetap konsisten sepanjang eksekusi program. Pemeriksaan tipe dilakukan secara statis pada saat kompilasi, yang memungkinkan banyak kesalahan terdeteksi sebelum program dieksekusi.

	**1.2 Tipe yang Kuat**:

	Tipe yang kuat dalam Haskell berarti bahwa sistem tipe menerapkan aturan yang ketat untuk memastikan kesesuaian tipe dalam operasi dan ekspresi. Ini berarti tidak diperbolehkan operasi yang tidak valid antara tipe yang berbeda, dan kesalahan tipe biasanya terdeteksi selama kompilasi. Tipe yang kuat membantu dalam mencegah kesalahan yang umum terkait tipe dan meningkatkan keamanan dan keandalan program.

	**Kelebihan Tipe Statis yang Kuat**:

	- Deteksi kesalahan sebelum eksekusi: 
	  Karena pemeriksaan tipe dilakukan secara statis pada saat kompilasi, banyak kesalahan tipe dapat terdeteksi sebelum program dieksekusi, menghindari potensi kesalahan saat runtime.
	- Pembacaan kode yang lebih jelas: 
	  Tipe statis yang kuat memungkinkan pemrogram untuk membaca kode dengan jelas dan memahami tipe data yang terlibat dalam operasi dan ekspresi.
	- Pemeliharaan kode yang mudah: 
	  Dengan tipe statis yang kuat, perubahan dalam kode yang melibatkan tipe dapat ditemukan secara langsung dan memaksa pengembang untuk memperbaiki kesesuaian tipe, sehingga memudahkan pemeliharaan kode dan refaktorisasi.
		
	Contoh Penggunaan Tipe Statis yang Kuat di Haskell:

	```
	add :: Int -> Int -> Int
	add x y = x + y

	square :: Double -> Double
	square x = x * x

	-- Pemanggilan fungsi dengan argumen yang tepat
	result1 = add 5 3       -- Hasilnya adalah 8
	result2 = square 2.5    -- Hasilnya adalah 6.25

	-- Contoh kesalahan tipe yang terdeteksi saat kompilasi
	-- result3 = add 5.0 3   -- Kesalahan tipe: Argumen pertama harus bertipe Int, bukan Float
	-- result4 = square "2"  -- Kesalahan tipe: Argumen harus bertipe Double, bukan String
	```
  
   Dalam contoh di atas, kita mendefinisikan dua fungsi: `add` dan `square`. Fungsi `add` menerima dua argumen bertipe `Int` dan mengembalikan hasil penjumlahan mereka. Fungsi `square` menerima argumen bertipe `Double` dan mengembalikan hasil kuadratnya.

   Ketika kita memanggil fungsi-fungsi ini dengan argumen yang tepat, seperti `add 5 3` atau `square 2.5`, tidak ada kesalahan tipe yang terjadi dan program dapat dikompilasi dan dijalankan dengan benar.

   Namun, jika kita mencoba memanggil fungsi dengan argumen yang tidak sesuai dengan tipe yang diharapkan, seperti `add 5.0 3` atau `square "2"`, kesalahan tipe terdeteksi saat kompilasi. Ini menunjukkan kekuatan tipe statis yang kuat dalam Haskell dalam mencegah kesalahan tipe yang umum.

2. Lazy Evaluation:

   Haskell menggunakan evaluasi lazim, yang berarti ekspresi dievaluasi hanya saat nilainya diperlukan. Ini berbeda dari evaluasi eagerness yang umumnya digunakan dalam bahasa pemrograman imperatif. Evaluasi lazim memungkinkan evaluasi yang tertunda dan memungkinkan pemrogram untuk mengoperasikan dengan struktur data tak terbatas atau tak terhingga secara efisien.

   ```
   lazyAdd :: Int -> Int -> Int
   lazyAdd x y = x + y

   main :: IO ()
   main = do
     let result = lazyAdd (2 + 3) (4 * 5)
     putStrLn $ "Result: " ++ show result
```
	Dalam contoh tersebut, kita memiliki fungsi `lazyAdd` yang melakukan penjumlahan dua bilangan. Namun, perhatikan bahwa argumen `x` dan `y` memiliki ekspresi matematika yang rumit.

	Pada baris `let result = lazyAdd (2 + 3) (4 * 5)`, kita sebenarnya sedang melakukan evaluasi lazim. Meskipun kita bisa langsung mengevaluasi ekspresi `(2 + 3)` dan `(4 * 5)` secara eager (cepat), Haskell menggunakan evaluasi lazim untuk menunda evaluasi ekspresi ini sampai benar-benar diperlukan.

	Ketika kita mencetak result ke layar dengan menggunakan `putStrLn`, evaluasi ekspresi `(2 + 3)` dan `(4 * 5)` akan dilakukan, dan hasilnya akan dijumlahkan oleh fungsi `lazyAdd`.

	Ealuasi ekspresi (2 + 3) dan (4 * 5) ditunda sampai saat mereka benar-benar diperlukan dalam evaluasi lazyAdd. Ini menunjukkan evaluasi lazim dalam aksi, di mana ekspresi dievaluasi hanya saat nilai mereka benar-benar diperlukan.

	Contoh sederhana ini menunjukkan bagaimana evaluasi lazim dalam Haskell memungkinkan penundaan evaluasi dan mengoptimalkan kinerja dengan tidak mengevaluasi ekspresi yang tidak perlu. Evaluasi lazim memungkinkan kita untuk menulis kode yang lebih ekspresif dan efisien, terutama saat berurusan dengan ekspresi yang kompleks atau mahal secara komputasi.

3. Inferensi Tipe (Type Inference):

   Haskell memiliki sistem tipe yang kuat dan statis. Setiap ekspresi dan fungsi di Haskell memiliki tipe yang dideklarasikan sebelumnya. Haskell mendukung inferensi tipe, yang memungkinkan sistem tipe untuk secara otomatis menentukan tipe yang tepat untuk ekspresi yang diberikan. Haskell juga mendukung tipe polimorfik, yang memungkinkan kita untuk menulis kode yang berlaku untuk berbagai tipe data.

4. Pola Correspondence dan Matching:

   Haskell memiliki fitur pola correspondence yang kuat yang memungkinkan pemrogram untuk melakukan pencocokan pola (pattern matching) pada struktur data. Pencocokan pola memungkinkan pemrogram untuk mengekstraksi nilai dari struktur data, memisahkan kasus khusus, atau membangun struktur data yang kompleks. Ini memungkinkan pengkodean yang elegan dan ekspresif dalam banyak kasus.

5. Fungsi Tingkat Tinggi dan Kepustakaan (Library):

   Haskell mendukung fungsi tingkat tinggi, yang berarti fungsi dapat dianggap sebagai nilai dan digunakan sebagai argumen atau hasil dari fungsi lainnya. Ini memungkinkan pemrogram untuk menulis kode yang lebih pendek, lebih ekspresif, dan lebih modular. Haskell memiliki kekayaan kepustakaan (library) yang luas yang menyediakan banyak fungsi dan modul yang siap digunakan, membantu dalam pengembangan aplikasi secara efisien.

6. Monads dan Efek Samping Terkendali:

   Haskell menggunakan monad untuk mengendalikan efek samping, seperti interaksi dengan IO (Input/Output), keadaan mutabel, atau non-determinisme. Monad adalah konstruksi yang memisahkan kode yang melibatkan efek samping dari kode yang murni. Ini membantu dalam menjaga kejelasan dan keamanan dalam kode Haskell, sambil memungkinkan penanganan efek samping secara terkendali.

7. Penanganan Kesalahan (Error Handling):

   Haskell memiliki pendekatan yang kuat dalam penanganan kesalahan. Dalam Haskell, kesalahan diperlakukan sebagai nilai yang dapat dioperasikan dan dikombinasikan dengan menggunakan tipe data seperti Maybe dan Either. Ini membantu dalam menangani kesalahan dengan lebih jelas, aman, dan ekspresif.

4. Pure Functions dan Immutabillity : Pure function maksudnya adalah Karena konsep dari bahasa pemogramannya lebih dekat dengan kosep matematika, dimana ciri umumnya adalah tidak ada efek samping. Sedangkan immutabillity maksudnya ketika sebuah variabel terdefinisi dengan value tertentu, variabel tersebut tidak bisa diubah.

5. Concurrency and Parallelism: 


