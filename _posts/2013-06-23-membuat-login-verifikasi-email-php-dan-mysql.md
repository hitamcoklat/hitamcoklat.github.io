---
id: 835
title: Membuat Login Verifikasi Email PHP dan MySQL
date: 2013-06-23T19:14:02+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=835
permalink: /2013/06/23/membuat-login-verifikasi-email-php-dan-mysql/
categories:
  - php
  - Tutorial
tags:
  - login email
  - login verifikasi email
  - membuat login verifikasi email dengan php
---
Pernahkan anda mendaftar pada suatu website yang sebelumnya mengharuskan kita untuk mengisi form isian pada website itu..? dan setelah itu jika kita telah mengisi form tersebut sampai beres maka kita diharuskan untuk membuka email kita untuk melanjutkan pada proses pendaftaran selanjutnya. Pada email kita dapat terlihat ada inbox yang berasal dari website yang kita isikan tadi dan kita diharuskan untuk men-klik link tautan yang menuju pada website itu dan setelah itu pendaftaran berhasil dilakukan.

Sekarang pertama kita buat dahulu database dengan nama sesuai keinginan anda, disini saya membuat dengan nama **untuk_blog **dan dengan table **verifikasi_email** dan dapat dilihat pada gambar dibawah ini.

<div id="attachment_871" class="wp-caption aligncenter" style="width: 325px">
  <a href="http://hitamcoklat.com/wp-content/uploads/2013/06/table.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[835]" title="table"><img class="size-full wp-image-871" title="table" src="http://hitamcoklat.com/wp-content/uploads/2013/06/table.png" alt="table" width="315" height="169" /></a>
  
  <p class="wp-caption-text">
    table
  </p>
</div>

Langkah selanjutnya adalah membuat form untuk mengisi data member yang akan nanti mendaftar pada aplikasi ini

**index.php**

<pre class="brush: xml; title: ; notranslate" title="">&lt;/pre&gt;
&lt;div id="konten"&gt;&lt;form action="" method="POST"&gt;
&lt;fieldset&gt;&lt;legend&gt;Form Member&lt;/legend&gt;
 &lt;label&gt;username&lt;/label&gt;
 &lt;input type="text" name="username" /&gt;
 &lt;label&gt;email&lt;/label&gt;
 &lt;input type="text" name="email" /&gt;
 &lt;label&gt;password&lt;/label&gt;
 &lt;input type="password" name="password" /&gt;
 &lt;input type="submit" name="submit" value="Submit" /&gt;&lt;/fieldset&gt;
&lt;/form&gt;&lt;/div&gt;
&lt;pre&gt;

</pre>

Sekarang menambah kan css pada halaman index tadi adapun sintaks nya sebagai berikut

**style.css**

<pre class="brush: css; title: ; notranslate" title="">#konten {
	margin: 20px auto;
	width: 300px;
	font-family: Helvetica;
	font-size: 0.8em;
}
#konten form fieldset label, #konten form fieldset input  {
	width: 100%;
	float: left;
	margin-top: 5px;
}
#konten form fieldset legend {
	padding: 5px;
	background-color: #DBEAF9;
	font-weight: bold;
}
#konten form fieldset {
	background-color: #ECF4FC;
	border: 1px solid #DBEAF9;
}
#konten form fieldset input[type=submit] {
	width: 30% !important;
	margin-top: 20px;
}
</pre>

Jika sudah langkah diatas sudah selesai maka akan tampil tampilan seperti gambar dibawah ini,

<a href="http://hitamcoklat.com/wp-content/uploads/2013/06/form_member.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[835]" title="form_member"><img class="aligncenter size-full wp-image-865" title="form_member" src="http://hitamcoklat.com/wp-content/uploads/2013/06/form_member.png" alt="form_member" width="342" height="270" /></a>

Jika semuanya telah selesai maka sekarang membuat aksi pada php yang nantinya akan berguna untuk mengirimkan email verifikasi kepada member yang telah mendaftar tadi. Adapun sintaks nya sebagai berikut.

<pre class="brush: php; title: ; notranslate" title="">if(isset($_POST['submit'])) {

		define('ROOT', 'http://localhost/septian/tes/untuk_blog/v_email/');
		$koneksi=mysql_connect('localhost','root','');
		mysql_select_db('untuk_blog',$koneksi);

		$kode	= md5(uniqid(rand()));
		$password = md5($_POST['password']);

		$query = mysql_query("INSERT INTO verifikasi_email (id, username, password, email, aktif, kode) VALUES ('', '$_POST[username]', '$password', '$_POST[email]','T', '$kode' )") or die (mysql_error());

		$to 	= $_POST['email'];
		$judul 	= "Aktivasi Akun Anda";
		$dari	= "From: septian@tian.com \n";
		$dari	.= "Content-type: text/html \r\n";

		$pesan	= "Klik link berikut untuk mengaktifkan akun: &lt;br /&gt;";
		$pesan	.= "&lt;a href='".ROOT."konfirm.php?email=".$_POST['email']."&kode=$kode&username=".$_POST['username']."'&gt;".ROOT."konfirm.php?email=".$_POST['email']."&kode=$kode&lt;/a&gt;";

		$kirim	= mail($to, $judul, $pesan, $dari);

		if($kirim AND $query)
		{
			echo "&lt;p class=info&gt;Berhasil Dikirim&lt;/p&gt;";
		}
		else
		{
			echo "&lt;p class=infoGagal&gt;Gagal Dikirim&lt;/p&gt;";
		}

	}
