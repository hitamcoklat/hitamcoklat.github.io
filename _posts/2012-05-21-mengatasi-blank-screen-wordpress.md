---
id: 309
title: 'Mengatasi Blank Screen &#8211; WordPress'
date: 2012-05-21T08:16:56+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=309
permalink: /2012/05/21/mengatasi-blank-screen-wordpress/
categories:
  - Lainnya
  - Tutorial
tags:
  - Blank Screen Wordpress
  - Layar Putih Wordpress
  - White Screen Of Death Wordpress
  - Wordpress Error
---
Blank Screen atau yang lebih dikenal dengan White Screen Of Death (WSOD) pada wordpress merupakan suatu permasalah yang mungkin sering muncul bagi kamu yang sering memakai plugin atau mengotak-atik website dengan CMS wordpress.

Masih hangat sekali kasus ini terjadi pada saya, blog ini total tidak bisa dibuka karena permasalahan diatas. Bermaksud ingin membuat template baru untuk blog ini, ehh malah terjadi Blank Scree pada tampilan admin-nya dan merembet deh ke tampilan utama website&#8230;huuuhh  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_sad.gif' alt=':(' class='wp-smiley' />

Setelah waktu dan tenaga telah dikeluarkan semua dan nyari informasi sana-sini ternyata kasus Blank Screen ini dapat disebabkan beberapa hal, antara lain:

### Masalah Plugin

Pada kasus yang pertama, adanya plugin yang bentrok atau anda terlalu banyak menginstall plugin ini-itu dan mengakibatkan terjadinya crash pada salah satu fungsi di wordpress.

Dalam kasus ini disarankan anda untuk menonaktifkan terlebih dahulu semua plugin-nya&#8230; atau jika sudah terlambat dengan kata lain anda sudah tidak bisa masuk ke halaman adminnya. Apa boleh buat dengan cara paksa saja hehe, yaitu:

  1. Masuk Ke Halaman Cpanel anda contoh: http://namawebanda.com/cpanel
  2. Setelah itu masuk ke PhpMyadmin anda,
  3. Klik pada bagian wp\_options, setelah itu pada halaman 2 cari bagian active\_plugins seperti tampak pada gambar dibawah, lalu rubah option_value-nya menjadi **a:0:{}**

<div class="mceTemp">
  <dl id="" class="wp-caption alignnone" style="width: 637px;">
    <dt class="wp-caption-dt">
      <img src="http://hitamcoklat.com/wp-content/uploads/2012/05/FireShot-Screen-Capture-010-localhost-_-localhost-_-wordpress-_-wp_options-I-phpMyAdmin-3_3_9-localhost_phpmyadmin_index_php_dbwordpresstoken5a11893aa2c5aefc49d5238195aa8322.jpg" alt="active_plugins" width="627" height="37" />
    </dt>
    
    <dd class="wp-caption-dd">
    </dd>
  </dl>
</div>

Sebelumnya back-up dulu database nya yah&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Ohh ya sebagai alternative anda bisa me-rename file-file di folder plugins untuk menonaktifkannya&#8230;

<h3 style="text-align: left;">
  Masalah Functions.php di template
</h3>

Selain masalah diatas, permalahan Blank Screen yang disebabkan oleh template itu sendiri sering terjadi&#8230;biasanya dibagian functions.php. Ya, bagian ini cukup vital bagi sistem wordpress itu sendiri karena berisi kode-kode fungsi yang mengatur segala sesuatu yang berkenaan dengan menjadikan halaman template menjadi dinamis.

Jika cara yang diatas tidak berhasil maka saya sarankan pikiran anda tertuju pada file functions.php di bagian template anda ini, pemecahan masalah nya yaitu dengan delete bagian White-Spaces pada bagian akhir kode php-nya&#8230;hhmm&#8230;kalo bingung langsung aja copy-paste kode yang ada dalam file **functions.php** ke website ini,

<span style="color: #33cccc;"><strong><a href="http://htmlcompressor.com/compressor.html" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://htmlcompressor.com']);" target="_blank">http://htmlcompressor.com/compressor.html</a></strong></span>

Baiklah, cara diatas merupakan cara yang sering saya pakai jika terjadi kesalahan sewaktu mengotak &#8211; atik wordpress. Namun ada beberapa hal lain yang dapat menyebabkan WordPress kamu menjadi Blank Screen, seperti terjadi kesalahan sewaktu melakukan proses **upgrade,** atau mungkin masih banyak lagi yang belum sempet saya coba..  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Baiklah sekarang jika mengalami Blank Screen lagi ga akan frustasi lagiii!!!!
  
Sekian dulu postingan kali ini, semoga bermanfaat&#8230;

Salam Blogger!