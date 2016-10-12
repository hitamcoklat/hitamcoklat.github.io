---
id: 218
title: Membuat Blog dengan PHP dan MySQL
date: 2012-06-24T14:20:14+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=218
permalink: /2012/06/24/membuat-blog-dengan-php-dan-mysql/
categories:
  - php
  - Tutorial
tags:
  - membuat blog
  - Membuat Blog dengan PHP dan MySQL
  - membuat blog mysql
  - membuat blog php
---
Kenapa judulnya harus &#8220;**Membuat Blog** dengan PHP dan MySQL&#8221;? padahal saya sendiri ngeblog udah pake WordPress..!?hehe. Yaa disini saya gakan ngejelasin tentang bagaimana cara membuat sistem dan merekomendasikan untuk beralih ke blog yang sekarang akan dibuat ini karena masih banyak kelemahan dari sistem blog yang akan dibuat sekarang ini dan jika dibandingkan dengan blog WordPress yang saya pakai ini jelas masih banyak kelemahannya&#8230;hehe

**Baiklah langsuuung aja ke tahap pembuatan..**

Check it out!

Pada dasarnya tampilan dari sebuah blog standar itu memiliki fitur posting blog, bagian kategori atau arsip yang membuat para pengunjung blog kamu lebih mudah dalam melihat postingan anda.

Pertama kita buat dulu tabel database nya yang diberi nama &#8220;artikel&#8221; dan terdiri dari,

  * id,
  * id_kategori -> yang berfungsi untuk menyorting ke dalam kategori-kategori tertentu,
  * judul -> berfungsi untuk menyimpan judul postingan kita, hehe *namanya juga udah &#8220;judul&#8221;,
  * konten ->berisi untuk menyimpan isi postingan kita,
  * tanggal -> berfungsi untuk menyimpan tanggal postingan kita

Kedua, buat tabel database untuk menyimpan kategori yang diberi nama &#8220;category&#8221; dan terdiri dari,

  * id,
  * category -> Untuk menyimpan nama-nama kategori yang akan dibuat

Ketiga, membuat tabel &#8220;user&#8221; untuk login pengguna &#8220;admin&#8221; atau &#8220;pengelola&#8221;,

  * id_user,
  * password -> untuk menyimpan passwordnya
  * level ->untuk menentukan level dari si pengguna

<div>
  Baiklah dibawah adalah sintaks MYSQL-nya langsung copas aja,,,hehe
</div>

<div>
</div>

#### Tabel &#8220;artikel&#8221;,

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `artikel` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_kategori` int(100) NOT NULL,
  `judul` varchar(100) NOT NULL,
  `konten` text NOT NULL,
  `tanggal` date NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=latin1 AUTO_INCREMENT=4
</pre>

#### Tabel &#8220;category&#8221;,

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `category` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `category` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=19 ;
</pre>

#### Tabel &#8220;user&#8221;,

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `user` (
  `id_user` varchar(50) COLLATE latin1_general_ci NOT NULL,
  `password` varchar(50) COLLATE latin1_general_ci NOT NULL,
  `level` varchar(50) COLLATE latin1_general_ci NOT NULL DEFAULT 'user',
  PRIMARY KEY (`id_user`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci;
</pre>

Sekarang kita akan membuat tampilan pengunjung nya yang terdiri dari &#8220;Header&#8221;, &#8220;Sidebar-Kiri&#8221; dan &#8220;Sidebar-Kanan&#8221; dapat dilihat seperti dibawah ini,

<div id="attachment_360" class="wp-caption aligncenter" style="width: 373px">
  <a href="http://hitamcoklat.com/wp-content/uploads/2012/06/2column.gif" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[218]" title="2column"><img class="size-full wp-image-360" title="2column" src="http://hitamcoklat.com/wp-content/uploads/2012/06/2column.gif" alt="2column" width="363" height="300" /></a>
  
  <p class="wp-caption-text">
    2column
  </p>
</div>

Dapat dilihat bahwa template yang akan digunakan terdiri dari 2 kolom, ohh ya untuk tampilannya itu tergantung selera&#8230;kamu bisa nyari template yang lebih baik lagi..  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

ohh ya untuk text-editor di bagian adminnya saya menggunakan CKEditor untuk lebih memperindah tampilan dan mempermudah dalam proses edit serta upload foto postingan blog-nya yaaa biar keliatan kaya WordPress hehe&#8230;seperti terlihat dibawah ini.

<a href="http://hitamcoklat.com/wp-content/uploads/2012/06/blog2.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[218]" title="blog2"><img class="aligncenter size-medium wp-image-362" title="blog2" src="http://hitamcoklat.com/wp-content/uploads/2012/06/blog2-300x174.jpg" alt="blog2" width="300" height="174" /></a>

Oke langsung aja jika ingin melihat hasil akhirnya, silahkan download

<div id='wpdm_file_4' class='wpdm_file wpdm-only-button'>
  <div class='cont'>
    <div class='btn_outer'>
      <div class='btn_outer_c' style='background-image: url(http://localhost/hitamcoklat/wp-content/plugins/download-manager/icon/Download_Crate.png);'>
        <a class='btn_left  ' rel='4' title='Blog' href="http://hitamcoklat.com/wp-content/uploads/download-manager-files/shopping_cart.rar">Download</a><span class='btn_right'>&nbsp;</span>
      </div>
    </div>
    
    <div class='clear'>
    </div>
  </div>
</div>

Sekian dulu postingan kali ini, mohon maaf jika masih ada kekurangan&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Salam Blogger!