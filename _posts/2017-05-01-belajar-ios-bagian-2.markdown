---
layout: post
title: Belajar iOS Bagian 2
modified:
categories:
description: Belajar iOS Bagian 2
tags: [Swift, iOS, Xcode, alamofire, RxSwift, ObjectMapper]
image:
  background: abstract-3.png
comments: true
share: true
date: 2017-04-01T20:15:28+07:00
---

Hy jumpa lagi :D, artikel ini merupakan kelanjutan dari artikel [sebelumnya](http://atominik.com/1XUG){:target="_blank"}. Pada bagian kedua ini kita akan mencoba membuat hingga tahap menampilkan data :). Berikut adalah tahapan development yang akan kita lakukan.

* Apa Itu Storyboards, xib dan auto layout ?
* Membuat View Dan Navigation
* Membuat Service Dengan RxSwift
* Membuat Controller

## Apa Itu Storyboards, XIB dan Auto Layout ?

Storyboard merupakan salah satu fitur untuk melakukan desain aplikasi. Pada zaman dulu, developer hanya dapat menggunakan fitur XIB. Storyboard dan XIB sama - sama mempunyai fungsi untuk melakukan desain interface aplikasi, akan tetapi pada zaman sekarang developer apple merekomendasikan untuk menggunakan storyboard. Di dalam story board kita dapat menggunakan beberapa layer aplikasi seperti gambar berikut.

![Screen Shot 2017-04-30 at 9.50.18 PM.png](../images/Screen Shot 2017-04-30 at 9.50.18 PM.png)

Sehingga anda dapat mengetahui alur dari aplikasi tersebut secara detail. Berbeda dengan XIB, di dalam xib kita hanya dapat menggunakan 1 layer aplikasi saja seperti gambar berikut.

![Screen Shot 2017-04-30 at 9.52.35 PM.png](../images/Screen Shot 2017-04-30 at 9.52.35 PM.png)

Akan tetapi, ketika dihadapkan dengan suatu project besar maka kedua nya akan tetap bisa kita gunakan karena masing - masing dari mereka berdua mempunyai kelebihan dan kekurangan masing - masing misalnya jika kita menggunakan 1 storyboard dengan banyak layer maka proses membuka storyboard tersebut akan memakan waktu lama disebabkan banyak nya layer di dalam nya.

Bagaimana dengan auto layout ?

>>Auto Layout biasanya digunakan jika kita akan mendevelop aplikasi dengan berbagai ukuran layar

Biasanya kita tidak hanya terpaku di 1 ukuran layar saja, kita diharuskan untuk membuat untuk beberapa ukuran layar maka kita dapat menggunakan fitur auto layout. Fitur auto layout ini sangat mirip dengan fitur constraint nya android. Berikut adalah percobaan untuk membuat auto layout.

### Membuat Contoh Auto Layout

Silahkan buat sebuah project, lalu silahkan drag button dari menu kanan bawah seperti berikut.

![Screen Shot 2017-04-30 at 9.59.24 PM.png](../images/Screen Shot 2017-04-30 at 9.59.24 PM.png)

Setelah selesai, silahkan klik menu berikut lalu sesuaikan property nya seperti berikut.

![Screen Shot 2017-04-30 at 10.03.16 PM.png](../images/Screen Shot 2017-04-30 at 10.03.16 PM.png)

dan kemudian pilih add 4 constrains. Maka secara otomatis button kalian akan seperti berikut.

![Screen Shot 2017-04-30 at 10.04.59 PM.png](../images/Screen Shot 2017-04-30 at 10.04.59 PM.png)

Gambar diatas telah diubah warna backgroud dan warna tulisan nya, untuk mengubahnya, kamu dapat menggunakan menu seperti gambar berikut.

![Screen Shot 2017-04-30 at 10.06.40 PM.png](../images/Screen Shot 2017-04-30 at 10.06.40 PM.png)

Silahkan dijalankan di beberapa emulator untuk melihat hasil nya :).

## Membuat View Dan Navigation

Oke, kembali ke project yang akan kita buat. Pada bagian ini kita akan membuat view dan navigation view. Secara default project anda hanya memiliki 1 storyboard yaitu main.storyboard. Silahkan buka storyboard tersebut, lalu pilih view controller nya, pada menu bagian atas silahkan pilih editor lalu pilih embed in dan terakhir pilih navigation controller maka akan muncul output seperti berikut.

![Screen Shot 2017-04-30 at 10.34.18 PM.png](../images/Screen Shot 2017-04-30 at 10.34.18 PM.png)

Setelah selesai, silahkan drag 1 table view ke view controller, lalu berikan constraint seperti berikut.

![Screen Shot 2017-04-30 at 10.36.25 PM.png](../images/Screen Shot 2017-04-30 at 10.36.25 PM.png)

Selanjutnya silahkan buat 1 group yaitu views, di dalam group views kita akan membuat view khusus untuk menampilkan list data lagu. Karena kita menggunakan table view, maka kita membutuhkan table view cell untuk list cell nya. Untuk membuat table view cell, silahkan klik kanan pada group views, lalu pilih new file, lalu pilih cocoa touch class, lalu klik next dan isikan property nya seperti berikut.

![Screen Shot 2017-04-30 at 10.40.55 PM.png](../images/Screen Shot 2017-04-30 at 10.40.55 PM.png)

Maka akan muncul 2 file yaitu `TrackTableViewCell.swift` dan `TrackTableViewCell.xib`. Silahkan buka yang xib lalu silahkan membuat desain seperti berikut.

![Screen Shot 2017-04-30 at 10.44.49 PM.png](../images/Screen Shot 2017-04-30 at 10.44.49 PM.png)

Setelah selesai, silahkan ikuti tutorial berikut untuk konfigurasi dari view table cell ke controller table cell.

<iframe width="560" height="315" src="https://www.youtube.com/embed/eHO5rljPWHg" frameborder="0" allowfullscreen></iframe>

Tahap selanjutnya, silahkan ikuti tutorial berikut untuk main storyboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/F-uCAcTfhA8" frameborder="0" allowfullscreen></iframe>

## Membuat Service Dengan RxSwift