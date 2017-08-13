---
layout: post
title: Membuat Routing Pada Angular 4
modified:
categories:
description: Membuat Routing Pada Angular 4
tags: [angular 4, typescript, routing]
image:
  background: abstract-2.png
comments: true
share: true
date: 2017-08-14T20:15:28+07:00
---

Pada artikel [sebelumnya](https://rizkimufrizal.github.io/setup-project-angular-4/), penulis telah membahas mengenai bagaimana cara setup project angular 4. Pada artikel ini, penulis akan membahas mengenai bagaimana cara membuat routing pada angular 4.

## Apa Itu Routing ?

>>Routing adalah salah satu fitur angular dimana routing ini biasanya digunakan untuk navigasi sebuah web.

Dalam melakukan development sebuah web, biasanya arsitektur yang digunakan adalah membuat sebuah web dengan full fitur angular, sehingga untuk urusan routing dan navigasi juga akan dihandle oleh angular. Untuk mengakses data ke bagian server, angular dapat menggunakan fungsi http bawaan. Pada artikel ini, kita akan mencoba membuat 2 routing, akan tetapi sebelum membuat routing, kita akan melakukan konfigurasi bootstrap terlebih dahulu.

## Setup Bootstrap

Untuk menambah dependency library bootstrap silahkan jalankan perintah berikut.

{% highlight bash %}
npm install --save @ng-bootstrap/ng-bootstrap bootstrap
{% endhighlight %}

pada artikel ini,kita akan menggunakan library [ng-bootstrap](https://ng-bootstrap.github.io).
