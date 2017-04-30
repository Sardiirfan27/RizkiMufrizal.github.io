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
* Membuat Service Dengan RxSwift Dan Alamofire
* Membuat Helper Dan Controller

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

## Membuat Service Dengan RxSwift Dan Alamofire

Pada bagian ini, kita akan membuat service. Biasanya service disini saya gunakan untuk melakukan request data ke API. Untuk melakukan request data, kita akan menggunakan [Alamofire](http://pintient.com/qcV){:target="_blank"}. Untuk melakukan parsing json ke object swift biasanya saya menggunakan [ObjectMapper](http://pintient.com/qch){:target="_blank"}. Untuk membuat aplikasi suatu event request yang asynchronous maka kita gunakan [RxSwift](http://pintient.com/qcy){:target="_blank"}, bagi anda yang ingin memperdalam tentang reactivex silahkan baca di [ReactiveX](http://pintient.com/qd6){:target="_blank"}.

Silahkan buat sebuah group dengan nama `services` lalu buatlah sebuah file swift dengan nama `TrackService` di dalam group service tersebut. Lalu isikan kodingan seperti berikut.

{% highlight swift %}
//
//  TrackService.swift
//  Belajar-iOS
//
//  Created by rizki mufrizal on 4/30/17.
//  Copyright © 2017 rizki mufrizal. All rights reserved.
//

import Alamofire
import ObjectMapper
import AlamofireObjectMapper
import RxSwift

class TrackService {
    func getTrackByQuery(parameters: String, offset: Int, limit: Int) -> Observable<TrackResponse> {
        return Observable<TrackResponse>.create { observer -> Disposable in
            let request = Alamofire
                .request("https://api.spotify.com/v1/search?q=\(parameters)&type=track&offset=\(offset)&limit=\(limit)", method: .get)
                .validate()
                .responseObject(completionHandler: { (response: DataResponse<TrackResponse>) in
                    switch response.result {
                    case .success(let trackResponse):
                        observer.onNext(trackResponse)
                        observer.onCompleted()
                    case .failure(let error):
                        observer.onError(error)
                    }
                })
            return Disposables.create(with: {
                request.cancel()
            })
        }
    };
}
{% endhighlight %}

Dengan menggunakan RxSwift maka kita dapat menggunakan fitur Observable, fitur ini mirip dengan fitur List di java. Disana terdapat 3 parameter yaitu parameters biasanya ini untuk parameter yang akan kita search, offset sebagai halaman ke berapa karena pada api ini kita menggunakan paging, dan yang terakhir adalah limit yang berfungsi untuk mendeklarasikan berapa per halaman yang akan kita tampilkan.

## Membuat Helper Dan Controller

Tahap terakhir kita akan membuat helper dan controller. Helper disini sendiri biasanya kita buat agar helper ini dapat digunakan di banyak tempat. Contohnya adalah, jika kita melakukan request, dimana jika kita menggunakan parameter dan parameter tersebut mempunyai spasi maka kita harus menconvert spasi dengan `+`, akan tetapi fungsi merubah karakter ini bergantung dari kebutuhan API, ada yang mengharuskan diubah menjadi `+` atau ada juga menggunakan `%20` dan lain sebagainya.

Silahkan buat sebuah group dengan nama `helpers` lalu buat sebuah file swift dengan nama `ConvertString`, kemudian masukkan kodingan seperti berikut.

{% highlight swift %}
//
//  ConvertString.swift
//  Belajar-iOS
//
//  Created by rizki mufrizal on 5/1/17.
//  Copyright © 2017 rizki mufrizal. All rights reserved.
//

import Foundation

class ConvertString {
    func toPlusString(text: String) -> String {
        return text.replacingOccurrences(of: " ", with: "+")
    }

    func fromArrayArtistToString(array: [Artist]) -> String {
        var text = ""
        if array.count == 1 {
            text = array[0].name!
        } else {
            for i in 0..<array.count {
                text = text + array[i].name! + ", "
            }
        }

        if text.substring(from: text.index(text.endIndex, offsetBy: -2)) == ", " {
            text.remove(at: text.index(text.endIndex, offsetBy: -2))
        }

        return text
    }
}
{% endhighlight %}

Pada class diatas terdapat 2 fungsi yaitu, fungsi `toPlusString` berfungsi untuk me replace string kosong dengan karakter `+`. Sedangkan fungsi `fromArrayArtistToString` kita gunakan untuk menconvert dari array object `Artist` menjadi string biasa.