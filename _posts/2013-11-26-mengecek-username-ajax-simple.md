---
id: 983
title: 'Mengecek Username Ajax &#8211; Simple'
date: 2013-11-26T01:58:20+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=983
permalink: /2013/11/26/mengecek-username-ajax-simple/
categories:
  - php
  - Tutorial
tags:
  - cek username
  - mengecek username ajax
  - username ajax
---
Mungkin sudah gak asing lagi ya tentang sistem mengecek ketersediaan data disebuah database hehe..tapi ga apa2 lah pengen berbagi sedikit mengenai sistem ini, kebetulan kemarin ada sedikit pekerjaan yang mengharuskan menggunakan sistem ini dan alhamdulillah sekarang dapat memposting pada blog ini.

Sebetulnya ada banyak sekali library jquery yang mungkin lebih canggih lagi dari sistem yang akan kita buat sekarang, tapi pada dasarnya sama saja dalam penggunaannya, yakni ketika kita mengecek suatu data maka data tersebut di proses dengan memanfaatkan ajax  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />. Baiklah langsung aja ya.. Semoga bermanfaat  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

## Database

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `users` (
          `id` int(11) NOT NULL AUTO_INCREMENT,
          `username` varchar(32) NOT NULL,
          `password` varchar(32) NOT NULL,
          PRIMARY KEY (`id`)
        );
</pre>

selanjutnya isi tabel nya

<pre class="brush: php; title: ; notranslate" title="">INSERT INTO `users` (`id`, `username`, `password`) VALUES
(1, 'budi', 'budi'),
(2, 'rudi', 'rudi'),
(3, 'tian', 'tian')
</pre>

## Langkah Pertama

Buatlah sebuah file index.html yang berisi dua input text login dan password. Setelah itu buatlah tag anchor yang nantinya digunakan untuk mengecek username yang akan kita ketik. Jika sudah maka tampilan ketersediaan username akan ditampilkan pada tag span yang ada pada HTMLnya. Berikut adalah sintaks HTML nya

<pre class="brush: xml; title: ; notranslate" title="">&lt;html&gt;
	&lt;head&gt;
		&lt;title&gt;Mengecek Username&lt;/title&gt;
		&lt;style&gt;
			body {
				font-family: Arial;
			}
			input, textarea {
				vertical-align: top;
			}
			fieldset {
				width: 400px;
			}
			label {
				float: left;
				width: 150px;
			}
			#error {
				font-weight: bold;
				color: #ff0000;
			}
		&lt;/style&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;fieldset&gt;
			&lt;legend&gt;&lt;strong&gt;Tambahkan Username dan Password&lt;/strong&gt;&lt;/legend&gt;
			&lt;form action="" method="POST" id="loginForm"&gt;
				&lt;p&gt;
					&lt;label&gt;Username&lt;/label&gt;
					&lt;input type="text" name="loginName" id="loginName" /&gt;
					&lt;a href="#" id="check"&gt;Check&lt;/a&gt;
					&lt;span id="status" style="float: right;"&gt;&lt;/span&gt;
				&lt;/p&gt;
				&lt;p&gt;
					&lt;label&gt;Password&lt;/label&gt;
					&lt;input type="password" name="password" /&gt;
				&lt;/p&gt;
				&lt;p&gt;
					&lt;span id="error"&gt;&lt;/span&gt;
				&lt;/p&gt;
				&lt;p&gt;
					&lt;input type="submit" value="Save" name="save" id="save" /&gt;
				&lt;/p&gt;
			&lt;/form&gt;
		&lt;/fieldset&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

Jika kita jalankan sintaks diatas maka akan tampil seperti gambar dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2013/11/cek_user1.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[983]" title="cek_user1"><img class="alignnone size-full wp-image-984" title="cek_user1" src="http://hitamcoklat.com/wp-content/uploads/2013/11/cek_user1.png" alt="cek_user1" width="454" height="197" /></a>

## Langkah Kedua

Langkah selanjutnya adalah menambahkan beberapa fungsi jquery kedalam head pada file HTML diatas dengan ditambahkan sintaks berikut ini..

<pre class="brush: jscript; title: ; notranslate" title="">&lt;script src="jquery.js"&gt;&lt;/script&gt;
		&lt;script&gt;
			$(document).ready(function (){

				var checked = false;

				$('#check').click(function (){

					$('#error').empty();
					var inputValue = $('#loginName').val();

					if (jQuery.trim(inputValue) == ''){
						return false;
					}
					$.post(
						'proses.php',
						{ username : inputValue },
						function (data)
						{
							if (data)
							{
								checked = true;
								$('#status').html('Username Tersedia');
							}
							else
							{
								checked = false;
								$('#status').html('Username sudah dipakai');
								return false;
							}
						}
					);
				});
				$('#loginForm').submit(function (){

					if (checked == false)
					{
						$('#error').html('Silahkan Cek Username');
						return false;
					}
					else
					{
						return false;
					}
				});
				$('#loginName').focus(function (){
					checked == false;
				});
			});
		&lt;/script&gt;
</pre>

Dapat dilihat bahwa sintaks diatas mengandung beberapa event jQuery yang berfungsi ketika kita mengklik check pada elemen ID check akan mengirim data berupa ajax request kepada file proses.php yang akan kita buat selanjutnya yang mengembalikan nilai true atau false tergantung kepada username yang kita cek. Oke supaya lebih jelas kita lanjutkan dulu ke langkah selanjutnya yaitu pembuatan file proses.php.. Oke cekidot

## Langkah Ketiga

Langkah selanjutnya yaitu membuat file proses.php yang mana akan berhubungan dengan database nanti, langsung aja ke sintaksnya ya..

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
mysql_connect("localhost","root","") or die("Koneksi gagal");
mysql_select_db("") or die("Database tidak bisa dibuka");

	$sql = mysql_query("SELECT username as user FROM users WHERE username = '".$_POST['username']."' LIMIT 1");

	$hitung = mysql_num_rows($sql);

	if ($sql)
	{
		if ($hitung &gt; 0)
		{
			echo false;
		}
		else
		{
			echo true;
		}
	}
	else
	{
		echo false;
	}
?&gt;
</pre>

Jika sudah maka silahkan jalankan file index.html tadi yang telah kita buat diawal. Setelah itu ketika username didalam input text nya. Ketika kamu mengklik pada pada anchor Check anda akan menerima pesan seperti dibawah ini. Ketika kamu mengetikan username yang sudah tersedia didalam table database maka akan tampil seperti gambar dibawah ini..

<a href="http://hitamcoklat.com/wp-content/uploads/2013/11/cek_user2.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[983]" title="cek_user2"><img class="alignnone size-full wp-image-987" title="cek_user2" src="http://hitamcoklat.com/wp-content/uploads/2013/11/cek_user2.png" alt="cek_user2" width="441" height="183" /></a>