---
id: 618
title: Membuat Toko Online – PHP dan MySQL Part 3
date: 2012-10-12T10:38:49+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=618
permalink: /2012/10/12/membuat-toko-online-php-dan-mysql-part-3/
categories:
  - php
  - Tutorial
tags:
  - Membuat Toko Online
  - Membuat Toko Online – PHP dan MySQL Part 3
  - Toko Online PHP dan MySQL
---
Akhirnya sampai juga pada pembuatan toko online part ke-3 setelah menunggu dan mengelak dari beberapa aktifitas di kampus dan di jalanan heheh  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />. Baiklah pada tahap ini bukalah file index.php yang telah kita buat sebelumnya pada bagian<a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">&#8220;Membuat Toko Online &#8211; PHP dan MySQL Part 2&#8243;</a>. Selanjutnya isikan syntax dibawah ini,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
include "include/lib.php";
include "include/top.php";
include "include/left.php";
	$v = $_GET['v'];
	if($v == 'produk') {
		require_once "include/product.php";
	} elseif ($v == 'cart') {
		require_once "include/cart.php";
	} elseif ($v == 'order') {
		require_once "include/order.php";
	} else {
		require_once "include/home.php";
	}
include "include/bottom.php";
?&gt;
</pre>

Pada syntax diatas dapat dijelaskan bahwa kita me-load file **<a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">lib.php</a>** yang berada pada folder include begitu juga file-file lainnya seperti **<a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">top.php, left.php dan bottom.php</a>**. Ya benar seperti yang telah kita ketahui pada part sebelumnya dalam pembuatan **<a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">toko online</a>** ini kita akan menggunakan teknik modulasi seperti tampak pada syntax diatas  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />.

Penjelasan selanjutnya yaitu kita akan memanfaatkan fungsi kontrol IF dan ELSE IF yang memanfaatkan $v sebagai variabel yang dihasilkan menggunakan method $_GET (dapat dilihat pada syntax diatas). Pada bagian ini kita membuat beberapa kondisi pengontrolan seperti, jika variabel &#8220;$v sama dengan (==) &#8220;produk&#8221; maka ikut sertakan file product.php yang telah kita buat pada part sebelumnya. Begitu juga file-file lainnya seperti **<a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">cart.php, order.php dan home.php</a>** seperti nampak pada syntax diatas.

Baiklah kita masuk ke tahap selanjutnya, silahkan buka file input.php (masih kosong) yang telah dijelaskan sebelumnya pada Membuat Toko Online &#8211; PHP dan MySQL Part2 lalu isikan syntax dibawah ini,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
session_start();
error_reporting(0);
include "include/lib.php";
$input=$_GET[input];
$sid = session_id();
$inputform=$_GET[inputform];

if($input=='add'){
	$sql = mysql_query("SELECT id_product FROM keranjang WHERE id_product='$_GET[id]' AND id_session='$sid'");
	$num = mysql_num_rows($sql);
	if ($num==0){
		mysql_query("INSERT INTO keranjang(id_product,
											id_session,
											tgl_keranjang,
											qty)
									VALUES	('$_GET[id]',
											'$sid',
											'$tgl_sekarang',
											'1')") or die (mysql_error());
	}
	else {
		mysql_query("UPDATE keranjang SET qty = qty + 1 WHERE id_session = '$sid' AND id_product='$_GET[id]'") or die (mysql_error());
	}
	deletecart();
	header('location:index.php?v=cart');
	}
elseif ($input=='delete'){
	mysql_query("DELETE FROM keranjang WHERE id_keranjang='$_GET[id]'");
	header('location:index.php?v=cart');
	}
elseif ($input=='inputform'){
	$ct_content = cart_content();
	$jml = count($ct_content);
	$now = date("Ymd");
	for($i=0; $i&lt;$jml; $i++){
	mysql_query("INSERT INTO order_product(name,
											email,
											phone,
											address,
											id_product,
											jumlah,
											tanggal,
											id_pemesan)
									VALUES ('$_POST[name]',
											'$_POST[email]',
											'$_POST[telp]',
											'$_POST[address]',
											{$ct_content[$i]['id_product']},
											{$ct_content[$i]['qty']},
											'$now',
											'$sid')");
		}
	for($i=0; $i&lt;$jml; $i++){
		mysql_query("DELETE FROM keranjang WHERE id_keranjang = {$ct_content[$i]['id_keranjang']}");
		}
		echo "&lt;script&gt;window.alert('Terima Kasih Pesanan Anda Sedang Kami Proses');
        window.location=('index.php')&lt;/script&gt;";
	}
?&gt;
</pre>

Jika disederhanakan syntax file diatas berisi perintah input ke dalam mySQL  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />. Tidak jauh berbeda dengan file sebelumnya, file input.php ini masih menggunakan teknik kontrol IF dan ELSEIF, ya mungkin kita akan akan lebih mudah dalam proses maintanance dan perawatan lainnya jika terdapat beberapa kesalahan atau hal yang tidak diinginkan   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />heheh lebay.

<ul style="line-height: 1.6em;" type="square">
  <li>
    Pada baris pertama, kita mengaktifkan session dengan menggunakan fungsi session_start().
  </li>
  <li>
    Baris kedua merupakan fungsi php yang berguna untuk mematikan menonaktifkan semua laporan pemberitahuan error.
  </li>
  <li>
    Baris ke tiga dan keempat mungkin sudah kita bahas pada bagian atas yah <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />
  </li>
  <li>
    Baris ke 19 sampai 27 berisi syntax PHP+MySQL yang berfungsi untuk melakukan proses input ke dalam database, seperti yang nampak pada syntax (pada baris ke 25) terlihat bahwa setelah melakukan input ke dalam database kita memanggil fungsi <strong><a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">deletecart()</a> </strong>yang berguna untuk menghapus query pada tabel keranjang yang telah kita buat sebelumnya pada<strong> <a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">tahap sebelumnya.</a></strong> Setelah proses dieksekusi makan proses dilanjutkan dengan me-direct ke halaman index.php (lihat pada Baris ke 26).
  </li>
  <li>
    Baris ke 28 sampai 31 berfungsi untuk menghapus query.
  </li>
  <li>
    Baris 32 sampai 53 berguna untuk mengeksekusi proses input yang berisi perintah untuk memasukan query ke dalam tabel order_product, sebelumnya telah kita ketahui proses ini hanya memindahkan tabel keranjang ke dalam tabel order_product. lihat juga fungsi <a title="Membuat Toko Online – PHP dan MySQL Part 2" href="http://hitamcoklat.com/2012/10/03/membuat-toko-online-php-dan-mysql-part-2/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);"><strong>cart_content()</strong></a> pada pembahasan sebelumnya.
  </li>
  <li>
    Baris ke 54 sampai 58 merupakan proses perulangan yang berisi perintah delete pada PHP+MySQL yang perulangannya telah ditentukan sebelumnya pada variabel <strong>$jml </strong>dengan menggunakan fungsi <strong>count() </strong>(lihat baris ke 34). Setelah itu jika proses berhasil maka akan muncul window alert dan me-direct halaman ke index.php seperti terlihat di baris ke 57 sampai 58.
  </li>
</ul>

Baiklah mungkin sampai disini tahap pembuatan toko online dari sisi pengunjung, pada part selanjutnya akan dibahas mengenai pembuatan halaman administrator nya. Semoga bermanfaat   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />Salam blogger!

Baiklah file part1, part2 dan part3 anda sudah selesai dan jika tidak ada kesalahan maka filenya akan seperti dibawah ini.

**<a title="download file" href="http://hitamcoklat.com/wp-content/uploads/2012/10/part1-part2-part3.rar" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);">Klik Disini Untuk Download File</a>**