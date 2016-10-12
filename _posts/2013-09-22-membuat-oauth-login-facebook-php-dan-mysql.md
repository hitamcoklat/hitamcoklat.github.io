---
id: 945
title: Membuat OAuth Login Facebook PHP dan MySQL
date: 2013-09-22T19:57:34+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=945
permalink: /2013/09/22/membuat-oauth-login-facebook-php-dan-mysql/
categories:
  - php
  - Tutorial
tags:
  - Faceboko Login PHP dan MySQL
  - Facebook Login
  - Membuat Facebook Connect
  - Membuat Login Facebook PHP
  - Membuat Oauth Facebook PHP
---
Bagi anda yang sering mengunjungi website, baik itu web portal atau toko online yang sering menanyakan informasi terhadap pengunjung webnya. Salah satu nya adalah untuk mengantisipisasi orang yang sedang berkunjung di website kita adalah orang. Halaaahh sampe segitunya, haha kita ambil contoh lainnya, mungkin kita pernah diminta untuk melakukan SignUp atau Login menggunakan akun facebook anda? kok bisa ya kita login dengan menggunakan akun Facebook kita? untuk penjelasannya coba deh googling dengan keyword &#8220;apa itu OAuth?&#8221;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Baiklah jika kita sudah mengetahui jawaban mengenai OAuth itu sendiri kita akan membuat skrip login sederhana menggunakan Facebook Login. Mengapa kita menggunakan Facebook Login? mungkin jaman sekarang siapa yang tidak memiliki akun Facebook? walaupun akun tersebut jarang sekali dibuka hehe&#8230; ya dengan adanya Facebook Login ini kita dapat mempersingkat waktu pengunjung website kita dalam proses login itu sendiri karena kita diberi akses untuk mengetahui data publik pengunjung kita tanpa harus mengetiknya, bagaimana? masih bingung? hehe

Jadi intinya dengan menggunakan fasilitas Facebook login ini, anda diberi kemudahan dalam proses login dalam suatu website karena memanfaatkan informasi dari Facebook anda  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Oke langsung aja pada penerapannya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

## Langkah 1 : Database

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE `users` (
    `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
    `oauth_provider` varchar(10),
    `oauth_uid` text,
    `username` text,
    PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1;

</pre>

Dalam table tersebut terdapat id, oauth\_provider, oauth\_uid dan username yang nantinya akan menyimpan data-data facebook user setelah melakukan login..

## Langkah 2 : Membuat Aplikasi di Facebook

Untuk dapat mendaftarkan aplikasi anda di facebook caranya mudah sekali, silahkan klik http://developers.facebook.com setelah itu nanti kamu bakalan disuruh untuk mengisi beberapa field seperti tampak pada gambar dibawah ini..

<img class="alignnone size-full wp-image-947" title="facebook_apps" src="http://hitamcoklat.com/wp-content/uploads/2013/09/facebook_apps.png" alt="" width="799" height="588" />

Keterangan :

  1. Pada label nomer satu yaitu AppId dan AppSecret yang nantinya kamu gunakan untuk menggunakan Facebook PHP SDK yang nantinya kita akan gunakan  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />
  2. Pada label nomer dua berisi field yang digunakan ketika script login kita dijalankan atau di redirect  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Oke selanjutnya kita akan mendownload ramuan intinya, disini kita akan menggunakan Facebook PHP SDK, maka silahkan klik link dibawah ini

<a href="https://github.com/facebook/facebook-php-sdk" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">https://github.com/facebook/facebook-php-sdk</a>

Jika anda sudah mendownloadnya, seharusnya terdapat beberapa file.. sekarang kita fokus saja pada file yang berada di dalam folder **/src**

didalam folder **/src** tadi seharusnya berisi dua buah file yaitu:

  1. base_facebook.php
  2. facebook.php

## Langkah 3 : Penerapan Skrip

Baiklah langkah terakhir yaitu penerapan Facebook PHP SDK tersebut pada aplikasi website yang kita buat. Disini anggap saja kita memiliki dua buah file atau dua buah halaman&#8230;

  1. Halaman pertama berfungsi sebagai halaman awal dari aplikasi kita, jadi di halaman ini terdapat link yang ditujukan pada pengguna untuk memulai login menggunakan Facebook Login
  2. Halaman kedua berfungsi untuk memproses ketika user melakukan login facebook dan memasukan data user tersebut kedalam table yang telah kita buat sebelumnya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

<div>
  NOTE: sebelumnya perlu diketahui bahwa pada postingan ini sistem folder adalah sebagai berikut:
</div>

<div>
  <ul>
    <li>
      ROOT <ul>
        <li>
          Folder <strong>src</strong> <ul>
            <li>
              File <strong>facebook.php</strong>
            </li>
            <li>
              File <strong>base_facebook.php</strong>
            </li>
          </ul>
        </li>
        
        <li>
          Folder <strong>Login</strong> <ul>
            <li>
              File <strong>index.php</strong>
            </li>
            <li>
              File <strong>proses.php</strong>
            </li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</div>

Oke langsung saja ya, pertama kita buat dulu file yang bernama index.php

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
&lt;?php

session_start();
?&gt;
&lt;h2&gt;Welcome,
&lt;?php
	if(!empty($_SESSION) {
		echo $_SESSION['username'];
	} else {
		echo 'Guest | &lt;a href="proses.php"&gt;Login?&lt;/a&gt;';
?&gt;&lt;/h2&gt;
</pre>

File tersebut jika dijalankan memiliki dua kondisi, yaitu ketika pengguna belum mendaftar maka akan memunculkan link untuk login dengan menggunakan Facebook Login tetapi jika pengguna telah melakukan login dan datanya sudah ada dalam table kita maka akan memunculkan username Facebook pengguna  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Selanjutnya kita buat file proses.php yang isinya sebagai berikut..

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
session_start();
require '../src/facebook.php';

$facebook = new Facebook(array(
  'appId'  =&gt; 'nama_app_id_anda',
  'secret' =&gt; 'nama_app_secret_anda',
));

// Get User ID
$user = $facebook-&gt;getUser();

if (!empty($user)) {
  try {

    $user_profile = $facebook-&gt;api('/me');
  } catch (FacebookApiException $e) {
    error_log($e);
    $user = null;
  }

  if(!empty($user_profile)) {

		mysql_connect('localhost', 'root', '');
		mysql_select_db('nama_database');

		//Mengecek apakah user sudah mendaftar atau belum
		$query = mysql_query("SELECT * FROM users WHERE oauth_provider = 'facebook' AND oauth_uid = ".$user_profile['id']);
		$result = mysql_fetch_array($query);

		if($result == null) {

			//Memasukan data user
			$query = mysql_query("INSERT INTO users(oauth_provider, oauth_uid, username) VALUES('facebook', {$user_profile['id']}, '{$user_profile['username']}')");
			$query = mysql_query("SELECT * FROM users WHERE id = ".mysql_insert_id());
			$result = mysql_fetch_array($query);
		}
		// Mengeset SESSION
		$_SESSION['id'] = $result['id'];
		$_SESSION['oauth_uid'] = $result['oauth_uid'];
		$_SESSION['oauth_provider'] = $result['oauth_provider'];
		$_SESSION['username'] = $result['username'];

	}
	  else {
		die("Terjadi Kesalahan");
		}
}
else {

	$login_url = $facebook-&gt;getLoginUrl();
	header("Location: ".$login_url);
}
?&gt;

</pre>

File proses.php tersebut berfungsi untuk mengecek apakah user telah terdaftar dalam table atau website kita? jika sudah terdaftar maka akan diset session dan dikembalikan ke halaman index.php tetapi jika belum maka akan dilakukan proses redirect ke halaman login facebook dengan memanfaatkan sintaks $facebook->getLoginUrl(); pada bagian akhir baris&#8230;

## Langkah 4 : Pengetesan

Untuk langkah pengetesan ini, silahkan anda masukan url yang merujuk pada **index.php** tadi, dan jika sudah seharusnya anda diharuskan login karena session anda belum dibuat. Untuk dapat dibuatkan session maka anda disuruh untuk mengklik login dan ketika anda klik login anda merujuk pada halaman login facebook. Setelah anda berhasil login maka anda dikembalikan pada halaman **proses.php** tadi yang berfungsi untuk mengambil data publik facebook anda dan memasukannya kedalam tabel database yang telah kita buat tadi. Setelah data kita berada di dalam tabel database tersebut maka secara otomatis user tersebut dibuat kan session&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Oke dengan dua buah file tadi yang telah kita buat dan ditambah Facebook SDK untuk Login telah selesai&#8230; Sekarang silahkan mencobanya. Dengan adanya fasilitas login seperti ini maka diharapkan proses login akan lebih mudah dan menyenangkan   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />heheh

Sekian postingan kali ini   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />Salam Blogger!