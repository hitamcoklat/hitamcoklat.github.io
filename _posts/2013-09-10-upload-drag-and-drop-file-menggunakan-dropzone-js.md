---
id: 917
title: Upload Drag and Drop File Menggunakan dropzone.js
date: 2013-09-10T13:42:02+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=917
permalink: /2013/09/10/upload-drag-and-drop-file-menggunakan-dropzone-js/
categories:
  - php
  - Tutorial
tags:
  - drag and drop
  - drag and drop dropzone
  - drag and drop php
  - dropzone
  - fitur drag and drop
---
Bagi kalian yang sering menggunakan toko online atau sering menggunakan wordpress sebagai media untuk berinternet atau saling berbagi mungkin tidak akan asing lagi dengan fitur ini. Ya! mungkin waktu dulu kita menggunakan input type file untuk mengupload sebuah file dan kita harus browse dan memilih file yang akan kita upload.. wow panjang banget ya kalo dipikir2 dan sangat ribet. Lebay banget ya padahal ga seribet itu.. hehhe

Dengan seiring kemajuan teknologi dan semakin banyak nya para inventor muda yang terus mengembangkan library javascript kita sekarang dimudahkan dalam memanfaatkan internet. Salah satunya pemanfatan library dropzone.js yang dapat memudahkan kita dalam mengupload secara multiple bahkan kita dapat mengupload nya secara Drag and Drop alias tinggal tarik saja file yang akan kita upload   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />Mudah bukan?

<a href="http://hitamcoklat.com/wp-content/uploads/2013/09/dropzone.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[917]" title="dropzone"><img class="aligncenter size-full wp-image-918" title="dropzone" src="http://hitamcoklat.com/wp-content/uploads/2013/09/dropzone.jpg" alt="drag and drop" width="600" height="350" /></a>

bagaimana? bagi pengguna wordpress mungkin sudah tidak asing dengan gambar bacaan diatas, sewaktu kalian melakukan posting artikel kalian diminta untuk melakukan upload file melalu drag and drop atau melalui select file  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />&#8230;

Plugin Dropzone ini memiliki beberapa kelebihan seperti,

  1. Diberi kemudahan mengostumisasi CSS dan tampilannya
  2. Membuat Thumbnail pada gambar yang kita upload nanti
  3. Multiple Upload file, jadi kita bisa mengupload sebanyak &#8211; banyaknya ke dalam folder
  4. Memiliki Callback event sehingga kita mengetahui file mana yang berhasil kita upload nanti

Nah sekarang bagaimana kita mengimplementasikan library dropzone.js ini  pada website kita, berikut penerapan simplenya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

  * ## Download File

Untuk dapat mendownload file silahkan kunjungi <a href="http://www.dropzonejs.com/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.dropzonejs.com']);">http://www.dropzonejs.com/</a> untuk dapat mendowload file nya silahkan klik <a href="https://github.com/enyo/dropzone/tree/master/downloads" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://github.com']);">https://github.com/enyo/dropzone/tree/master/downloads</a>

Jika sudah di download maka akan berisi file sebagai berikut

  1. Folder CSS
  2. Folder Images
  3. File dropzone.js
  4. File dropzone.min.js
  5. dropzone-amd-module.js
  6. dropzone-amd-module.min.js

  * ## Mempersiapkan File Index.php

Pada dasarnya untuk dapat mengupload sesuatu kita membutuhkan form, baiklah di dalam file index.php tadi seperti syntax berikut

<pre class="brush: php; title: ; notranslate" title="">&lt;form action="proses.php" class="dropzone" id="my-awesome-dropzone"&gt;
			&lt;div class="fallback"&gt;
				&lt;input type="file" name="file" /&gt;
			&lt;/div&gt;
		&lt;/form&gt;
</pre>

pada sintaks diatas dapat dilihat bahwa aksi pada mengacu pada file **proses.php **dan memiliki class **dropzone **dan id **my-awesome-dropzone **yang nanti nya akan kita gunakan pada pada library dropzone nya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Setelah sintaks form tadi selesai maka kita persiapkan sintaks untuk head pada html nya yang berisi sintaks javascript sebagai berikut

<pre class="brush: php; title: ; notranslate" title="">&lt;!DOCTYPE html&gt;
&lt;html&gt;
	&lt;head&gt;
		&lt;link rel="stylesheet" href="css/dropzone.css" type="text/css" /&gt;
		&lt;script src="dropzone.js"&gt;&lt;/script&gt;
		&lt;script src="jquery.js"&gt;&lt;/script&gt;
		&lt;script&gt;
			var Dropzone = require("dropzone");

			$("div#my-awesome-dropzone").dropzone({ url: "proses.php" });

		&lt;/script&gt;
</pre>

Pada bagian header diatas dilakukan pemanggilan CSS dropzone, jquery, dan library dropzone itu sendiri. Setelah itu dilakukan proses eksekusi fungsi pada library dropzone.js

Baiklah  file index.php tersebut ditulis lengkap maka akan seperti dibawah ini sintaksnya

<pre class="brush: php; title: ; notranslate" title="">&lt;!DOCTYPE html&gt;
&lt;html&gt;
	&lt;head&gt;
		&lt;link rel="stylesheet" href="css/dropzone.css" type="text/css" /&gt;
		&lt;script src="dropzone.js"&gt;&lt;/script&gt;
		&lt;script src="jquery.js"&gt;&lt;/script&gt;
		&lt;script&gt;
			var Dropzone = require("dropzone");

			$("div#my-awesome-dropzone").dropzone({ url: "proses.php" });

		&lt;/script&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;form action="proses.php" class="dropzone" id="my-awesome-dropzone"&gt;
			&lt;div class="fallback"&gt;
				&lt;input type="file" name="file" /&gt;
			&lt;/div&gt;
		&lt;/form&gt;
	&lt;/body&gt;
&lt;/html&gt;
</pre>

  * ## Membuat File Proses.php

File proses.php ini berguna untuk proses pemindahan file kedalam suatu folder dimana folder yang akan dipakai adalah folder bernama **file , **selanjutnya masukan sintaks berikut

<pre class="brush: php; title: ; notranslate" title="">$ds = "/";

	$storeFolder = 'file';

	if(!empty($_FILES)) {
		$tempFile = $_FILES['file']['tmp_name'];
		$targetPath = dirname(__FILE__) . $ds . $storeFolder . $ds;
		$targetFile = $targetPath . $_FILES['file']['name'];
		move_uploaded_file($tempFile, $targetFile);
	}
</pre>

Sintaks diatas merupakan sintaks untuk memindahkan file yang akan diupload kedalam folder yang bernama **file. **Selanjutnya jika file proses.php tersebut sudah selesai maka kita buat file yang bernama **file.**

Jika semuanya sudah dilakukan, langkah terakhir adalah menguji coba aplikasi aplikasi tadi di localhost, jika langkahnya benar maka seharusnya tampil sebagai berikut&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

<a href="http://hitamcoklat.com/wp-content/uploads/2013/09/FireShot-Screen-Capture-051-localhost_septian_tes_dropzone.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[917]" title="Dropzone Upload"><img class="aligncenter size-full wp-image-923" title="Dropzone Upload" src="http://hitamcoklat.com/wp-content/uploads/2013/09/FireShot-Screen-Capture-051-localhost_septian_tes_dropzone.png" alt="Dropzone Upload" width="664" height="305" /></a>

dan sekarang lihat ke dalam folder **file **anda, seharusnya file yang anda upload tadi sudah berada di dalam folder tersebut  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Bagaimana? mudah bukan? hehe plugin ini juga dapat di integrasikan dengan proses penginputan produk pada toko online dan aplikasi lainnya sehingga toko online dan aplikasi kita terlihat elegann hahaha  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />