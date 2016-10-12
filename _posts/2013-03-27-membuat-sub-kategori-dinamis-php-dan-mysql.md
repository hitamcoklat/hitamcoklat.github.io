---
id: 752
title: Membuat Sub Kategori Dinamis PHP dan MySQL
date: 2013-03-27T09:04:01+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=752
permalink: /2013/03/27/membuat-sub-kategori-dinamis-php-dan-mysql/
categories:
  - php
  - Tutorial
tags:
  - kategori php
  - Membuat Sub Kategori Dinamis PHP dan MySQL
  - php dan mysql
  - sub kategori
  - sub kategori php
---
Wow mungkin udah hampir 3 bulan blog ini tidak terurus dan nampak usang hoho. Oh ya sebelumnya mohon maaf atas pertanyaan-pertanyaan agan-agan yang belum bisa saya balas dan diposting sekarang. Mungkin pada postingan selanjutnya aja ya gan mohon maaf sebelumnya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Mungkin sudah tidak asing lagi dengan judul diatas. Jika agan pernah lihat toko-toko online terdapat menu di sebelah kiri atau sebelah kanan atau sebelah atas terdapat menu yang apabila agan sorot maka akan muncul sub kategori didalamnya? hehe&#8230; ya pada postingan kali ini saya akan sedikit berbagi cara untuk membuat Kategori dan Sub Kategori yang sangat simple menggunakan PHP dan MySQL dan akan dijelaskan bagaimana cara kita menampilkan Kategori Induk dan Sub Kategorinya. Baiklah langsung saja ya&#8230;

## 1. Relasi Tabel

<p style="text-align: center;">
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/03/relasi.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[752]" title="relasi"><img class="size-full wp-image-754 aligncenter" title="relasi" src="http://hitamcoklat.com/wp-content/uploads/2013/03/relasi.png" alt="" width="474" height="223" /></a>
</p>

Adapun sintaks MySQL nya adalah sebagai berikut

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `category` (
            `id` int(11) NOT NULL AUTO_INCREMENT,
            `category` varchar(100) NOT NULL,
            PRIMARY KEY (`id`)
          ) ENGINE=MyISAM AUTO_INCREMENT=21 DEFAULT CHARSET=latin1
</pre>

&nbsp;

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `sub_category` (
                `id_sub` int(3) NOT NULL AUTO_INCREMENT,
                `id_category` int(3) NOT NULL,
                `nama_sub` varchar(100) NOT NULL,
                PRIMARY KEY (`id_sub`)
              ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=latin1
</pre>

Ohh ya bisa juga langsung dibuat pake phpmyadmin dengan keterangan seperti sintaks MySQL diatas,
  
Keterangan:

  * id -> INT (3) *AUTO INCREMENT _primary_
  * category -> VARCHAR (100)

<div>
  Untuk tabel <strong>sub_category </strong>sebagai berikut,
</div>

<div>
  <ul>
    <li>
      id_sub -> INT (3) *AUTO INCREMENT <em>primary</em>
    </li>
    <li>
      id_category -> INT(3)
    </li>
    <li>
      nama_sub -> VARCHAR(100)
    </li>
  </ul>
</div>

Dua perintah SQL diatas merupakan perintah untuk membuat tabel yang bisa dilihat di gambar, nah sekarang kita masukan isi dari masing-masing tabel tersebut. Disini kamu bisa memberikan nilai seperti yang saya input kan *nampak seperti dibawah ini,

### Isi Tabel &#8220;category&#8221;

<p style="text-align: center;">
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/03/category.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[752]" title="category"><img class="size-full wp-image-759 aligncenter" title="category" src="http://hitamcoklat.com/wp-content/uploads/2013/03/category.jpg" alt="" width="229" height="136" /></a>
</p>

### Isi Tabel &#8220;sub_category&#8221;

<a href="http://hitamcoklat.com/wp-content/uploads/2013/03/sub_category.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[752]" title="sub_category"><img class="aligncenter size-full wp-image-761" title="sub_category" src="http://hitamcoklat.com/wp-content/uploads/2013/03/sub_category.jpg" alt="" width="304" height="135" /></a>
  
Baiklah bisa dilihat pada bagian tabel **sub_category** terdapat field id\_category yang menghubungkan dengan field id pada tabel category diatas. Pada gambar diatas dapat dilihat bahwa nilai id\_category yaitu 14 yang memiliki relasi pada field id di tabel category. Dengan kata lain nama\_sub atau id\_sub yang memiliki id_category 14 adalah anak dari nama category dari tabel category yang memiliki id 14 . . . heheh maaf kalo muter-muter kata-katanya.  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

## 2. Tampil PHP

Ohh ya pertama silahkan salin sintaks PHP dibawah ini terlebih dahulu,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	mysql_connect('localhost','root','password') or die("Koneksi gagal");
	mysql_select_db('nama database yang agan buat') or die("Database tidak bisa dibuka");
?&gt;
&lt;html&gt;
	&lt;body&gt;
	&lt;ul id="menu"&gt;
	&lt;?php
		$sql = mysql_query("SELECT id, category FROM category");

		while($r=mysql_fetch_array($sql)) {

			echo "&lt;li&gt;&lt;a href='#'&gt;".$r['category']."&lt;/a&gt;";

			$sql2 = mysql_query("SELECT * FROM sub_category WHERE id_category = '".$r['id']."'");

			if($sql2) {
				echo "&lt;ul&gt;";
				while($d=mysql_fetch_array($sql2)) {
					echo "&lt;li&gt;&lt;a href='#'&gt;".$d['nama_sub']."&lt;/a&gt;&lt;/li&gt;";

				}
				echo "&lt;/ul&gt;";
			} else {
				echo "&lt;/li&gt;";
			}
		}
	?&gt;
	&lt;/ul&gt;
</pre>

Baiiikkklaaah sekarang masuk pada tahap penampilan kategori-kategori tersebut. Mungkin sudah kebayang ya hasilnya? yaaa ga jauh beda sama kita memunculkan list waktu kita ngetik di blog agan masing-masing&#8230;

<a href="http://hitamcoklat.com/wp-content/uploads/2013/03/tampil1.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[752]" title="tampil1"><img class="aligncenter size-full wp-image-762" title="tampil1" src="http://hitamcoklat.com/wp-content/uploads/2013/03/tampil1.jpg" alt="" width="182" height="227" /></a>
  
Taraaa&#8230;. ya kurang lebih akan tampil seperti tampilan diatas, jelek ya? haha untuk memperindah tampilan kita bisa memanfaatkan plugin-plugin jquery. Disini saya akan menggunakan plugin **menu.js** yang bisa di download di<a href="http://www.menujs.net/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.menujs.net']);"> http://www.menujs.net/</a>jika sudah anda download salin kode dibawah ini,

File yang bernama **sub.php**

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	mysql_connect('localhost','root','') or die("Koneksi gagal");
	mysql_select_db('nama database yang agan buat') or die("Database tidak bisa dibuka");
?&gt;
&lt;html&gt;
	&lt;head&gt;
		&lt;title&gt;Membuat Sub Kategori Dinamis PHP dan MySQL&lt;/title&gt;
		&lt;script src="js/prototype.js" type="text/javascript"&gt;&lt;/script&gt;
		&lt;script src="js/Menu.js" type="text/javascript"&gt;&lt;/script&gt;
		&lt;script type="text/javascript"&gt;
			Menu.init("menu", {"orientation": Menu.VERTICAL});
		&lt;/script&gt;

		&lt;style type="text/css"&gt;
			a {
				text-decoration: none;
				}
			table {
				position: absolute;
				margin-top: 10px;
				}
			table tr td {
				background-color: #EDEDED;
				}
			/* reset default styles */
			#menu,
			#menu ul { margin: 0; padding: 0; }
			#menu li { list-style-type: none; }

			/* first level */
			#menu { width: 100px; float: left; margin-top: 100px; }
			#menu li,
			#menu a { float: left; width: 100px; }
			#menu a { display: block; background: #EEE; }
			#menu a:hover,
			#menu a.menu_open { background: #DDD; }

			/* second level */
			#menu ul { visibility: hidden; position: absolute; width: 100px; }
			#menu ul a { background: #DDD; }
			#menu ul a:hover,
			#menu ul a.menu_open { background: #CCC; }

			/* third level (colors) */
			#menu ul ul a { background: #CCC; }
			#menu ul ul a:hover { background: #BBB; }
		&lt;/style&gt;
	&lt;/head&gt;
	&lt;body&gt;
	&lt;ul id="menu"&gt;
	&lt;?php
		$sql = mysql_query("SELECT id, category FROM category");

		while($r=mysql_fetch_array($sql)) {

			echo "&lt;li&gt;&lt;a href='#'&gt;".$r['category']."&lt;/a&gt;";

			$sql2 = mysql_query("SELECT * FROM sub_category WHERE id_category = '".$r['id']."'");

			if($sql2) {
				echo "&lt;ul&gt;";
				while($d=mysql_fetch_array($sql2)) {
					echo "&lt;li&gt;&lt;a href='#'&gt;".$d['nama_sub']."&lt;/a&gt;&lt;/li&gt;";

				}
				echo "&lt;/ul&gt;";
			} else {
				echo "&lt;/li&gt;";
			}
		}
	?&gt;
	&lt;/ul&gt;
	&lt;table&gt;
	&lt;tr&gt;&lt;td&gt;&lt;a href="input.php?aksi=tambahkategori"&gt;Tambah Kategori&lt;/a&gt;&lt;/td&gt;&lt;td&gt;&lt;a href="input.php?aksi=tambahsub"&gt;Tambah Sub Kategori&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;
	&lt;/table&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

Ohh ya bisa dilihat pada bagian pemanggilan plugin javascript diatas saya memasukan file nya kedalam satu folder yang bernama **js .**

****Jika berhasil maka akan tampil seperti dibawah ini.

<a href="http://hitamcoklat.com/wp-content/uploads/2013/03/gambar_menu.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[752]" title="gambar_menu"><img class="aligncenter size-full wp-image-765" title="gambar_menu" src="http://hitamcoklat.com/wp-content/uploads/2013/03/gambar_menu.jpg" alt="" width="509" height="338" /></a>
  
Sekarang tampilannya lebih indah bukan? haha ini adalah tampilan plugin dari **menu.js** yang saya download barusan *menurut saya sih kurang elegan hahaha, tapi pada fungsi nya sama saja lah&#8230;hehe, ketika kursor menyorot pada kategori maka akan muncul sub kategori yang bersangkutan dan jika tidak terdapat sub kategori maka tidak akan ditampilkan apa-apa.

## 3. Input PHP

Oke lanjut ke tahapan proses penginputan kategori dan sub kategori. Sebenernya sih bisa langsung rubah di phpmyadmin-nya, tapi itu bakalan memakan waktu apalagi proses nya tidak user friendly banget heheh. Maka alternatifnya kita akan membuat form input untuk proses input kategori dan sub kategori nya. Baiklah langsung aja kita salin sintaks PHP dibawah ini,

File yang bernama **input.php**

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	mysql_connect('localhost','root','') or die("Koneksi gagal");
	mysql_select_db('nama database yang agan buat') or die("Database tidak bisa dibuka");
?&gt;
&lt;html&gt;
	&lt;head&gt;
		&lt;title&gt;Membuat Sub Kategori Dinamis PHP dan MySQL&lt;/title&gt;
	&lt;/head&gt;
	&lt;body&gt;
&lt;?php
	if($_GET['aksi'] == 'tambahsub') { ?&gt;
		&lt;form method="POST" action="tambah_sub.php"&gt;
			&lt;input name="nama_sub" type="text" /&gt;&lt;br /&gt;
			&lt;select name="category"&gt;
				&lt;option value="0"&gt;Pilih Kategori&lt;/option&gt;
			&lt;?php
				$sql = mysql_query("SELECT id, category FROM category");

				while($r=mysql_fetch_array($sql)) {

					echo "&lt;option value=".$r['id']."&gt;".$r['category']."&lt;/option&gt;";

				}
			?&gt;
			&lt;/select&gt;*)Silahkan Masukan Nama kategori
			&lt;p&gt;&lt;input type="submit" value="Submit" name="submit" /&gt;&lt;/p&gt;
		&lt;/form&gt;
&lt;?php }
	if($_GET['aksi'] == 'tambahkategori') { ?&gt;
		&lt;p&gt;Masukan Nama Kategori&lt;/p&gt;
		&lt;form method="POST" action="tambah_kat.php"&gt;
			&lt;input type="text" name="nama_category" /&gt;
			&lt;input type="submit" value="Submit" /&gt;
		&lt;/form&gt;
&lt;?php } ?&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

ya itulah skirp untuk menampilkan form input kategori dan sub kategori**, **dapat dilihat bahwa form action-nya membutuhkan dua file yang bernama **tambah_sub.php** dan **tambah_kat.php , **oke sekarang lanjut kita akan membuat ke dua file tersebut langsung salin aja sintaks dibawah ini hheehe.

Pertama agan buat file yang bernama **tambah_sub.php **

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	mysql_connect('localhost','root','') or die("Koneksi gagal");
	mysql_select_db('nama database yang agan buat') or die("Database tidak bisa dibuka");

	$sql = mysql_query("INSERT INTO sub_category (id_sub, id_category, nama_sub) VALUES ('','$_POST[category]','$_POST[nama_sub]')") or die (mysql_error());

	if($sql) {
		echo "&lt;h2&gt;PROSES INPUT SUB KATEGORI BERHASIL&lt;/h2&gt;&lt;p&gt;&lt;a href='sub.php'&gt;Klik Disini Untuk Melihat&lt;/a&gt;&lt;/p&gt;";
	}
?&gt;
</pre>

Sekarang file kedua yang agan buat adalah **tambah_kat.php **

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	mysql_connect('localhost','root','') or die("Koneksi gagal");
	mysql_select_db('nama database yang agan buat') or die("Database tidak bisa dibuka");

	$sql = mysql_query("INSERT INTO category (id, category) VALUES ('','$_POST[nama_category]')") or die (mysql_error());

	if($sql) {
		echo "&lt;h2&gt;PROSES INPUT KATEGORI BERHASIL&lt;/h2&gt;&lt;p&gt;&lt;a href='sub.php'&gt;Klik Disini Untuk Melihat&lt;/a&gt;&lt;/p&gt;";
	}
?&gt;
</pre>

Baiklah mungkin segitu dulu postingan hari ini. Ohh ya jika ada kesalahan langsung aja kasih komentarnya ya gannnnn!!!

## SALAM BLOGGER!!!!!