---
id: 1254
title: Debugging Aplikasi Hybrid Menggunakan GapDebug
date: 2016-03-22T15:23:11+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=1254
permalink: /2016/03/22/debugging-aplikasi-hybrid-menggunakan-gapdebug/
categories:
  - Mobile
  - Tutorial
  - Website
tags:
  - android
  - belajar gapdebug
  - belajar menggunakan gapdebug
  - debugging dengan gapdebug
  - gapdebug
  - membuat aplikasi hybrid
---
Sekarang ini banyak sekali para developer menggunakan Phonegap (atau
  
Cordova) untuk membuat hybrid mobile. Yaa..apalagi web developer seperti
  
saya yang lebih memahami HTML5 untuk membuat aplikasi dibandingkan harus
  
menggunakan bahasa pemrograman JAVA, C++ atau lainnya. Mungkin karena setiap hari berkutat dengan bahasa seputar web.

Dalam postingan kali ini saya mencoba untuk mengenalkan tools yang cukup berguna untuk melakukan proses debugging dalam membuat aplikasi hybrid dengan menggunakan phonegap/cordova. Sebenarnya ada banyak sekali tools untuk melakukan proses debugging ini, seperti contoh nya **weinre**, tapi kenapa saya menggunakan **GapDebug**? okee&#8230;mari kita bahas ya.  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

## GapDebug

Sama seperti **weinre**, **GapDebug** merupakan sebuah tools debugger yang gratis dan cross-platform, bisa digunakan untuk debugging yang bisa berjalan di **Windows** dan **MacOS** yang cukup banyak fitur yang sangat berguna untuk keperluan debugging.

Cara penggunaan **GapDebug** sangatlah mudah dibandingkan tools lainnya. Yakni cukup melakukan build device anda baik itu anda menggunakan **AndroidStudio** atau menggunakan **CLI** sambil menjalankan aplikasi **GapDebug**nya. Untuk penggunakan fitur-fiturnya hampir sama dengan menggunakan plugin **FireBug** pada Firefox. Yaaa..disini anda sudah tidak asing lagi dalam menggunakan tools ini.hehe

<a href="http://hitamcoklat.com/wp-content/uploads/2016/03/gapdebug.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1254]" title="gapdebug"><img class="alignnone size-large wp-image-1255" title="gapdebug" src="http://hitamcoklat.com/wp-content/uploads/2016/03/gapdebug-1024x486.png" alt="" width="1024" height="486" /></a>

Nah dibawah ini screenshot gambar dalam melakukan proses debugging-nya, mirip dengan tools **FireBug** di Mozilla Firefox ya?. Ya! sebenernya **GapDebug** ini merupakan aplikasi web-based. Untuk bisa mencobanya silahkan akses http://localhost:8081.

<a href="http://hitamcoklat.com/wp-content/uploads/2016/03/proses-debugging.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1254]" title="proses-debugging"><img class="alignnone size-large wp-image-1256" title="proses-debugging" src="http://hitamcoklat.com/wp-content/uploads/2016/03/proses-debugging-1024x539.png" alt="" width="1024" height="539" /></a>

Nah coba lihat screenshot dibawah ini, selain anda bisa melihat dan memonitor aplikasi yang sedang berjalan secara realtime, anda juga bisa langsung mengedit HTML pada aplikasi yang anda buat secara langsung.

<a href="http://hitamcoklat.com/wp-content/uploads/2016/03/proses-debuggin2.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1254]" title="proses-debuggin2"><img class="alignnone size-full wp-image-1257" title="proses-debuggin2" src="http://hitamcoklat.com/wp-content/uploads/2016/03/proses-debuggin2.png" alt="" width="760" height="512" /></a>

Semoga bermanfaat&#8230;