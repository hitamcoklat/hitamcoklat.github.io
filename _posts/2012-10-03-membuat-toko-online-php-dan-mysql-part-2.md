---
id: 525
title: 'Membuat Toko Online &#8211; PHP dan MySQL Part 2'
date: 2012-10-03T19:24:27+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=525
permalink: /2012/10/03/membuat-toko-online-php-dan-mysql-part-2/
categories:
  - php
  - Tutorial
tags:
  - Membuat Toko Online
  - 'Membuat Toko Online - PHP dan MySQL'
  - 'Membuat Toko Online - PHP dan MySQL Part 2'
---
Pada postingan sebelumnya telah dibahas mengenai pembuatan template sederhana untuk toko online ini. Pada bagian ini akan dibahas mengenai konfigurasi file dan desain database nya. Pada bagian_** Membuat Toko Online &#8211; PHP dan MySQL Part 2 **_pertama-tama saya akan membahas cara pembuatan database terlebih dahulu untuk memberikan bayangan mengenai sistem yang akan kita buat nanti. Oh ya sebelumnya jika kamu sudah membuat tampilan HTML+CSS nya di **[Membuat Toko Online &#8211; PHP dan MySQL Part 2](#) **mungkin akan ada beberapa hal yang akan berbeda di tahap** [Membuat Toko Online &#8211; PHP dan MySQL Part 2](#) **karena dalam tahap ini saya akan membagi bagian template-nya ke dalam beberapa bagian (dimaksudkan untuk dapat lebih mudah dalam pengembangan dan maintanance nanti) baiklah langsung aja check it out.

<a href="http://hitamcoklat.com/wp-content/uploads/2012/10/Drawing1.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[525]" title="Drawing1"><img class="alignnone size-full wp-image-998" title="Drawing1" src="http://hitamcoklat.com/wp-content/uploads/2012/10/Drawing1.png" alt="" width="382" height="520" /></a>

## Membuat Tabel Database

### tabel &#8211; category

<pre class="brush: sql; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `category` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `category` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=17 ;
</pre>

### Tabel &#8211; Keranjang

<pre class="brush: sql; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `keranjang` (
  `id_keranjang` int(5) NOT NULL AUTO_INCREMENT,
  `id_product` int(5) NOT NULL,
  `id_session` varchar(100) COLLATE latin1_general_ci NOT NULL,
  `tgl_keranjang` date NOT NULL,
  `qty` int(4) NOT NULL,
  PRIMARY KEY (`id_keranjang`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci AUTO_INCREMENT=394 ;
</pre>

### Tabel &#8211; Order Product

<pre class="brush: sql; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `order_product` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_product` int(11) NOT NULL,
  `id_pemesan` varchar(100) NOT NULL,
  `name` varchar(100) NOT NULL,
  `email` varchar(100) NOT NULL,
  `address` text NOT NULL,
  `phone` int(20) NOT NULL,
  `status` varchar(30) NOT NULL DEFAULT 'New',
  `jumlah` int(4) NOT NULL,
  `tanggal` date NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=70 ;
</pre>

### Tabel &#8211; Product

<pre class="brush: sql; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `product` (
`id` int(11) NOT NULL AUTO_INCREMENT,
`product_name` varchar(100) NOT NULL,
`price` int(20) NOT NULL,
`image` varchar(1000) NOT NULL,
`id_category` int(11) NOT NULL,
`deskripsi` text NOT NULL,
PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1 AUTO_INCREMENT=36 ;
</pre>

### Tabel &#8211; User

<pre class="brush: sql; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `user` (
  `id_user` varchar(50) COLLATE latin1_general_ci NOT NULL,
  `password` varchar(50) COLLATE latin1_general_ci NOT NULL,
  `email` varchar(100) COLLATE latin1_general_ci NOT NULL,
  `level` varchar(50) COLLATE latin1_general_ci NOT NULL DEFAULT 'user',
  PRIMARY KEY (`id_user`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1 COLLATE=latin1_general_ci;
</pre>

## Membuat File Konfigurasi

Langkah selanjutnya adalah membuat file-file konfigurasi yang dibutuhkan dalam pembuatan Toko Online ini, seperti

  * Membuat fungsi PHP yang dibutuhkan
  * Memisahkan file-file PHP kedalam bagian-bagian terkecil atau biasa disebut dengan teknik modulasi

Sebelum melangkah pada pembuatan fungsi PHP buatlah terlebih dahulu folder dan file yang dapat dilihat hasilnya pada gambar dibawah ini,

<a href="http://hitamcoklat.com/wp-content/uploads/2012/10/Untitled.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[525]" title="Gambar Folder"><img class="aligncenter size-full wp-image-537" title="Gambar Folder" src="http://hitamcoklat.com/wp-content/uploads/2012/10/Untitled.png" alt="Gambar Folder" width="312" height="258" /></a>

Setelah dibuat folder dan filenya, ayoo kita lanjutkan pada tahap selanjutnya (semoga masih semangat yaaaa&#8230;!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />). Bukalah folder **&#8220;include&#8221; **dan buatlah sebuah file diberi nama **lib.php**, isilah file tersebut dengan fungsi-fungsi berikut ini.

### lib.php

<pre class="brush: php; title: ; notranslate" title="">&lt;!--?php $seminggu = array("Minggu","Senin","Selasa","Rabu","Kamis","Jumat","Sabtu"); $hari = date("w"); $hari_ini = $seminggu[$hari]; $tgl_sekarang = date("Ymd"); $thn_sekarang = date("Y"); $jam_sekarang = date("H:i:s"); $nama_bln=array(1=--&gt; "Januari", "Februari", "Maret", "April", "Mei",
                    "Juni", "Juli", "Agustus", "September",
                    "Oktober", "November", "Desember");
//fungsi untuk keranjang belanja
function cart_content(){
	$ct_content = array();
	$sid = session_id();
	$sql = mysql_query("SELECT * FROM keranjang WHERE id_session='$sid'");
	while ($r=mysql_fetch_array($sql)) {
		$ct_content[] = $r;
	}
	return $ct_content;
}
//fungsi untuk menghapus keranjang
function deletecart(){
	$del = date('Y-m-d', mktime(0,0,0, date('m'), date('d') - 1, date('Y')));
	mysql_query("DELETE FROM keranjang WHERE tgl_keranjang &lt; '$del'"); 	} //fungsi untuk membuat koneksi database ke server function koneksi() { 	$server = "localhost"; 	$username = "root"; 	$password = ""; 	$database = "toko2"; 	mysql_connect($server,$username,$password) or die("Koneksi gagal"); 	mysql_select_db($database) or die("Database tidak bisa dibuka"); } ?&gt;
</pre>

ya&#8230;!! dalam membuat toko online ini fungsi diatas akan menjadi pilar dalam sistem toko online ini, selanjutnya kita akan masuk ke dalam tahap cara menggunakan teknik modulasi yang menurut saya sangat bermanfaat untuk membuat aplikasi web. Karena dengan teknik modulasi ini kita dapat mudah dalam melakukan pengembangan dan perawatan suatu aplikasi web, oh ya **teknik modulasi ini merupakan suatu teknik pemisahan sebuah aplikasi menjadi bagian-bagian kecil**&#8230;hhmmm, mungkin terlalu panjang bahasannya ya hehe, langsung ajalah buat file-file dibawah ini didalam folder **&#8220;include&#8221; :**

  1. bottom.php
  2. cart.php
  3. cart2.php
  4. home.php
  5. left.php
  6. order.php
  7. product.php
  8. top.php

Jika sudah dibuat, silahkan file tersebut isikan dengan syntax berikut,

### bottom.php

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="footer"&gt;
© &lt;!--?php echo date('Y') ?--&gt; Membuat Sistem Shopping Cart | PHP dan MySQL Developed by &lt;a href="http://www.hitamcoklat.com/"&gt;hitamcoklat&lt;/a&gt;&lt;/div&gt;
&lt;pre&gt;

</pre>

File diatas berfungsi untuk menampilkan bagian bawah website toko online ini.

### cart.php

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="BigContent"&gt;
&lt;div class="RightContent"&gt;
&lt;h1 class="Judul"&gt;Shopping Cart&lt;/h1&gt;
&lt;div class="KetProd"&gt;$sid = session_id(); $no = 1; $sql = mysql_query("SELECT * FROM keranjang, product WHERE id_session='$sid' AND keranjang.id_product=product.id"); $hitung = mysql_num_rows($sql); if ($hitung &lt; 1){echo""; } else { while($tian=mysql_fetch_array($sql)){ echo""; $no++; } } ?&gt;
&lt;table class="TableCart" style="border-top: 1px dotted #0; border-bottom: 1px dotted #0;" width="100%" border="0" cellspacing="0" cellpadding="0"&gt;
&lt;tbody&gt;
&lt;tr&gt;
&lt;th&gt;No&lt;/th&gt;
&lt;th&gt;Foto Produk&lt;/th&gt;
&lt;th&gt;Nama Produk&lt;/th&gt;
&lt;th&gt;Jumlah&lt;/th&gt;
&lt;th&gt;Harga&lt;/th&gt;
&lt;th&gt;Delete&lt;/th&gt;
&lt;!--?php &lt;br ?--&gt;
&lt;td&gt;$no&lt;/td&gt;
&lt;td&gt;&lt;img src="foto/$tian[image]" alt="" width="50" /&gt;&lt;/td&gt;
&lt;td&gt;$tian[product_name]&lt;/td&gt;
&lt;td&gt;$tian[qty]&lt;/td&gt;
&lt;td&gt;$tian[price]&lt;/td&gt;
&lt;td&gt;&lt;a href="input.php?input=delete&id=$tian[id_keranjang]"&gt;Hapus&lt;/a&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;
 &lt;a class="tombol" href="?v=order"&gt;Selesai&lt;/a&gt;
 &lt;a class="tombol" href="index.php"&gt;Belanja Lagi..&lt;/a&gt;&lt;/div&gt;
</pre>

File diatas berfungsi untuk menampilkan produk yang sudah dimasukan ke dalam keranjang

### cart2.php

<pre class="brush: php; title: ; notranslate" title="">&lt;!--?php &lt;br ?--&gt;include "inc/koneksi.php";
	$sid = session_id();
	$sql = mysql_query("SELECT * FROM keranjang");
	$row = mysql_num_rows($sql);
	$jml = mysql_fetch_array($sql);

	echo "&lt;span class="KetCart"&gt;$row item&lt;/span&gt;";
	?&gt;
</pre>

File diatas berfungsi untuk menampilkan produk yang telah dimasukan kedalam tabel keranjang dan menghitungnya dengan menggunakan fungsi _**mysql\_num\_rows()**_

### home.php

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="BigContent"&gt;
&lt;div class="RightContent"&gt;
&lt;h1 class="Judul"&gt;Produk terbaru&lt;/h1&gt;
&lt;!--?php 	$sql = mysql_query("SELECT * FROM product ORDER BY id DESC") or die ("Query gagal dengan error: ".mysql_error()); 	while($data=mysql_fetch_array($sql)){ ?--&gt;
&lt;div class="produk"&gt;&lt;a href="?v=produk&id=&lt;?php echo $data['id']; ?&gt;"&gt;
 &lt;img class="FotoProduk" title="&lt;?php echo $data['product_name']; ?&gt;" src="foto/&lt;?php echo $data['image']; ?&gt;" alt="" height="110px" /&gt;
 &lt;/a&gt;
 &lt;br class="clearfloat" /&gt;
&lt;div class="KotakKet"&gt;&lt;a class="pesanprod" href="input.php?input=add&id=&lt;?php echo $data['id']; ?&gt;"&gt;Pesan&lt;/a&gt;
 &lt;a class="detprod" href="product.php?id=&lt;?php echo $data['id']; ?&gt;"&gt;Detail&lt;/a&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;!--?php } ?--&gt;
</pre>

### left.php

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="LeftContent"&gt;
&lt;div id="navigation"&gt;
&lt;ul class="top-level"&gt;
&lt;ul class="top-level"&gt;&lt;!--?php &lt;br ?--&gt; $kat = mysql_query("SELECT category, category.id from category join product on product.id_category=category.id group by category");&lt;/ul&gt;
&lt;/ul&gt;
&lt;ul class="top-level"&gt;
&lt;ul class="top-level"&gt;while($list=mysql_fetch_array($kat)){&lt;/ul&gt;
&lt;/ul&gt;
&lt;ul class="top-level"&gt;
&lt;ul class="top-level"&gt;echo"
	&lt;li&gt;&lt;a href="?v=produk&cat=$list[id]"&gt;$list[category]&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/ul&gt;
&lt;ul class="top-level"&gt;
&lt;ul class="top-level"&gt;";&lt;/ul&gt;
&lt;/ul&gt;
&lt;ul class="top-level"&gt;
&lt;ul class="top-level"&gt;}&lt;/ul&gt;
&lt;/ul&gt;
&lt;ul class="top-level"&gt;?&gt;&lt;/ul&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;pre&gt;
</pre>

File diatas berfungsi untuk menampilkan menu kategori dari tabel category dengan menggabungkan tabel product, dapat dilihat dari syntax mysqlnya,

<pre>mysql_query("SELECT category, category.id from category join product on product.id_category=category.id group by category");</pre>

### order.php

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="BigContent"&gt;
&lt;div class="RightContent"&gt;
&lt;h2 class="Judul"&gt;Form Pemesanan&lt;/h2&gt;
&lt;form action="input.php?input=inputform" method="post"&gt;
&lt;table&gt;
&lt;tbody&gt;
&lt;tr&gt;
&lt;td&gt;Nama&lt;/td&gt;
&lt;td&gt;&lt;input class="form" type="text" name="name" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;Email&lt;/td&gt;
&lt;td&gt;&lt;input class="form" type="text" name="email" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;Alamat&lt;/td&gt;
&lt;td&gt;&lt;textarea class="form" name="address" rows="7" cols="40"&gt;&lt;/textarea&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;No HP&lt;/td&gt;
&lt;td&gt;&lt;input class="form" type="text" name="telp" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;&lt;/td&gt;
&lt;td&gt;&lt;input type="submit" name="submit" value="order" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;
&lt;/form&gt;
</pre>

File diatas berfungsi sebagai form dengan tujuan file yaitu** _input.php._**

### product.php

File ini berfungsi untuk menampilkan produk per kategori dan produk inti,

<pre class="brush: php; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div class="BigContent"&gt;
&lt;div class="RightContent"&gt;&lt;!--?php &lt;br ?--&gt; $prod = $_GET['id'];
 $cat = $_GET['cat'];
 if($cat){
 $sql = mysql_query("SELECT * FROM category WHERE id = '$cat'"); //untuk mengambil tabel kategori berdasarkan id
 $jdl = mysql_fetch_array($sql);
 echo "
&lt;h1 class="Judul"&gt;Kategori $jdl[category]&lt;/h1&gt;
";
 $sql2 = mysql_query("SELECT * FROM product WHERE id_category='$cat'");
 while($t = mysql_fetch_array($sql2)){ ?&gt;
&lt;div class="produk"&gt;&lt;a href="?v=produk&id=&lt;?php echo $t['id']; ?&gt;"&gt;
 &lt;img class="FotoProduk" title="&lt;?php echo $t['product_name']; ?&gt;" src="foto/&lt;?php echo $t['image']; ?&gt;" alt="" height="110px" /&gt;
 &lt;/a&gt;
 &lt;br class="clearfloat" /&gt;
&lt;div class="KotakKet"&gt;&lt;a class="pesanprod" href="input.php?input=add&id=&lt;?php echo $t['id']; ?&gt;"&gt;Pesan&lt;/a&gt;
 &lt;a class="detprod" href="?v=produk&id=&lt;?php echo $t['id']; ?&gt;"&gt;Detail&lt;/a&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;!--?php 	} } elseif($prod){ ?--&gt;
&lt;!--?php //jika variable cat tidak terdefinisikan maka lanjut ke proses dibawah ini 	$sql = mysql_query("SELECT * FROM product WHERE id='$prod'"); 	$d = mysql_fetch_array($sql); 	?--&gt;
&lt;h1 class="Judul"&gt;Produk &lt;!--?php echo $d['product_name']; ?--&gt;&lt;/h1&gt;
&lt;div class="KetProd"&gt;&lt;img class="GambarKetProd" src="foto/&lt;?php echo $d['image']; ?&gt;" alt="" /&gt;
 &lt;!--?php echo $d['deskripsi']; ?--&gt;&lt;/div&gt;
 &lt;a class="haha" href="javascript:history.go(-1)"&gt;Kembali&lt;/a&gt; | &lt;a class="haha" href="input.php?input=add&id=&lt;?php echo $d['id']; ?&gt;"&gt;Beli&lt;/a&gt;
&lt;!--?php } ?--&gt;
</pre>

### top.php

<pre class="brush: php; title: ; notranslate" title="">&lt;!--?php 	error_reporting(0); 	session_start(); 	?--&gt;

		Toko Online
&lt;/pre&gt;
&lt;div class="wrap"&gt;
&lt;div class="header"&gt;
&lt;div class="LeftOne"&gt;&lt;a href="index.php"&gt;&lt;img src="images/toko-online.png" alt="" width="150px" /&gt;&lt;/a&gt;&lt;/div&gt;
&lt;div class="RightOne"&gt;
&lt;div class="cart"&gt;&lt;/div&gt;
 &lt;br class="clearfloat" /&gt;
 &lt;a class="tocart" href="cart.php"&gt;Keranjang&lt;/a&gt;&lt;/div&gt;
&lt;/div&gt;
 &lt;br class="clearfloat" /&gt;
</pre>

Dari syntax diatas dapat dilihat bahwa terdapat 2 alur pengerjaannya, yaitu jika kondisi pertama (yaitu variable **cat** dimana dihasilkan dari parameter URL) terpenuhi maka akan melanjutkan query pengambilan kategori dan apabila kondisi kedua (dimana variable **cat **tidak terdefinisikan) maka akan akan melanjutkan query pengambilan produk berdasarkan_ **id.**_ Dilanjutkan di bagian &#8220;<a title="Membuat Toko Online – PHP dan MySQL Part 3" href="http://hitamcoklat.com/2012/10/12/membuat-toko-online-php-dan-mysql-part-3/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);"><strong>Membuat Toko Online PHP dan MySQL Part3</strong></a>&#8221; ya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Ohh ya jika ada pertanyaan seputar pembuatan toko online ini silahkan isi komentar.