</pre>

Nah jika file diatas disatukan maka untuk halaman **index.php** akan berisi sintaks dibawah ini

&nbsp;

<pre class="brush: php; title: ; notranslate" title="">&lt;html&gt;
	&lt;head&gt;
		&lt;link rel="stylesheet" href="style.css" type="text/css" /&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;div id="konten"&gt;
			&lt;form method="POST" action=""&gt;
			&lt;fieldset&gt;
				&lt;legend&gt;Form Member&lt;/legend&gt;
				&lt;label&gt;username&lt;/label&gt;
				&lt;input type="text" name="username" /&gt;
				&lt;label&gt;email&lt;/label&gt;
				&lt;input type="text" name="email" /&gt;
				&lt;label&gt;password&lt;/label&gt;
				&lt;input type="password" name="password" /&gt;
				&lt;input type="submit" name="submit" value="Submit" /&gt;
			&lt;/fieldset&gt;
			&lt;/form&gt;
		&lt;/div&gt;
	&lt;/body&gt;
&lt;/html&gt;
&lt;?php
	if(isset($_POST['submit'])) {

		define('ROOT', 'http://localhost/septian/tes/untuk_blog/v_email/');
		$koneksi=mysql_connect('localhost','root','');
		mysql_select_db('untuk_blog',$koneksi);

		$kode	= md5(uniqid(rand()));
		$password = md5($_POST['password']);

		$query = mysql_query("INSERT INTO verifikasi_email (id, username, password, email, aktif, kode) VALUES ('', '$_POST[username]', '$password', '$_POST[email]','T', '$kode' )") or die (mysql_error());

		$to 	= $_POST['email'];
		$judul 	= "Aktivasi Akun Anda";
		$dari	= "From: septian@tian.com \n";
		$dari	.= "Content-type: text/html \r\n";

		$pesan	= "Klik link berikut untuk mengaktifkan akun: &lt;br /&gt;";
		$pesan	.= "&lt;a href='".ROOT."konfirm.php?email=".$_POST['email']."&kode=$kode&username=".$_POST['username']."'&gt;".ROOT."konfirm.php?email=".$_POST['email']."&kode=$kode&lt;/a&gt;";

		$kirim	= mail($to, $judul, $pesan, $dari);

		if($kirim AND $query)
		{
			echo "&lt;p class=info&gt;Berhasil Dikirim&lt;/p&gt;";
		}
		else
		{
			echo "&lt;p class=infoGagal&gt;Gagal Dikirim&lt;/p&gt;";
		}

	}
?&gt;
</pre>

Maka jika sudah selesai seharusnya sudah berfungsi untuk mengirimkan email yang berisi kode verifikasi yang dapat dilihat seperti gambar dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2013/06/kirim_email.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[835]" title="kirim_email"><img class="aligncenter size-full wp-image-869" title="kirim_email" src="http://hitamcoklat.com/wp-content/uploads/2013/06/kirim_email.png" alt="kirim_email" width="581" height="273" /></a>

dapat dilihat bahwa link yang dihasilkan pada sintaks php diatas adalah berupa email dan kode. Oke pada langkah selanjutnya adalah membuat file untuk memproses link diatas untuk memberitahukan kepada sistem bahwa email yang dimasukan adalah valid dan bukan bot. Adapun sintaksnya adalah sebagai berikut&#8230;

**konfirm.php**

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$kode = $_GET['kode'];
	$username = $_GET['username'];

	$koneksi=mysql_connect('localhost','root','');
	mysql_select_db('untuk_blog',$koneksi);

	$query = mysql_query("UPDATE verifikasi_email SET aktif = 'Y' WHERE kode = '".$kode."'") or die (mysql_error());

	if($query) {
		echo "Member dengan username &lt;strong&gt;".$username."&lt;/strong&gt; telah diaktifkan";
	} else {
		echo "Gagal diaktifkan";
	}
?&gt;
</pre>

Nah pada tahap terakhir adalah uji coba terhadap sintaks diatas. Untuk menguji coba nya silahkan klik link yang dikirim pada email tadi. Jika berhasil maka akan tampil seperti pada gambar dibawah ini&#8230;

<a href="http://hitamcoklat.com/wp-content/uploads/2013/06/member_aktif.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[835]" title="member_aktif"><img class="aligncenter size-full wp-image-874" title="member_aktif" src="http://hitamcoklat.com/wp-content/uploads/2013/06/member_aktif.png" alt="member_aktif" width="418" height="103" /></a>

Bagaimana? mudah bukan untuk membuat form pendaftaran member dengan verifikasi email untuk mengecek bahwa pendaftar bukanlah bot.  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Untuk File yang sudah jadi bisa di download disini.

<div id='wpdm_file_7' class='wpdm_file wpdm-only-button'>
  <div class='cont'>
    <div class='btn_outer'>
      <div class='btn_outer_c' style='background-image: url(http://localhost/hitamcoklat/wp-content/plugins/download-manager/icon/Download_Crate.png);'>
        <a class='btn_left  ' rel='7' title='verifikasi_email' href="http://localhost/hitamcoklat/?wpdmact=process&did=Ny5ob3RsaW5r"   >Download File</a><span class='btn_right'>&nbsp;</span>
      </div>
    </div>
    
    <div class='clear'>
    </div>
  </div>
</div>