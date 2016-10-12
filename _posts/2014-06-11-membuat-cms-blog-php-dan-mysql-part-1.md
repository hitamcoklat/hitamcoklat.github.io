---
id: 1123
title: Membuat CMS Blog PHP dan MySQL Part-1
date: 2014-06-11T17:31:24+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=1123
permalink: /2014/06/11/membuat-cms-blog-php-dan-mysql-part-1/
categories:
  - php
  - Tutorial
tags:
  - membuat blog php
  - membuat CMS dengan php
  - Membuat CMS PHP mudah
---
Pada postingan kali ini saya akan membahas mengenai pembuatan CMS blog. Yaa sebelumnya saya posting tentang “Membuat Blog dengan PHP” tapi tidak begitu jelas yah hehe, sekarang mau coba posting mengenai pembuatan CMS blog yang lebih lengkap nya, supaya lebih jelas.. 
<img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' /> 

## Kerangka Postingan

<table style="border-collapse:collapse;border-spacing:0; margin-left: 20px; margin-bottom: 20px;">
  <tr>
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:bold;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px; text-align: left;" colspan="2">
      Membuat Blog Part-1
    </th>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;font-style:italic" rowspan="3">
      Pembahasan Kali ini ->
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat halaman awal Blog
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat halaman detail Blog
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat Database & Table
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;font-weight:bold" colspan="2">
      Membuat Blog Part-2
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;font-style:italic" rowspan="2">
      Pembahasan =>
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat Halaman admin
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat Fitur Posting &#8211; add, edit dan delete
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;font-weight:bold" colspan="2">
      Membuat Blog Part-3
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px;font-style:italic">
      Pembahasan =>
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-top-width:1px;border-bottom-width:1px">
      Membuat Fitur Kategori &#8211; add, edit dan delete
    </td>
  </tr>
</table>

Pertama kita siapkan dulu file untuk halaman front end nya, dimana file ini berfungsi untuk menampilkan halaman postingan kita. Didalam halaman ini terdiri dari 

  * Header
  * Navigasi
  * Bagian artikel yang terletak disebelah kiri
  * Bagian sidebar yang akan menampilkan postingan terbaru, terletak disebelah kanan

Pada bagian halaman artikel terdapat 2 tampilan, yaitu halaman home awal yang befungsi untuk melihat kilasan artikel sebelum user melihat artikel secara detail dan halaman detail artikel dimana user akan melihat detail artikel ketika user meng klik artikel lalu setelah itu kita tampilkan artikel secara penuh. 

## Membuat Halaman depan Blog

Baiklah langsung saja kita membuat halaman awal blog kita. Pada pembuatan blog yang akan kita buat ini dapat langsung liat di screenshot nya dibawah ini.

<a href="http://hitamcoklat.com/wp-content/uploads/2014/06/halaman_depan_blog.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1123]" title="halaman_depan_blog"><img class="alignnone size-medium wp-image-1124" title="halaman_depan_blog" src="http://hitamcoklat.com/wp-content/uploads/2014/06/halaman_depan_blog-300x228.jpg" alt="halaman_depan_blog" width="300" height="228" /></a>

Dan halaman detail artikelnya sebagai berikut
  
<a href="http://hitamcoklat.com/wp-content/uploads/2014/06/halaman_depan_blog-FILEminimizer.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1123]" title="halaman_depan_dua"><img class="alignnone size-medium wp-image-1126" title="halaman_depan_dua" src="http://hitamcoklat.com/wp-content/uploads/2014/06/halaman_depan_blog-FILEminimizer-300x232.png" alt="halaaman_detail_blog" width="300" height="232" /></a>

Berikut source code HTML nya

### index.html

<pre class="brush: php; title: ; notranslate" title="">&lt;html&gt;
	&lt;head&gt;
		&lt;link rel="stylesheet" type="text/css" href="css/style.css" /&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;div id="wrap"&gt;
			&lt;div id="header"&gt;
				&lt;h1&gt;Hitamcoklat | Blog&lt;/h1&gt;
			&lt;/div&gt;
			&lt;div id="navigasi"&gt;
				&lt;ul&gt;
					&lt;li&gt;&lt;a href="#"&gt;Menu Satu&lt;/a&gt;&lt;/li&gt;
					&lt;li&gt;&lt;a href="#"&gt;Menu Dua&lt;/a&gt;&lt;/li&gt;
					&lt;li&gt;&lt;a href="#"&gt;Menu Tiga&lt;/a&gt;&lt;/li&gt;
					&lt;li&gt;&lt;a href="#"&gt;Menu Empat&lt;/a&gt;&lt;/li&gt;
				&lt;/ul&gt;
			&lt;/div&gt;
			&lt;div id="konten"&gt;
				&lt;div id="kiri"&gt;
					&lt;div class="artikel"&gt;
						&lt;h2&gt;Postingan Satu&lt;/h2&gt;
						&lt;p&gt;Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem Lorem ipsum dolor sit amet...&lt;a href="#"&gt;Baca Selengkapnya&lt;/a&gt;&lt;/p&gt;
					&lt;/div&gt;

					&lt;div class="artikel"&gt;
						&lt;h2&gt;Postingan Satu&lt;/h2&gt;
						&lt;p&gt;Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem Lorem ipsum dolor sit amet...&lt;a href="#"&gt;Baca Selengkapnya&lt;/a&gt;&lt;/p&gt;
					&lt;/div&gt;

					&lt;div class="artikel"&gt;
						&lt;h2&gt;Postingan Satu&lt;/h2&gt;
						&lt;p&gt;Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem Lorem ipsum dolor sit ametLorem ipsum dolor sit ametLorem ipsum dolor sit ametLoremLorem Lorem ipsum dolor sit amet...&lt;a href="#"&gt;Baca Selengkapnya&lt;/a&gt;&lt;/p&gt;
					&lt;/div&gt;

				&lt;/div&gt;
				&lt;div id="kanan"&gt;
					&lt;h2&gt;Recent Post&lt;/h2&gt;
					&lt;ul&gt;
						&lt;li&gt;&lt;a href="#"&gt;Artikel Satu&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Artikel Dua&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Artikel Tiga&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Artikel Empat&lt;/a&gt;&lt;/li&gt;
					&lt;/ul&gt;
				&lt;/div&gt;
			&lt;/div&gt;
			&lt;div class="clear"&gt;&lt;/div&gt;
			&lt;div id="footer"&gt;
				&lt;p&gt;Hitamcoklat | Blog&lt;/p&gt;
			&lt;/div&gt;
		&lt;/div&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

### style.css

<pre class="brush: css; title: ; notranslate" title="">* {
	margin: 0;
	padding: 0;
}
body {
	background-color: #fff;
	font-family: Arial;
	font-size: 0.850em;
}

.artikel p {
	margin-top: 10px;
}

#wrap {
	padding: 10px;
	background-color: #EAEAEA;
	width: 800px;
	margin: 20px auto;
}

#header, #navigasi, #konten {
	width: 100%;
	float: left;
}

#header {
	height: 70px;
}

#navigasi {
	background-color: #CCC;
}

#navigasi ul li {
	margin: 10px;
	font-weight: bold;
	list-style: none;
	float: left;
}

#navigasi ul li a, #kanan ul li a {
	text-decoration: none;
	color: #000;
}

#navigasi ul li a:hover, #kanan ul li a:hover {
	text-decoration: underline;
}

#kanan ul li {
	list-style: none;
	font-weight: bold;
	border-left: 3px solid #CCC;
	margin-top: 5px;
	padding-left: 5px;
	background-color: #fff;
}
.clear {
	clear: both;
}

.artikel {
	border: 1px solid #CCC;
	margin-top: 10px;
	padding: 10px;
	background-color: #fff;
}

#kiri {
	padding: 10px;
	float: left;
	width: 65%;
}

#kanan {
	padding: 10px;
	float: left;
	width: 30%;
}

#footer {
	background-color: #CCCCCC;
	width: 100%;
	height: 50px;
}

#footer p {
	margin: 10px;
	float: left;
}
</pre>

Baiklah jika semuanya sudah selesai maka tampilannya akan sama dengan screenshot diatas  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />, kita lanjut membuat database yaa biar cepet hehe

## Membuat database

Selanjutnya kita akan membuat database. Seperti biasa pertama buat dulu database di phpmyadmin dengan nama bebas terserah anda hehe. Setelah itu kita akan membuat table – table dalam database, untuk lebih jelasnya dapat dilihat pada gambar berikut ini

<a href="http://hitamcoklat.com/wp-content/uploads/2014/06/database.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1123]" title="database"><img class="alignnone size-medium wp-image-1135" title="database" src="http://hitamcoklat.com/wp-content/uploads/2014/06/database-300x206.png" alt="database" width="300" height="206" /></a>

*Keterangan

### Table Category

<table style="border-collapse:collapse;border-spacing:0;border-color:#999">
  <tr>
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Nama Field
    </th>
    
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Tipe
    </th>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      id
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      int(11)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      category
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      varchar(100)
    </td>
  </tr>
</table>

### Table Artikel

<table style="border-collapse:collapse;border-spacing:0;border-color:#999">
  <tr>
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Nama Field
    </th>
    
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Tipe
    </th>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      id
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      int(11)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      id_kategori
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      varchar(100)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      judul
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      varchar(250)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      konten
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      text
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      tanggal
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
    </td>
  </tr>
</table>

### Table User

<table style="border-collapse:collapse;border-spacing:0;border-color:#999">
  <tr>
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Nama Field
    </th>
    
    <th style="font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#fff;background-color:#26ADE4">
      Tipe
    </th>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      id_user
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      int(5)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      username
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      varchar(10)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      password
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      varchar(35)
    </td>
  </tr>
  
  <tr>
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      level
    </td>
    
    <td style="font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:#999;color:#444;background-color:#F7FDFA">
      enum(&#8216;user&#8217;,'admin&#8217;)<br /> DEFAULT ‘user’
    </td>
  </tr>
</table>

Oke untuk part pertama cukup sampai disini, besok dilanjut yah   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />Salam Blogger! 

<a href="http://www.hitamcoklat.com/download/?3006342321751ecf0fe55306b8c71fe7" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.hitamcoklat.com']);" class="download">Download File</a>