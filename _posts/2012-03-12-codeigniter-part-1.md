---
id: 64
title: 'Codeigniter &#8211; Part 1'
date: 2012-03-12T15:36:44+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=64
permalink: /2012/03/12/codeigniter-part-1/
image:
  - 
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
categories:
  - Internet
  - Lainnya
  - Uncategorized
tags:
  - Belajar Codeigniter
  - Codeigniter
---
<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/41CodeIgniter.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[64]" title="CodeIgniter"><img class="alignnone size-full wp-image-67" title="CodeIgniter" src="http://hitamcoklat.com/wp-content/uploads/2012/03/41CodeIgniter.jpg" alt="" width="500" height="265" /></a>

Oke pada post kali ini saya akan membahas sedikit tentang Framework PHP Codeigniter, mungkin Codeigniter ini dapat dibilang cukup populer saat ini dan Codeigniter ini adalah salah satu framework PHP dari sekian banyak yang tersedia di alam sana.. hehe. Kenapa saya memilih membahas Codeigniter ketimbang Framework lainnya? hhmmm&#8230;Ini alasannya,

  1. Codeigniter adalah Framework OpenSource alias Free!
  2. Codeigniter sangat ringan jika dijalankan pada semua platform
  3. Codeigniter menggunakan M-V-C
  4. Codeigniter menciptakan URL friendly
  5. Codeigniter dikemas dalam sebuah framework yang lengkap

<!--more-->

Dan banyaaaakkk lagii deh&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Secara umum Framework adalah sebuah susunan atau rangkaian kerja yang tetap dan dibuat sedemikian rupa yang kemudian dapat digunakan kembali dalam sebuah kegiatan kerja yang lain tapi masih dalam satu area kerja dengan rangkaian kerja sebelumnya.

**Fitur utama Codeigniter**

  * Berbasis Model &#8211; View &#8211; Controller (MVC)
  * Kompatibel dengan PHP4 dan PHP5
  * Sangat ringan
  * Class database lengkap
  * Manajemen session
  * Class yang sangat lengkap seperti HTML text email, send mail &#8211; SMTP &#8211; MAIL, support attachment dan banyak lagi
  * Class FTP
  * Pengurutan halaman paging
  * Class untuk kalender
  * Support Hooks, Ekstensi class, dan plugins
  * Class trackback (metoda untuk mengetahui halaman web lain yang mempunyai link pada halaman web kita)

### **MODEL &#8211; VIEW &#8211; CONTROLLER**

Seperti sudah dijelaskan diatas Framework Codeigniter merupakan Framework yang berbasiskan MVC, MVC adalah sebuah software yang memisahkan antara aplikasi logika dengan konten yang disajikan pada halaman website. Sehingga dalam pengkodeannya akan sedikit karena terjadi pemisahan antara tampilan dengan pemrograman.

**Apa itu MODEL?**

Model disini adalah struktur data. Jika dijelaskan secara spesifik Class Model ini akan berisi fungsi kode yang membantu dalam segala proses yang berhubungan dengan database seperti mendapatkan, menghapus, mengedit dan memasukan data dalam database.

**Apa itu VIEW?**

View adalah informasi yang disampaikan ke pengguna internet disini biasanya berupa halaman website yang disajikan bisa berupa header dan footer ataupun halaman web yang lain seperti RSS.

**Apa itu CONTROLLER?**

Controller merupakan perantara Model dan View dan semua sumber yang dibutuhkan untuk memproses permintaan HTTP.

Gambaran umumnya seperti dibawah ini&#8230;

<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/mvc.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[64]" title="Model View Controller"><img class="alignnone size-full wp-image-70" title="Model View Controller" src="http://hitamcoklat.com/wp-content/uploads/2012/03/mvc.jpg" alt="" width="400" height="432" /></a>