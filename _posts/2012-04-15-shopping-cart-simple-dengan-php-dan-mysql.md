---
id: 191
title: Shopping Cart Simple dengan PHP dan MySQL
date: 2012-04-15T07:07:01+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=191
permalink: /2012/04/15/shopping-cart-simple-dengan-php-dan-mysql/
categories:
  - Lainnya
  - php
  - Tutorial
  - Website
tags:
  - mysql
  - php
  - shopping
  - shopping cart
  - shopping cart php dan mysql
---
Sekarang ini banyak orang yang memanfaatkan internet sebagai media jual beli, yaa ga jauh beda dengan saya yang memanfaatkan internet untuk menjual barang reseller saya, hehe&#8230;. dan ternyata internet itu memang banyak membawa keuntungan bagi mereka yang memanfaatkannya untuk berjualan. Oleh karena itu saya ingin sedikit membagi bagaimana mengimplementasikannya karena shopping cart ini cukup simple  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />. Pada &#8220;Shopping cart&#8221; simple ini hanya membutuhkan table dari database yang yang berfungsi sebagai penyimpan datanya setelah itu disimpan kembali ke table fix pemesanannya, ya kira-kira segitu penjelasan sistem shopping cartnya   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />hehehe

Baiklah langsung saja, dalam sistem shopping cart ini terdapat tahapan-tahapan yang harus diperhatikan.

## Langkah pertama,

Pada langkah pertama ini buatlah database yang terdiri dari 5 table,

Yang pertama adalah table Kategori,

<<<<<<< HEAD
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `category` (
            `id` int(11) NOT NULL AUTO_INCREMENT,
            `category` varchar(100) NOT NULL,
            PRIMARY KEY (`id`)
          ) ENGINE=MyISAM AUTO_INCREMENT=13 DEFAULT CHARSET=latin1
=======
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `category` (
            `id` int(11) NOT NULL AUTO_INCREMENT,
            `category` varchar(100) NOT NULL,
            PRIMARY KEY (`id`)
          ) ENGINE=MyISAM AUTO_INCREMENT=13 DEFAULT CHARSET=latin1
>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
</pre>

Selanjutnya Buatlah table order_product, yang berfungsi untuk menyimpan data pesanan nanti seperti dibawah ini.

<<<<<<< HEAD
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `order_product` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `id_product` int(11) NOT NULL,
 `id_pemesan` varchar(100) NOT NULL,
 `name` varchar(100) NOT NULL,
 `email` varchar(100) NOT NULL,
 `address` varchar(1000) NOT NULL,
 `phone` bigint(20) NOT NULL,
 `status` varchar(30) NOT NULL DEFAULT 'New',
 `jumlah` int(4) NOT NULL,
 `tanggal` date NOT NULL,
 PRIMARY KEY (`id`)
 ) ENGINE=MyISAM AUTO_INCREMENT=51 DEFAULT CHARSET=latin1
=======
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `order_product` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `id_product` int(11) NOT NULL,
 `id_pemesan` varchar(100) NOT NULL,
 `name` varchar(100) NOT NULL,
 `email` varchar(100) NOT NULL,
 `address` varchar(1000) NOT NULL,
 `phone` bigint(20) NOT NULL,
 `status` varchar(30) NOT NULL DEFAULT 'New',
 `jumlah` int(4) NOT NULL,
 `tanggal` date NOT NULL,
 PRIMARY KEY (`id`)
 ) ENGINE=MyISAM AUTO_INCREMENT=51 DEFAULT CHARSET=latin1
>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
</pre>

Berikutnya table product yang berfungsi untuk menyimpan data produk. Sintaksnya dapat dilihat seperti dibawah ini.

<<<<<<< HEAD
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `product` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `product_name` varchar(100) NOT NULL,
 `price` bigint(20) NOT NULL,
 `image` varchar(1000) NOT NULL,
 `id_category` int(11) NOT NULL,
 `deskripsi` text NOT NULL,
 PRIMARY KEY (`id`)
 ) ENGINE=MyISAM AUTO_INCREMENT=30 DEFAULT CHARSET=latin1
=======
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `product` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `product_name` varchar(100) NOT NULL,
 `price` bigint(20) NOT NULL,
 `image` varchar(1000) NOT NULL,
 `id_category` int(11) NOT NULL,
 `deskripsi` text NOT NULL,
 PRIMARY KEY (`id`)
 ) ENGINE=MyISAM AUTO_INCREMENT=30 DEFAULT CHARSET=latin1
>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
</pre>

Lanjut ke table user untuk halaman login-nya&#8230;

<<<<<<< HEAD
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `user` (
 `id_user` varchar(50) COLLATE latin1_general_ci NOT NULL,
 `password` varchar(50) COLLATE latin1_general_ci NOT NULL,
 `email` varchar(100) COLLATE latin1_general_ci NOT NULL,
 `level` varchar(50) COLLATE latin1_general_ci NOT NULL DEFAULT 'user',
 PRIMARY KEY (`id_user`)
 ) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci

=======
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `user` (
 `id_user` varchar(50) COLLATE latin1_general_ci NOT NULL,
 `password` varchar(50) COLLATE latin1_general_ci NOT NULL,
 `email` varchar(100) COLLATE latin1_general_ci NOT NULL,
 `level` varchar(50) COLLATE latin1_general_ci NOT NULL DEFAULT 'user',
 PRIMARY KEY (`id_user`)
 ) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci

>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
</pre>

Langkah terakhir adalah table keranjang yang berfungsi untuk mengambil data sementara untuk penggunaan cart dalam penggunaan keranjang pada sistem shopping cart ini.

<<<<<<< HEAD
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `keranjang` (
 `id_keranjang` int(5) NOT NULL AUTO_INCREMENT,
 `id_product` int(5) NOT NULL,
 `id_session` varchar(100) COLLATE latin1_general_ci NOT NULL,
 `tgl_keranjang` date NOT NULL,
 `qty` int(4) NOT NULL,
 PRIMARY KEY (`id_keranjang`)
 ) ENGINE=MyISAM AUTO_INCREMENT=360 DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci

=======
<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `keranjang` (
 `id_keranjang` int(5) NOT NULL AUTO_INCREMENT,
 `id_product` int(5) NOT NULL,
 `id_session` varchar(100) COLLATE latin1_general_ci NOT NULL,
 `tgl_keranjang` date NOT NULL,
 `qty` int(4) NOT NULL,
 PRIMARY KEY (`id_keranjang`)
 ) ENGINE=MyISAM AUTO_INCREMENT=360 DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci

>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
</pre>

## Langkah Berikutnya,

menentukan desain dari shoping cart-nya&#8230;
  
Untuk desain nya, saya membuatnya se simple mungkin yang terdiri dari kolom kiri, kolom kanan, header dan footer seperti yang nampat dibawah ini.
  
<a href="http://hitamcoklat.com/wp-content/uploads/2012/04/FireShot-Screen-Capture-002-Toko-Online-localhost_septian_tes_toko2_index_php.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[191]" title="Shopping Cart"><img class="aligncenter size-medium wp-image-199" title="Shopping Cart" src="http://hitamcoklat.com/wp-content/uploads/2012/04/FireShot-Screen-Capture-002-Toko-Online-localhost_septian_tes_toko2_index_php-300x233.jpg" alt="Shopping Cart" width="300" height="233" /></a>

## Langkah terakhir,

Baiklah pada langkah ini kita mempersiapkan file-file yang dibutuhkan seperti.

Input.php &#8211;> Berfungsi untuk memproses data yang nantinya digunakan untuk memasukan belanjaan ke keranjang
  
Product.php&#8211;>Berfungsi untuk menampilkan produk dan kategori yang terdapat di dalam sistem shopping cart ini.
  
Checkout.php&#8211;>Berfungsi untuk pengisian data konsumen
  
Koneksi.php&#8211;>Berfungsi untuk integrasi ke database

Hmm&#8230;mungkin kalo disebutin satu-satu agak banyak ya&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Tapi jika kamu penasaran bisa langsung di download aja file-nya 

<div id='wpdm_file_3' class='wpdm_file wpdm-only-button'>
  <div class='cont'>
    <div class='btn_outer'>
<<<<<<< HEAD
      <div class='btn_outer_c'>
        <a class='btn_left' rel='3' title='Shopping Cart Simple' href="http://hitamcoklat.com/wp-content/uploads/download-manager-files/shopping_cart.rar"><< Download</a><span class='btn_right'>&nbsp;</span>
=======
      <div class='btn_outer_c' style='background-image: url(http://localhost/hitamcoklat/wp-content/plugins/download-manager/icon/Download_Crate.png);'>
        <a class='btn_left  ' rel='3' title='Shopping Cart Simple' href="http://localhost/hitamcoklat/?wpdmact=process&did=My5ob3RsaW5r"   >Download</a><span class='btn_right'>&nbsp;</span>
>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
      </div>
    </div>
    
    <div class='clear'>
    </div>
  </div>
</div>

<<<<<<< HEAD
Semoga bisa membantu  :)
=======
Semoga bisa membantu  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />
>>>>>>> e9f0b44fcb065adf8f120ab0638d33dbda8ac0ca
