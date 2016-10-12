---
id: 473
title: Beberapa Teknik Looping Dalam PHP
date: 2012-09-25T10:50:09+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=473
permalink: /2012/09/25/beberapa-teknik-looping-dalam-php/
categories:
  - php
  - Tutorial
tags:
  - Beberapa Teknik Looping Dalam PHP
  - Looping PHP
  - Teknik Looping Dalam PHP
---
Alhamdulillah saya bisa memposting lagiiiii setelah sekian lamanya   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />hehe, ohh ya pada kesempatan kali ini saya akan coba share sedikit pengetahuan saya mengenai Looping atau Pengulangan dalam bahasa pemrograman PHP dari berbagai sumber dan pengalaman pribadi sendiri dan semoga bisa bermanfaat bagi pembacanya amiiin  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />. Ohh ya langsung aja yah udah kebelet hehe  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Looping merupakan salah satu teknik untuk membuat suatu perintah secara berulang-ulang sampai batas yang ditentukan oleh si programmer. Ya dalam dunia pemrograman kita bisa melakukan &#8220;Perulangan&#8221; atau &#8220;Looping&#8221; tanpa merasa capek atau kelelahan, tapi coba kalau kita melakukan perulangan tersebut di dalam dunia nyata haha mungkin kita akan lelah melakukan rutinitas yang diakibatkan oleh proses looping tersebut.

Baiklah langsung saja pada pembahasan yaaa!! Struktur Looping secara umum terdiri atas dua bagian yaitu,

  1. Kondisi pengulangan, yang biasanya merupakan ekspresi boolean yang harus dipenuhi untuk melakukan pengulangan tersebut,
  2. Alogoritma dari looping itu sendiri yang berisi algoritma yang di ulang-ulang

Seorang programer biasanya memilih-milih tipe konstruksi perulangan yang cocok untuk digunakan dalam programnya karena ada beberapa konstruksi pengulangan yang dapat dipakai untuk memecahkan masalah yang sama namu ada juga beberapa konstruksi pengulangan yang hanya cocok untuk dipakai dalam memecahkan masalah tertentu. Ya&#8230;maka dari itu pemilihan kontruksi looping(pengulangan) sangatlah penting dan akan sangat mempengaruhi sekali terhadap kebenaran algoritma pemrograman algoritma kita. Ada beberapa Teknik looping yang pada kesempaatan kali ini akan saya bahas dalam menggunakan bahasa pemrograman PHP seperti,

  * WHILE
  * DO &#8211; WHILE
  * FOR

## _WHILE_

Struktur _**while**_ adalah jenis pengulangan yang penulisan kondisi algoritma nya di awal blok, maksudnya jika kondisi algoritma tadi tidak terpenuhi maka kondisi bernilai _false_ dan proses pengulangan pun tidak akan dilakukan. Dibawah ini merupakan bentuk umum penulisan dari struktur pengulangan menggunakan **_while_**.

_**while(ekspresi) {**_
  
_ **blok program**_
  
_ **}**_

Contoh Lainnya

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$a = 1;
	while($a&lt;=10) {
		echo "$a&lt;br /&gt;";
		$a++;
	}
?&gt;
</pre>

## _FOR_

Sturktur _**for **_biasanya digunakan ketika kita akan melakukan pengulangan yang banyaknya sudah pasti atau sudah diketahui oleh kita sebelumnya. Dalam menuliskan pengulngan _**for **_ini sebelumnya kita harus mendefinisikan inisial dan kondisi terlebih dahulu untuk melakukan pengulangannya. Berikut adalah bentuk umum dari pengulangan menggunakan _**for.**_

_**for (inisial; kondisi; iterasi) {**_
  
_**//isi dari pengulangan**_
  
_**} **_

Contoh lainnya,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$a = 10;
	for($i=10; $i&gt;0; $i--) {
		echo "PHP $a &lt;br /&gt;";
		$a--;
	}
?&gt;
</pre>

Program diatas akan mencetak teks &#8220;PHP&#8221; sebanyak 10 kali dengan indeks dimulai dari 10 sampai 1 (menurun)

Varisai FOR  (Menentukan Bilangan Prima)

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$n = 19; //membuat variable
	$prima = true;

	for($i=2; $i&lt;=($n/2); $i++) {
		if(($n%$i)==0) {
			$prima = false;
			break; //untuk menghentikan looping pada program
		}
	}
	if($prima) {
		echo "$n merupakan bilangan prima";
	} else {
		echo "$n bukan bilangan prima";
	}
?&gt;
</pre>

Contoh Lainnya,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$n = 3; //menentukan variable yang akan ditambahkan
	$hasil = 0;

	for($i=1; $i&lt;=$n; $i++) {
		$hasil += $i;
		if($i !=$n) {
			echo "$i + ";
		} elseif($i = $n) {
			echo "$i = ";
		}
	}
	echo "$hasil";
?&gt;
</pre>

Hasil keluaran program diatas adalah melakukan penjumlahan seperti dibawah ini,

<span style="color: #ff0000;"><strong>1 + 2 + 3 = 6</strong></span>

## _DO &#8211; WHILE_

Sebelumnya kita tadi sudah mengenal pengulangan dengan menggunakan _**while , **_ terus kenapa? haha&#8230;ya karena sebenarnya struktur pengulangan ini mirip dengan struktur _**while**_, mungkin perbedaannya hanya terdapat pada penempatan kondisi saja yang dengan kata lain pada struktur pengulangan ini kondisinya terletak di akhir blok pengulangan sedangkan pada struktur _**while**_ yang kita kenal tadi berada di awal blok pengulangan. Berikut adalah bentuk umun dari penggunaan struktur pengulangan _**do-while**_,

_**inisial**_
  
_**do {**_
  
_**//proses pengulangan**_
  
_**iterasi**_
  
_**} while(kondisi); **_

## _FOREACH_

Selain fungsi yang telah dituliskan diatas PHP juga menyediakan cara mengakses data kedalam bentuk array dengan menggunakan fungsi _**foreach(). **_Adapun sintaknya adalah:

_**foreach($data as $value) {**_
  
_**$pernyataan yang akan diproses yaitu $value
  
} **_

Silahkan ketikan kode dibawah ini, 

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$data = array("Sedan", "Bus", "Angkot", "Kereta Api");
	foreach($data as $value) {
		echo "Kendaraan " . $value;
		echo "&lt;br /&gt;";
	}
?&gt;
</pre>

&nbsp;

### Perulang Dalam Perulangan

Adakalanya dalam menuliskan bahasa pemrograman sering terjadi dimana perulangan tersebut berada dalam pengulangan yang lain. Silahkan ketikan kode dibawah ini,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	for($i=1; $i&lt;=5; $i++) {
		for($d=1; $d&lt;=$i; $d++) {
			echo "A";
		}
	echo "&lt;br /&gt;";
	}
?&gt;
</pre>

Semoga postingan kali ini bermanfaat  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

_**SALAM BLOGGER!!!**_