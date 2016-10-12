---
id: 1298
title: API Programming Studi Kasus Twitter Search Part 1
date: 2016-07-28T17:01:27+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=1298
permalink: /2016/07/28/api-programming-studi-kasus-twitter-search-part-1/
categories:
  - php
  - Tutorial
tags:
  - api programming
  - php
  - twitter api
---
Mau share dikit tentang API Programming. Apa itu API Programming? ya, untuk lebih jelasnya silahkan googling2 dahulu, soalnya udah banyak blog yang bikin artikel tentang API Programming hehhe. Atau menurut wikipedia silahkan cek link berikut:

<a href="https://id.wikipedia.org/wiki/Antarmuka_pemrograman_aplikasi" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://id.wikipedia.org']);">https://id.wikipedia.org/wiki/Antarmuka_pemrograman_aplikasi</a>

Gimana sudah paham?   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />sekarang langsung aja ke studi kasus-nya ya, dalam postingan kali ini saya akan coba buat aplikasi simple dengan memanfaatkan API-nya dari Twitter. Kisi-kisi aplikasi yang akan kita buat adalah aplikasi untuk melakukan search tweet setiap orang.

Untuk lebih jelasnya, silahkan simak trailer dari aplikasi yang akan dibuat dibawah ini  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />



Oke, API yang akan kita buat akan mengambil **name, username, profile\_image, tweet, location, followers\_count, friends_count, timezone**, Gimana? asik ya dengan memanfaatkan sebuah API dari pihak ketiga katakanlah disini **Twitter** kita dapat mengemas kembali aplikasi yang memanfaatkan API yang sudah tersedia (Twitter) dengan ini kita bebas menamakannya aplikasi apapun. Oke, langsung aja ke praktik nya ya

Dalam memanfaatkan API ini, kita membutuhkan sebuah library perantara untuk melakukan autentikasi pada API si Twitter, sebenernya kita bisa membuatnya sendiri dari awal library ini. Namun, seperti yang kita ketahui bahwa ada banyak sekali developer yang membagikan library2 yang telah mereka buat *dan library nya juga keren2  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />. Seperti salah satunya library Twitter Oauth yang satu ini yang menurut saya cukup lengkap. Silahkan anda download terlebih dahulu

<a href="https://github.com/abraham/twitteroauth" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">https://github.com/abraham/twitteroauth</a>

Selanjutnya langkah pembuatan aplikasi dari sisi twitter nya

1. silahkan kunjungi link berikut ini <a href="https://apps.twitter.com/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://apps.twitter.com']);">https://apps.twitter.com</a> setelah itu silahkan login menggunakan akun twitter anda, Jika sudah maka akan muncul tampilan seperti dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2016/07/1.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1298]" title="1"><img src="http://hitamcoklat.com/wp-content/uploads/2016/07/1.png" alt="" title="1" class="alignnone size-full wp-image-1305" /></a>

2. Setelah itu silahkan isi form dibagian **Create an application** lalu klik dibagian Create your <stong>Twitter Application</strong>, cek gambar dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2016/07/2.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1298]" title="2"><img src="http://hitamcoklat.com/wp-content/uploads/2016/07/2-828x1024.png" alt="" title="2" class="alignnone size-large wp-image-1306" /></a>

<a href="http://hitamcoklat.com/wp-content/uploads/2016/07/3.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1298]" title="3 class="><img src="http://hitamcoklat.com/wp-content/uploads/2016/07/3.png" alt="" title="3 class=" /></a>

3. Pilih **Keys and Access Token** Untuk melihat Consumer Keys yang nanti akan kita gunakan dalam membuat aplikasi

<a href="http://hitamcoklat.com/wp-content/uploads/2016/07/4.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[1298]" title="4"><img src="http://hitamcoklat.com/wp-content/uploads/2016/07/4.png" alt="" title="4" class="alignnone size-full wp-image-1308" /></a>

4. Setelah itu, anda akan lihat ada beberapa kode dari API Twitter yang telah anda buat, seperti 

  * Consumer Key
  * Consumer Secret
  * Access Token
  * Access Token Secret

Silahkan salin masing-masing value yang ada di bagian API Twitter anda, lalu paste ke file **config.php** didalam folder **config/config.php**

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	
	$config = array(

				"CONSUMER_KEY" 			=&gt; "YOUR-TWITTER-CONSUMER-KEY", //CONSUMER KEY
				"CONSUMER_SECRET" 		=&gt; "YOUR-TWITTER-CONSUMER-SECRET", // CONSUMER SECRET
				"ACCESS_TOKEN" 			=&gt; "YOUR-TWITTER-ACCESS-TOKEN", // ACCESS TOKEN
				"ACCESS_TOKEN_SECRET" 	=&gt; "YOUR-TWITTER-ACCESS-TOKEN-SECRET" // ACCESS TOKEN SECRET
			 
			 );
</pre>

Gimana? sampai sini mengalami kesulitan? Silahkan komentar di bagian bawah, jika tidak mengalami kesulitan silahkan lanjut ke Bagian 2 nya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />