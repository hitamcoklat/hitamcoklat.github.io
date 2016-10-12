---
id: 227
title: Membuat Image Hosting Menggunakan PHP
date: 2013-06-14T17:04:43+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=227
permalink: /2013/06/14/membuat-image-hosting-menggunakan-php/
categories:
  - php
  - Tutorial
tags:
  - image hosting
  - Image Hosting Menggunakan PHP
  - php upload gambar
---
Bagi kalian pengguna forum atau blog mungkin sudah tidak asing lagi dengan kata &#8220;Image Host&#8221;, ya! dari katanya sendiri dapat diartikan sebagai hosting yang dikhususkan untuk gambar. Sistem dari image hosting tersebut sangat simple yaitu ketika kita mengupload gambar maka akan muncul link embed untuk kita pergunakan selanjutnya.

Ada banyak sekali penyedia layanan hosting gambar sekarang ini, hhmm&#8230; yang sering saya gunakan sekitar ada 4 Contohnya,

  * <span style="color: #ff0000;"><strong>Flikr.com</strong></span>
  * <span style="color: #ff0000;"><strong>Photobucket.com</strong></span>
  * <span style="color: #ff0000;"><strong>Imageshack.us</strong></span>
  * <span style="color: #ff0000;"><strong>Tinypic.com</strong></span>

Hubungan image host dengan dengan internet sangat erat kaitannya khususnya para sahabat blogger atau pengguna forum (Kaskuser) pasti kalian tahu jawabannya hehehe&#8230;

Tapi sekarang ada permasalah lain lagi yang muncul, waktu itu saya menggunakan Imageshack sebagai penyedia hosting gambar saya tapi entah kenapa setelah beberapa hari kemudian gambar yang saya upload berubah gambarnya menjadi kodok!!?? saya berpikir kenapa ini bisa terjadi? ya memang sekarang-sekarang ini hosting gambar gratisan tersebut sudah membatasi jumlah bandwidth untuk mengakses gambarnya dan alasan lainnya hehe.

oke langsung saja kita persiapkan file &#8211; file nya berupa CSS dan file PHPnya,

**style.css**

<pre class="brush: css; title: ; notranslate" title="">.codes {
    display: block;
    width: 100%;
    overflow: scroll;
    white-space: nowrap;
    height: 2.5em;
    font-size: 100%;
    background-color: #FFF;
    color: #000;
    border: 1px solid #000;
}
h1 {
	font-family: Calibri;
	margin-top: 2px;
	text-align: center;
	}
body {
	font-family: 'Ubuntu', sans-serif;
    text-align: center;
    background: #CCC;
}
.wrapper {
	background: #FFF;
    color: #000;
    text-align: left;
    font-family: sans-serif;
	font-weight: 700;
    width: 798px;
	max-width: 800px;
	padding: 10px 10px 10px 10px;
    margin: 80px auto;
	border: 1px solid #CCC;
	}
#showdiv {
    text-align: center;
}
#squares {
    text-align: center;
}
#squares iframe {
    margin: 0 auto;
}
#codes input{
	width: 80%;
}
.footer {
	font-family: Calibri;
	text-align: right;
	font-size: small;
}
.gambar {
	max-width: 700px;
	}

</pre>

File diatas untuk bagian CSS nya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

selanjutnya kita siapkan file bernama **index.php** yang isinya sebagai berikut,

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
$filedir = 'foto';
$maxsize = 1024*1024;
$terima = array('png', 'jpg', 'jpeg', 'gif', 'bmp');
?&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Posting gambar&lt;/title&gt;
&lt;link rel="stylesheet" type="text/css" href="style.css" /&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div class="wrapper"&gt;
&lt;h1&gt;Hitamcoklat - Penyimpanan Gambar &lt;/h1&gt;
&lt;div id="showdiv"&lt;?php if(empty($urlgambar)) { ?&gt; style="display: none;"&lt;?php } ?&gt;&gt;
&lt;img id="showimg" src="&lt;?php if(!empty($urlgambar)) print $urlgambar; else { ?&gt;about:blank&lt;?php } ?&gt;" alt="Loading image..." /&gt;
&lt;/div&gt;

&lt;?php
if($_SERVER['REQUEST_METHOD'] == 'POST') {

        if($_FILES['file']['size'] &lt;= $maxsize) {
            $namafile = $_FILES['file']['name'];
            move_uploaded_file($_FILES['file']['tmp_name'], $filedir.'/'.$namafile);
            $linkurl = 'http://'.$_SERVER['HTTP_HOST'].preg_replace('/\/([^\/]+?)$/', '/', $_SERVER['PHP_SELF']).$namafile;
            $urlgambar = 'http://'.$_SERVER['HTTP_HOST'].preg_replace('/\/([^\/]+?)$/', '/', $_SERVER['PHP_SELF']).$filedir.'/'.$namafile;
            print '&lt;h2&gt;Upload Berhasil!&lt;/h2&gt;
					&lt;p id="codes"&gt;
						&lt;label for="kode"&gt;
							Embed untuk halaman forum:
						&lt;/label&gt;&lt;br /&gt;
					&lt;input type="text" id="kode" value="[IMG]'.$urlgambar.'[/IMG]" onclick="javascript:this.focus();this.select();" readonly="true" /&gt;&lt;br /&gt;
					&lt;label for="kodehtml"&gt;Embed untuk halaman website: &lt;/label&gt;&lt;br /&gt;
						&lt;input type="text" id="kodehtml" value=\'&lt;a href="'.$linkurl.'"&gt;&lt;img src="'.$urlgambar.'" alt="Image hosting by hitamcoklat" /&gt;&lt/a&gt;\' onclick="javascript:this.focus();this.select();" readonly="true" /&gt;&lt;br /&gt;
					&lt;label for="codedirect"&gt;Direct link:&lt;/label&gt;&lt;br /&gt;
            &lt;input type="text" id="codedirect" value="'.$urlgambar.'" onclick="javascript:this.focus();this.select();" readonly="true" /&gt;&lt;/p&gt;&lt;br&gt;
			Gambar:&lt;br&gt;&lt;img class="gambar" src="'.$urlgambar.'" /&gt;';

        } else
            print '&lt;p&gt;Maaf file terlalu besar.&lt;/p&gt;';

}
?&gt;
&lt;form enctype="multipart/form-data" action="&lt;?php echo $_SERVER['PHP_SELF']; ?&gt;" method="post"&gt;
  &lt;br /&gt;
  &lt;input type="hidden" name="max_file" value="&lt;?php echo $maxsize; ?&gt;" /&gt;
&lt;label for="file"&gt;Upload Gambar: &lt;/label&gt;&lt;input type="file" name="file" id="file" /&gt;
(File jangan lebih dari 1024 Kb)&lt;br /&gt;
&lt;input name="submit" type="submit" value="Upload" /&gt;
&lt;br /&gt;
&lt;/form&gt;
&lt;div class="footer"&gt;
	&copy;&lt;a href="http://www.hitamcoklat.com"&gt;Septian Dwi Anugrah&lt;/a&gt;
&lt;/div&gt;
&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;
</pre>

File diatas berfungsi sebagai halaman awal dan berguna untuk memproses gambar yang akan di hosting kan.

  * Pada baris 19 hingga 41 merupakan pengecekan terhadap method yang digunakan kepada server, jika method POST telah dilakukan maka mengeksekusi perintah-perintah dibawahnya dan jika tidak maka akan ditampilkan halaman upload file.
  * Pada baris ke 21 merupakan pengecekan terhadap file yang akan di upload, apakah melebihi batas upload atau tidak, jika melebihi maka akan ditampilkan pesan file terlalu besar dan proses dibatalkan
  * Sebenarnya skrip ini standar yang memiliki inti di fungsi move\_uploaded\_file() yang berfungsi untuk mengupload data ke server dan setelah itu menyajikannya ke dalam input type yang format nya sudah ditentukan.

## Screenshot

<div id="attachment_851" class="wp-caption aligncenter" style="width: 532px">
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/06/imagehost2.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[227]" title="imagehost2"><img class="wp-image-851" title="imagehost2" src="http://hitamcoklat.com/wp-content/uploads/2013/06/imagehost2.png" alt="imagehost2" width="522" height="331" /></a>
  
  <p class="wp-caption-text">
    Penampakan Image Hosting
  </p>
</div>

<div id="attachment_852" class="wp-caption aligncenter" style="width: 653px">
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/06/imagehost1.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[227]" title="imagehost1"><img class="wp-image-852" title="imagehost1" src="http://hitamcoklat.com/wp-content/uploads/2013/06/imagehost1.png" alt="imagehost1" width="643" height="138" /></a>
  
  <p class="wp-caption-text">
    Penampakan Upload File Foto
  </p>
</div>

## Kesimpulan:

Mungkin penggunaan image hosting ini merupakan alternatif lain dari penggunaan image hosting yang sudah ada. Seperti sistem-sistem yang sudah ada, image hosting php ini memiliki kekuarang dan kelebihan dari sudut pemakaiannya. diantara lain,

### Kelebihan:

  * Dengan memiliki image hosting sendiri anda dapat dengan leluasa mengupload file apapun ke dalam hosting anda dan memanfaatkannya kembail
  * Dengan memiliki image hosting sendiri maka untuk dapat mengakses file yang anda gunakan akan lebih cepat dibanding kan image hosting luar yang telah saya sebutkan diatas *tergantung server juga siihh hehehe

### Kekurangan:

  * Untuk dapat menggunakan image hosting PHP ini anda diharuskan memiliki hosting untuk dapat menggunakannya karena image hosting ini bersifat berdiri sendiri jadi anda dituntut untuk selalu memonitor hosting anda.
  * Jika ada yang melakukan injeksi terhadap image hosting anda maka resiko ditanggung sendiri hahha  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Semoga bermanfaat! SALAM BLOGGER!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />