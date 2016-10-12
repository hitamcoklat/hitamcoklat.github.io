---
id: 502
title: 'Membuat Toko Online &#8211; PHP dan MySQL Part 1'
date: 2012-10-03T19:23:34+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=502
permalink: /2012/10/03/membuat-toko-online-php-dan-mysql-part-1/
categories:
  - php
  - Tutorial
tags:
  - Membuat Toko Online
  - 'Membuat Toko Online - PHP dan MySQL'
---
Pada postingan sebelumnya saya sudah menuliskan mengenai sistem shopping cart menggunakan PHP dan MySQL tetapi dalam postingan sebelumnya itu saya tidak menuliskan kode atau menjelaskan kode secara menyeluruh karena waktu itu saya sempat berpikir mungkin akan banyak menyita postingan hehe, tapi sekarang saya berubah pikiran dan akan mencoba untuk mempostingan cara pembuatan sistem toko online dari awal sampai akhir. Baiklah pada pembuatan toko online ini akan dibagi ke dalam beberapa bagian yang terdiri dari:

  1. Menentukan Layout
  2. Membuat database dan tabel
  3. Konfigurasi File

## Menentukan Layout &#8211; Pengunjung

Dalam toko online kali ini akan di bahas pertama kali mengenai layout karena menurut saya layout merupakan hal terpenting dalm memetakan sebuah sketsa dari sebuah website, yaa tapi kadang-kadang membuat database nya terlebih dahulu juga engga apa-apa sih&#8230;hehee. Baiklah kembali ke pembahasan lagi yaa,, untuk layout toko online ini sendiri saya menggunakan tampilan dengan menggunakan 3 kolom. Pertama buat 2 buah file yang terdiri dari file .html dan .css, pada bagian file .html silahkan ketikan syntax html dibawah ini.

<pre class="brush: xml; title: ; notranslate" title="">&lt;html&gt;&lt;head&gt;
&lt;meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"&gt;
		&lt;title&gt;Toko Online&lt;/title&gt;
		&lt;link rel="StyleSheet" href="file/style.css" type="text/css"&gt;
		&lt;link rel="StyleSheet" href="file/reset.css" type="text/css"&gt;
	&lt;/head&gt;

	&lt;body&gt;
		&lt;div class="wrap"&gt;
			&lt;div class="header"&gt;
				&lt;div class="LeftOne"&gt;
					&lt;a href="#"&gt;&lt;img src="file/toko-online.png" width="150px"&gt;&lt;/a&gt;
				&lt;/div&gt;
				&lt;div class="RightOne"&gt;
					&lt;div class="cart"&gt;
						&lt;span class="KetCart"&gt;0 item&lt;/span&gt;					&lt;/div&gt;
					&lt;br class="clearfloat"&gt;
					&lt;a class="tocart" href="#"&gt;Keranjang&lt;/a&gt;
				&lt;/div&gt;
			&lt;/div&gt;
			&lt;br class="clearfloat"&gt;&lt;div class="LeftContent"&gt;
	&lt;div id="navigation"&gt;
		&lt;ul class="top-level"&gt;
		&lt;li&gt;&lt;a href="#"&gt;Baju Formal&lt;/a&gt;&lt;/li&gt;&lt;li&gt;&lt;a href="#"&gt;Baju Gamis&lt;/a&gt;&lt;/li&gt;&lt;li&gt;&lt;a href="#"&gt;Sepatu Cibaduyut&lt;/a&gt;&lt;/li&gt;&lt;li&gt;&lt;a href="#cat=16"&gt;Sepatu Kopo&lt;/a&gt;&lt;/li&gt;		&lt;/ul&gt;
	&lt;/div&gt;
&lt;/div&gt;&lt;div class="BigContent"&gt;
&lt;div class="RightContent"&gt;
&lt;h1 class="Judul"&gt;Produk terbaru&lt;/h1&gt;
&lt;div class="produk"&gt;
	&lt;a href="#id=35"&gt;
		&lt;img title="Produk Ganteng" class="FotoProduk" src="file/versace-kids-shoes.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="produk"&gt;
	&lt;a href="#id=34"&gt;
		&lt;img title="Sepatu Cewe" class="FotoProduk" src="file/sepat1u.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="produk"&gt;
	&lt;a href="#id=33"&gt;
		&lt;img title="Baju Cewe" class="FotoProduk" src="file/1297307145_165392947_1-Pictures-of--baju-muslimah-trendyBroo.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="produk"&gt;
	&lt;a href="#id=32"&gt;
		&lt;img title="Baju Timnas" class="FotoProduk" src="file/5e314d4cbf3be7f42c724d85ff3f65a1.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="produk"&gt;
	&lt;a href="#id=31"&gt;
		&lt;img title="Sepatu Dua" class="FotoProduk" src="file/sepatu.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="produk"&gt;
	&lt;a href="#"&gt;
		&lt;img title="Sepatu Keren" class="FotoProduk" src="file/cnqy4fkdrymitqaif8hw.jpg" height="110px"&gt;
	&lt;/a&gt;
	&lt;br class="clearfloat"&gt;
	&lt;div class="KotakKet"&gt;
	&lt;a class="pesanprod" href="#"&gt;Pesan&lt;/a&gt;
	&lt;a class="detprod" href="#"&gt;Detail&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
			&lt;/div&gt;
				&lt;br class="clearfloat"&gt;
			&lt;/div&gt;
			&lt;div class="footer"&gt;
				&lt;p align="center"&gt;© 2012 Membuat Sistem Shopping Cart | PHP dan MySQL Developed by &lt;a href="http://www.hitamcoklat.com/"&gt;hitamcoklat&lt;/a&gt;&lt;/p&gt;
			&lt;/div&gt;
		&lt;/div&gt;

&lt;/body&gt;&lt;/html&gt;
</pre>

Setelah itu pada bagian file .css nya silahkan ketikan css dibawah ini,

<pre class="brush: css; title: ; notranslate" title="">body {
    font-family: Verdana,sans-serif,Arial;
	background: url("../images/stripe.png") repeat scroll 0 0 transparent;
	font-size: 0.75em;
}
.clearfloat {
    clear: both;
}
.wrap {
    border: 5px solid #CCCCCC;
    margin: 10px auto;
    padding: 5px;
    width: 750px;
	background-color: #fff;
}
.Judul {
	font-size: 18px;
	font-weight: bold;
	margin: 5px 5px 5px 5px;
	}
.LeftOne {
	float: left;
	width: 200px;
	}
.RightOne {
	float: right;
	}
.header {
    height: 120px;
    margin-bottom: 10px;
}
.form {
	margin: 10px 10px 10px 10px;
	border: 1px solid #CCC;
	padding: 2px 2px 2px 2px;
	}
.BigContent {
	width: 750px;
	}
.LeftContent {
	float: left;
    margin: 5px;
    width: 180px;
}
.RightContent {
	float: right;
    padding: 5px;
    width: 520px;
	position: relative;
}
.produk {
    float: left;
	border: 1px solid #CCC;
	margin-top: 10px;
	margin-left: 10px;
}
.pesanprod {
    float: left;
    margin-left: 10px;
}
.tocart {
	float: right;
    background: none repeat scroll 0 0 #FF9900;
	padding: 5px;
	text-decoration: none;
	color: black;
	}
.tocart:hover {
	color: black;
	font-weight: bold;
	}
.KotakKet {
	padding: 5px;
	float: left;
    background: none repeat scroll 0 0 #FF9900;
	}
.pesanprod:hover {
    background: none repeat scroll 0 0 #fff;
	}
.FotoProduk {
	padding: 3px 3px 3px 3px;
	float: left;
	}
.detprod {
    float: left;
    margin-left: 10px;
}
.detprod:hover {
    background: none repeat scroll 0 0 #fff;
	}
.cart {
    background-color: #fff;
    float: right;
    min-height: 50px;
    width: 200px;
	border-bottom: 1px solid #CCC;
}
.KetCart {
	font-size: 18px;
	float: left;
	margin-top: 25px;
	font-weight: bold;
	margin-left: 10px;
	}
input {
	margin: 10px 10px 10px 10px;
	}
#navigation {font-size:0.75em; width:150px;}
#navigation ul {margin:0px; padding:0px;}
#navigation li {list-style: none;}

ul.top-level {background:#666;}
ul.top-level li {
 border-bottom: #fff solid;
 border-top: #fff solid;
 border-width: 1px;
}

#navigation a {
 color: #fff;
 cursor: pointer;
 display:block;
 height:25px;
 line-height: 25px;
 text-indent: 10px;
 text-decoration:none;
 width:100%;
}
#navigation a:hover{
 text-decoration:underline;
}

#navigation li:hover {
 background: #f90;
 position: relative;
}
.footer {
	background-color: #DBF7FA;
	padding-top: 20px;
	padding-bottom: 20px;
	margin-top: 30px;
	}
.KetProd {
	background-color: #fff;
	width: 500px;
	height: 200px;
	padding: 10px 10px 10px 10px;
	}
.haha {
	text-decoration: none;
	font-size: 14px;
	background: none repeat scroll 0 0 #FF9900;
	padding: 5px;
	}
.haha:hover{
	color: #fff;
	background: none repeat scroll 0 0 blue;
	}
.tombol {
	float: right;
	margin-right:30px;
	margin-top: 30px;
	font-weight: bold;
	color: #121212;
	}
.tombol:hover {
	background: none repeat scroll 0 0 #FF9900;
	padding: 2px 2px 2px 2px;
	}
.GambarKetProd {
	float: left;
	width: 150px;
	margin-right: 20px;
	padding: 3px 3px 3px 3px;
	border: 1px solid #CCC;
	}
.TableCart {
	border: 1px solid #CCC;
	    color: #000000;
    font-family: Verdana;
    font-size: 8pt;
    line-height: 18px;
    text-decoration: none;
    width: 100%;
	}
th {
	background-color: #e0e0e0;
	}
</pre>

Jika tidak ada kesalah maka tampilan yang dihasilkan kurang lebih dapat dilihat pada gambar dibawah ini,

<p style="text-align: center;">
  <a href="http://hitamcoklat.com/wp-content/uploads/2012/10/FireShot-Pro-Screen-Capture-083-Toko-Online-localhost_septian_tes_toko2_index_php.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[502]" title="Toko Online"><img class="aligncenter  wp-image-560" title="Toko Online" src="http://hitamcoklat.com/wp-content/uploads/2012/10/FireShot-Pro-Screen-Capture-083-Toko-Online-localhost_septian_tes_toko2_index_php.jpg" alt="Toko Online" width="600" height="auto" /></a>
</p>

<a title="download file" href="http://hitamcoklat.com/wp-content/uploads/edd/2012/10/pengunjung.rar" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" target="_blank"><strong>Download File</strong></a>

## Menentukan Layout &#8211; Pengelola

Tahap selanjutnya yaitu menentukan layout yang akan digunakan dalam halaman pengelola, halaman pengelola ini bertugas untuk menginputkan produk atau kategori yang akan ditampilkan di halaman pengunjung tadi. Dalam kasus ini saya menggunakan layout 2 Kolom yang terdiri dari Sidebar Sebelah Kiri dan Sidebar sebelah kanan. Sidebar sebelah kiri berfungsi untuk tampilan menu-menu yang isinya akan ditampilkan di dalam Sidebar sebelah kanan. Biar ga bingung langsung aja buat folder dan diberi nama **&#8220;admin&#8221; **yang isinya terdapat 2 buah file terdiri dari .html dan .css (sama seperti layout &#8211; pengelola). Jika sudah silahkan ketikan kode html dibawah ini,

<pre class="brush: xml; title: ; notranslate" title="">&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"&gt;
&lt;html lang="en"&gt;
	&lt;head&gt;
    	&lt;title&gt;Toko Online&lt;/title&gt;
        &lt;link rel="stylesheet" media="screen" href="css/style.css" type="text/css" /&gt;
    &lt;/head&gt;
    &lt;body&gt;
    	&lt;div class="wrap"&gt;
        	&lt;div class="header"&gt;
				&lt;h3&gt;Bagian header&lt;/h3&gt;
            &lt;/div&gt;
			&lt;div class="Menu"&gt;
			&lt;/div&gt;
            &lt;div class="Konten"&gt;
            	&lt;div class="KontenKiri"&gt;
					&lt;h3&gt;Konten Kiri&lt;/h3&gt;
                &lt;/div&gt;
                &lt;div class="KontenTengah"&gt;
					&lt;h3&gt;Konten Tengah&lt;/h3&gt;
                &lt;/div&gt;
				&lt;br class="clearfloat" /&gt;
            &lt;/div&gt;
            &lt;div class="Footer"&gt;
				&lt;h3&gt;Footer&lt;/h3&gt;
            &lt;/div&gt;
    	&lt;/div&gt;
    &lt;/body&gt;
&lt;/html&gt;
</pre>

Baiklah pada bagian css nya silahkan ketikan kode CSS dibawah ini,

<pre class="brush: css; title: ; notranslate" title="">body {
	background-color: #fff;
	font-family: Arial;
	}
.clearfloat {
	clear: both;
	}
.wrap {
	margin: 10px auto;
	width: 750px;
	padding: 5px;
	border: 1px solid #CCC;
	}
.header {
	float: left;
	background-color: #ddd;
	width: 100%;
	}
.Menu {
	height: 50px;
	width: 100%;
	}
.Konten {
	min-height: 300px;
	background-color: #ACD1E9;
	}
.KontenTengah {
	float: left;
	width: 580px;
	background-color: #5E9DC8;
	}
.KontenKiri {
	float: left;
	width: 150px;
	padding: 5px;
	background-color: #336699;
	margin-right: 10px;
	}
.Footer {
	width: 100%;
	background-color: #5E9DC8;
	}
</pre>

Jika tidak ada kesalahan maka pada tampilan admin/pengelola seharusnya seperti dibawah ini,
  
<a href="http://hitamcoklat.com/wp-content/uploads/2012/10/FireShot-Pro-Screen-Capture-084-__-Toko-Online-__-localhost_septian_tes_toko2_admin_admin_php_modhome.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[502]" title="Toko Admin"><img class="aligncenter  wp-image-562" title="Toko Admin" src="http://hitamcoklat.com/wp-content/uploads/2012/10/FireShot-Pro-Screen-Capture-084-__-Toko-Online-__-localhost_septian_tes_toko2_admin_admin_php_modhome-1024x320.jpg" alt="Toko Admin" width="600" height="auto" /></a>

<a title="Download File Admin" href="http://hitamcoklat.com/wp-content/uploads/2012/10/admin.rar" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" target="_blank"><strong>Download File</strong></a>

Sebagai catatan bahwa keterangan syntax-syntax diatas merupakan syntax HTML dan CSS yang hanya akan menampilkan halaman depan dari sisi admin dan pengunjung secara umum yang memiliki 2 kolom (kolom kiri dan kolom kanan) dengan kata lain pada tahap ini belum dibahas mengenai tampilan per kategori yang nantinya akan berubah setiap kita memilih menu yang tersedia. Mungkin dilanjutkan dibagian <a title="Membuat Toko Online Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);"><strong>Membuat Toko Online &#8211; PHP dan MySQL Part 2</strong></a> yaaa&#8230;

Semoga bermanfaat  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />