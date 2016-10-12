---
id: 812
title: Mengecek Online User Unik PHP dan MySQL + AJAX Simple
date: 2013-04-14T20:36:22+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=812
permalink: /2013/04/14/mengecek-online-user-unik-php-dan-mysql-ajax-simple/
categories:
  - php
  - Tutorial
tags:
  - Mengecek Online User Unik PHP dan MySQL + AJAX Simple
  - online user php
  - online user php dan mysql
---
Pada postingan kali ini saya akan mencoba mengulas mengenai pengecekan pengguna atau pengecekan user yang sedang online dalam website kita. Ohh ya sebelumnya saya sebelumnya saya memposting mengenai hal ini mungkin terinspirasi oleh seorang teman yang bertanya kepada saya tentang cara bagaiman untuk mengetahui pengunjung yang sedang online di website kita. Mungkin sudah tidak asing lagi yaa.. dengan judul yang satu ini, dan mungkin agan &#8211; agan dan aganwati   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />sekalian udah pada tahu bagaimana cara membuatnya.

Tetapi pada kasus ini saya akan mengintegrasikannya dengan AJAX, kenapa harus sambil menggunakan AJAX?? ohh ya jadi begini ceritanya.., berawal ketika saya membuat kode standar untuk membuat pengecekan online user dan ketika itu semuanya berjalan dengan lancar dalam kasus ini saya menggunakan 2 browser. Ketika saya buka browser skrip nya berjalan dengan baik dan menunjukan 2 pengunjung yang sedang online. Tapi setelah browser ke-dua saya tutup window-nya, pada browser pertama tadi tetap menampilkan dua pengunjung yang sedang online hingga saya me-refresh browser pertama tadi jadii dengan AJAX ini kita tidak perlu me-refresh lagi untuk mengecek berapa orang yang benar-benar online pada waktu tersebut  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />.

<a href="http://hitamcoklat.com/wp-content/uploads/2013/04/close_pointer.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[812]" title="close_pointer"><img class="aligncenter size-full wp-image-823" title="close_pointer" src="http://hitamcoklat.com/wp-content/uploads/2013/04/close_pointer.jpg" alt="close_pointer" width="409" height="229" /></a>

Ohh ya sebelumnya bisa dikatakan unik karena saya menggunakan fungsi dari pengambilan **session_id** untuk mebuat setiap browser tampak unik selain itu skrip ini juga mirip &#8211; mirip dengan aplikasi chating yang ketika kita menutup jendela obrolan kita maka pengunjung yang sedang online akan berkurang&#8230;bagaimana? asyikan? hahah maaf saya terlalu lebay hehe&#8230;Oke langsung aja ke pembahasan ya, Cekidot ikuti langkah dibawah ini&#8230;

## 1.Pembuatan Table

Berikut adalah gambar penampakan table yang akan dibuat..

<a href="http://hitamcoklat.com/wp-content/uploads/2013/04/g_table.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[812]" title="g_table"><img class="aligncenter size-full wp-image-817" title="g_table" src="http://hitamcoklat.com/wp-content/uploads/2013/04/g_table.jpg" alt="g_table" width="390" height="83" /></a>

karena kita akan membuat skrip online usernya yang simple, jadi saya kira sudah lebih dari cukup untuk menggunakan dua field saja hehe  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />, Untuk sintaks MySQL nya silahkan lihat dibawah ini&#8230;

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `online_user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_session` varchar(32) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=latin1 AUTO_INCREMENT=44 ;
</pre>

## 2. File koneksi.php

Seperti biasa kita buat file koneksi secara terpisah  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

<pre class="brush: php; title: ; notranslate" title="">&lt;?php

	$host ='localhost';
	$user ='root';
	$pass ='';
	$dbase   ='herey';

	$koneksi = mysql_connect($host, $user, $pass);
	
	if (!$koneksi)
	{
		die ('Tidak Bisa Konek: ' . mysql_error());
	}
	
	mysql_select_db($dbase, $koneksi);
	
?&gt;
</pre>

## 4.File cekOnline.php

File ini berfungsi untuk mengecek apakah user sedang online atau tidak dengan cara melakukan pengecekan ke dalam tabel.

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
include "koneksi.php";

$query = mysql_query("SELECT * FROM online_user");

$hitung = mysql_num_rows($query);

echo $hitung;
?&gt;
</pre>

dapat dilihat bahwa kita menggunakan fungsi **mysql\_num\_rows() **untuk menghitung jumlah rows yang ada dalam table yang dengan kata lain merupakan jumlah user yang sedang online  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

## 5. File online.php

File ini berfungsi untuk memasukan nilai kedalam tabel.

<pre class="brush: php; title: ; notranslate" title="">&lt;?php

include "koneksi.php";

session_start();

$id_saya = session_id();

$query = mysql_query("SELECT id_session FROM online_user WHERE id_session = '".$id_saya."'");

$query2 = mysql_fetch_array($query);

if ($query2 == null)
{
	mysql_query("INSERT INTO online_user (id, id_session) VALUES ('', '$id_saya')");
}


?&gt;
</pre>

Dapat dilihat bahwa pada awal &#8211; awal baris kita menggunakan fungsi session yaitu **session_start() **yang berguna untuk memulai session dan mengecek setiap user yang unik atau berbeda seperti yang sudah dijelaskan diatas hehe  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />. Jika dijelaskan skrip diatas adalah kita akan melakukan insert query kedalam table jika **id_session** tidak sama dengan variable **$id_saya** yang berarti browser yang kita pakai  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

## 6. File exit.php

File ini berguna untuk menghapus sesi online kita.

<pre class="brush: php; title: ; notranslate" title="">&lt;?php

session_start();

$id_saya = session_id();

include "koneksi.php";

mysql_query("DELETE FROM online_user WHERE id_session='".$id_saya."'");

session_destroy();

?&gt;
</pre>

## 7. File index.php

File ini berfungsi untuk menampilkan pengunjung yang online, ohh ya file nya disatuin aja yaa sama javascriptnya biar agak jelas hehe..

<pre class="brush: php; title: ; notranslate" title="">&lt;html&gt;
	&lt;head&gt;
		&lt;script&gt;
            //Skirp yang wajib ada jika ingin menggunakan AJAX
            function GetXmlHttpObject()
                {
                var xmlHttp;

                try
                    {
                    // Firefox, Opera 8.0+, Safari
                    xmlHttp = new XMLHttpRequest();
                    }
                catch (e)
                    {
                    //Internet Explorer
                    try
                        {
                        xmlHttp = new ActiveXObject("Msxml2.XMLHTTP");
                        }
                    catch (e)
                        {
                        xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
                        }
                    }

                return xmlHttp;
                }
				
			function cekOnline()
			{
				xmlHttp = GetXmlHttpObject();
				
				if (xmlHttp == null)
				{
					alert("Browser Anda Tidak Mendukung HTTP Request");
					return;
				}
				
				var url = "cekOnline.php";
				xmlHttp.open("POST", url, true);
				xmlHttp.onreadystatechange = stateChanged;
				xmlHttp.send(null);
			}
			
            function stateChanged()
                {
                if (xmlHttp.readyState == 4 || xmlHttp.readyState == 0)
                    {
                    var hitung = xmlHttp.responseText;
                    document.getElementById("jumlahOnline").innerHTML = "&lt;font color='red'&gt;" + hitung + "&lt;/font&gt; user online";
                    window.setTimeout("cekOnline();", 2000);
                    }
                }
			
			function online()
			{
                online = GetXmlHttpObject();

                if (online == null)
                    {
                    alert("Browser Anda Tidak Mendukung HTTP Request");
                    return;
                    }

                var url = "online.php";
                online.open("POST", url, true);
                online.onreadystatechange = responeOnline;
                online.send(null);
			}
			
			function responeOnline()
			{
                if (online.readyState == 4 || online.readyState == 0)
                    {
                    cekOnline();
                    }
			}
						
			function exit()
			{
				exit = GetXmlHttpObject();
				
				if (exit == null)
				{
					alert("Browser Tidak Support HTTP Request");
					return;
				}
				
				var url = "exit.php";
				exit.open("POST", url, true);
				exit.send(null);
			}
						
		&lt;/script&gt;
	&lt;/head&gt;
	
	&lt;body onload="online();" onbeforeunload="exit();"&gt;
		&lt;h1&gt;Yang sekarang sedang Online adalah: &lt;span id="jumlahOnline"&gt;&lt;/span&gt; &lt;/h1&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

Baiklah dapat dilihat bahwa pada

  * Baris ke 5 sampai baris ke 28 merupakan baris yang biasa digunakan dalam menggunakan AJAX, yaitu pendeklarasian penggunaan dalam XMLHttpRequest yang dilakukan didalam sebuah javascript..
  * Baris ke 30 sampai 54 merupakan fungsi untuk membuat request ke server untuk mebuka file **cekOnline.php** setelah itu pada baris ke 46 akan mengupdate data dengan elemen di html yang memiliki **id=&#8221;jumlahOnline&#8221;**
  * Pada baris ke 56 sampai baris 78 merupkan fungsi untuk membuat request ke server untuk membuka file online.php yang didalam file tersebut sudah dijelaskan diatas yaitu untuk memasukan nilai user yang sedang online yang setelah itu membuat respon pada fungsi **responOnline()**
  * Baris 80 sampai baris 93 merupakan fungsi untuk membuat request ke server untuk membuka file file exit.php yang berfungsi untuk melakukan delete rows pada table yang memiliki nilai dari id_session kita..
  * Baris ke 98 merupakan tag HTML body yang memiliki **onload event** yang berfungsi ketika halaman di load maka jalankan fungsi **online()** dan **onbeforeunload** event yang berfungsi untuk menjalankan fungsi **exit()**
  * Baris ke 99 terlihat tag HTML **<span>** yang memiliki attribut **id=&#8221;jumlahOnline&#8221;** yang berfungsi untuk menampilkan jumlah user yang sedang online dengan memanfaatkan **fungsi jumlahOnline** tadi  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

<div>
  Ohh ya untuk penampakannya seperti nampak pada gambar dibawah ini&#8230;
</div>

<div>
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/04/online_user.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[812]" title="online_user"><img class="aligncenter size-full wp-image-827" title="online_user" src="http://hitamcoklat.com/wp-content/uploads/2013/04/online_user.jpg" alt="online_user" width="515" height="175" /></a>
</div>

Keterangan:

Ohh ya karena dalam skrip ini memanfaatkan event onbeforeunload() oleh karenan itu skrip ini akan berjalan dengan baik jika menggunakan chrome dan internet explorer  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Salam Blogger!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />