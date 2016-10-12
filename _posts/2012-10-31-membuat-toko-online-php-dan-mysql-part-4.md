---
id: 659
title: Membuat Toko Online – PHP dan MySQL Part 4
date: 2012-10-31T23:12:55+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=659
permalink: /2012/10/31/membuat-toko-online-php-dan-mysql-part-4/
categories:
  - php
  - Tutorial
tags:
  - Membuat Toko Online PHP
---
Pada tahap ini saya akan coba menjelaskan bagaimana sistem dari sisi admin toko online ini. Pertama buatlah file-file yang akan dibutuhkan seperti terlihat dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2012/10/screenshot.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[659]" title="screenshot"><img class="aligncenter size-full wp-image-660" title="screenshot" src="http://hitamcoklat.com/wp-content/uploads/2012/10/screenshot.png" alt="screenshot" width="237" height="325" /></a>

  * Folder CSS yang berguna menyimpan segala file CSS
  * JS berguna untuk menyimpan file Javascript dan library plugin-plugin .js dan jquery yang akan dibutuhkan nanti
  * Folder Media yang yang merupakan tempat menyimpan plugin datatables yang telah dibahas di postingan sebelumnya di <a title="Menampilkan PHP Tabel dengan Plugin Datatables" href="http://hitamcoklat.com/2012/06/28/menampilkan-php-tabel-dengan-datatables/" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" target="_blank">cara menambahkan plugin datatables</a>
  * Folder Modul yang berguna untuk memisahkan bagian-bagian form yang nanti akan dibutuhkan dalam halaman adminnya
  * Folder NICEDIT yang berguna untuk menyimpan plugin text editor, dan nanti akan dapat memudahkan kita dalam menuliskan penginputan produk. Ya disini saya menggunakan plugin NICEDIT karena plugin ini sangat ringan  dan cukup powerful

Baiklah langsung saja pada pembahasan file Admin.php, silahkan buat file admin.php yang isinya

<pre class="brush: php; title: ; notranslate" title="">&lt;!--?php &lt;br ?--&gt;include "../include/lib.php";
error_reporting(0);
session_start();
if (empty($_SESSION[namauser]) AND empty($_SESSION[passuser])){
echo "&lt;/pre&gt;
&lt;center&gt;Silahkan Login terlebih dahulu
";
 echo "&lt;a href="index.php"&gt;&lt;strong&gt;LOGIN&lt;/strong&gt;&lt;/a&gt;&lt;/center&gt;
&lt;pre&gt;";
}
else{
?&gt;

:: Toko Online ::
&lt;script type="text/javascript" src="nicedit/nicEdit.js"&gt;&lt;/script&gt;&lt;script type="text/javascript" src="js/jquery.js"&gt;&lt;/script&gt;
&lt;script type="text/javascript" src="media/js/jquery.dataTables.js"&gt;&lt;/script&gt;&lt;script charset="utf-8" type="text/javascript"&gt;// &lt;![CDATA[
            $(document).ready(function(){
                $('#datatables').dataTable({
                    "sPaginationType":"full_numbers",
                    "aaSorting":[[2, "desc"]],
                    "bJQueryUI":false
                });
                $('#pengelola').dataTable({
                    "sPaginationType":"full_numbers",
                    "aaSorting":[[2, "desc"]],
                    "bJQueryUI":false
                });
            })

// ]]&gt;&lt;/script&gt;
&lt;script type="text/javascript"&gt;// &lt;![CDATA[
	bkLib.onDomLoaded(function(){
		nicEditors.allTextAreas(({buttonList : ['fontSize','bold','italic','underline','strikeThrough','subscript','superscript','html','image']})) });
// ]]&gt;&lt;/script&gt;

&lt;/pre&gt;
&lt;div class="wrap"&gt;
&lt;div class="header"&gt;
&lt;div class="LeftOne"&gt;&lt;a href="index.php"&gt;
 &lt;/a&gt;&lt;/div&gt;
&lt;div class="RightOne"&gt;
&lt;div class="cart"&gt;&lt;span class="KetCart"&gt;Administrator&lt;/span&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
 &lt;br class="clearfloat" /&gt;
&lt;div class="BigCOntent"&gt;
&lt;div class="LeftContent"&gt;
&lt;div id="navigation"&gt;
&lt;ul class="top-level"&gt;
	&lt;li&gt;&lt;a href="?mod=home"&gt;Home&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="?mod=product"&gt;Produk&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="?mod=category"&gt;Kategori&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="?mod=report"&gt;Report&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="logout.php"&gt;Logout&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;div class="RightContent"&gt;&lt;!--?php &lt;br ?--&gt; if ($_GET[mod]=='home'){
 echo "
&lt;h1 class="Judul"&gt;Selamat Datang&lt;/h1&gt;
 Anda Telah masuk ke halaman administrator silahkan gunakan menu yang tersedia <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' /> 

";
 }
 //Add Kategori
 elseif ($_GET[mod]=='category'){
 require_once "modul/mod_kategori.php";
 }
 //Add Product
 elseif ($_GET[mod]=='product'){
 require_once "modul/mod_produk.php";
 }
 //Report
 elseif ($_GET[mod]=='report'){
 require_once "modul/report.php";
 }
 ?&gt;&lt;/div&gt;
&lt;/div&gt;
 &lt;br class="clearfloat" /&gt;
&lt;div class="footer"&gt;
© &lt;!--?php echo date('Y') ?--&gt; Membuat Sistem Shopping Cart | PHP dan MySQL Developed by &lt;a href="http://www.hitamcoklat.com/"&gt;hitamcoklat&lt;/a&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;pre&gt;

&lt;!--?php } ?--&gt;
</pre>

Halaman admin ini merupakan bagian dimana semua proses yang dibutuhkan dalam penginputan dan beberapa proses lainnya dilakukan. Pada halaman admin ini saya membuat beberapa file yang semuanya saling mendukung

### Admin.php

Pada bagian baris ke 5 sampai ke 9 merupakan validasi terhadap login yang telah dilakukan sebelumnya di bagian file index.php

  * Pada baris ke 17 merupakan sintaks untuk me load plugin text editor nicedit
  * Pada baris ke 18 merupakan sintaks untuk me load framework jquery
  * Pada baris ke 19 sampai ke 44 merupakan sintaks untuk me load plugin datatables beserta konfigurasi datatables
  * Pada baris 45 sampai ke 48 merupakan sintaks konfigurasi dari plugin text editor nicedit dan selanjutnya merupakan sintaks html yang mungkin sudah normal
  * Pada baris 78 sampai ke 94 merupakan sintaks php yang berfungsi sebagai proses pengujian, jika kondisi mod sama dengan home maka akan di isi dengan statement admin yang berupa string dan begitu juga pada pengujian selanjutnya pada category, product dan report yang akan mengacu pada pembukaan file dengan menggunakan require_once.

### Mengenai nicedit

nicedit merupakan plugin text editor yang ditulis dalam bahasa javascript yang dapat memudahkan kita dalam mengelola tulisan kita yang memanfaatkan tag textarea pada HTML, untuk info lebih lanjut silahkan klik link dibawah ini

http://www.nicedit.com

### index.php

<pre class="brush: php; title: ; notranslate" title="">&lt;div id="header"&gt;
&lt;div id="content"&gt;&lt;center&gt;
&lt;form action="login.php" method="POST"&gt;
&lt;table&gt;
&lt;tbody&gt;
&lt;tr&gt;
&lt;td&gt;Username&lt;/td&gt;
&lt;td&gt;: &lt;input type="text" name="username" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;Password&lt;/td&gt;
&lt;td&gt;: &lt;input type="password" name="password" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td colspan="2"&gt;&lt;input type="submit" value="Login" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;
&lt;/form&gt;&lt;/center&gt;&lt;/div&gt;
&lt;/div&gt;
</pre>

Pada bagian file index.php berisi sintaks HTML untuk menampilkan form login yang merujuk pada file login.php

### Login.php

File login.php ini berisi sintaks php yang berfungsi untuk memeriksa username dan password dari file rujukan index.php. Dapat dilihat bahwa username dan password tersebut di simpan pada session yaitu pada baris ke 16 dan 17 setelah itu melakukan direct ke halaman admin.php yang memiliki parameter home pada baris ke 18 dan jika username dan password tidak cocok maka akan menampilkan window alert serta me direct ke halaman index.php.

### Logout.php

Pada bagian file ini berisi sintaks php yang berfungsi untuk menghapus semua session yang telah di lakukan dalam proses login ke halaman admin.php

### aksi.php

<pre class="brush: php; title: ; notranslate" title="">session_start();
error_reporting(0);
include "../include/lib.php";
 
$mod=$_GET[mod];
$act=$_GET[act];
 
// Menghapus data
if (isset($mod) AND $act=='hapus'){
  mysql_query("DELETE FROM ".$mod." WHERE id ='$_GET[id]'");
  header('location:admin.php?mod='.$mod);
}
 
//Add Category
elseif ($mod=='category' AND $act=='input'){
    $insert = mysql_query("INSERT INTO category (id,category) VALUES ('','$_POST[nama_kategori]')");
    if($insert == FALSE){
        echo "
 
Kategori gagal ditambahkan, alesannya:".(mysql_error())."
 
";
        }
    header('location:admin.php?mod='.$mod);
    }
//Category Update
elseif ($mod=='category' AND $act=='update'){
    $update = mysql_query("UPDATE category SET category = '$_POST[nama_kategori]' WHERE id = '$_POST[id]'");
    if($update ==FALSE){
        echo "
 
Update gagal dilakukan karena:".(mysql_error())."
 
";
        }
    header('location:admin.php?mod='.$mod);
    }
 
//Add Product
elseif ($mod=='product' AND $act=='input'){
$lokasi_file    = $_FILES['fgambar']['tmp_name'];
$tipe_file      = $_FILES['fgambar']['type'];
$nama_file      = $_FILES['fgambar']['name'];
 
move_uploaded_file($lokasi_file,"../foto/$nama_file");
    $insert = mysql_query("INSERT INTO product (product_name,
                                                price,
                                                image,
                                                id_category,
                                                deskripsi)
                                        VALUES ('$_POST[product_name]',
                                                '$_POST[price]',
                                                '$nama_file',
                                                '$_POST[cat]',
                                                '$_POST[deskripsi]')");
    header('location:admin.php?mod='.$mod);
}
//Product Update
elseif ($mod=='product' AND $act=='update'){
    $lokasi_file    = $_FILES['fgambar']['tmp_name'];
    $tipe_file      = $_FILES['fgambar']['type'];
    $nama_file      = $_FILES['fgambar']['name'];
 
    //If the image doesnt change
    if (empty($lokasi_file)){
        mysql_query("UPDATE product SET product_name        = '$_POST[product_name]',
                                        price       = '$_POST[price]',
                                        id_category = '$_POST[cat]',
                                        deskripsi   = '$_POST[deskripsi]'
                                    WHERE id = '$_POST[id]'");
    }
    else {
        move_uploaded_file($lokasi_file,"../foto/$nama_file");
        mysql_query("UPDATE product SET product_name= '$_POST[product_name]',
                                        price       = '$_POST[price]',
                                        image   = '$nama_file',
                                        id_category = '$_POST[cat]',
                                        deskripsi   = '$_POST[deskripsi]'
                                    WHERE id = '$_POST[id]'");
    }
    header('location:admin.php?mod='.$mod);
}
?&gt;
</pre>

Pada bagian file aksi.php ini berisi fungsi yang nanti akan di butuhkan dalam proses-proses baik itu penginputan dan hal lainnya dalam mengelola form pada bagian admin.

  * Pada baris ke 7 dan 8 merupakan proses pengambilan variable yang di dapat dari parameter mod dan act
  * Pada baris ke 12 sampai 15 merupakan sintaks php yang berguna untuk proses hapus data pada tabel melalui variable mod dan id
  * Pada baris 19 sampai 25 merupakan sintaks php yang berguna untuk proses penginputan kategori yang ke dalam tabel kategori
  * Pada baris 27 sampai 33 merupakan sintaks php yang berguna untuk melakukan proses update pada tabel kategori 
      * Pada baris 36 sampai 53 merupakan sintaks php yang berguna untuk melakukan proes menambahkan produk yang berisi teks dan gambar yang disimpan pada folder foto yang menggunakan fungsi php move\_uploaded\_file
      * Pada baris ke 55 sampai 78 merupakan sintaks php yang berguna untuk melakukan proses update produk yang memanfaatkan fungsi update pada mysql query</ul> 
    Baiklah sekarang kita akan membuat beberapa file di dalam folder modul yang berisi seperti dibawah.
    
      * mod_kategori.php → yang berisi form untuk penginputan kategori dalam halaman admin
      * mod_produk.php → yang berisi form untuk penginputan produk dalam halaman admin
      * report.php → berisi tabel untuk laporan hasil dari penjualan produk
    
    Adapun sintaks yang dimasukan nya seperti berikut
    
    ### mod_kategori.php
    
    <?php
  
    switch($_GET[act]){
	  
    //Tampil Kategori
	  
    default:
	  
    echo"<h1 class=&#8217;Judul&#8217;>List Category</h1>
		  
    <input type=button value=Tambah kategori onclick=location.href=&#8217;?mod=category&act=addkategori&#8217;>
		  
    <table class=&#8217;TableCart&#8217; id=&#8217;datatables&#8217;>
		  
    <thead><tr><th>no</th><th>nama kategori</th><th>aksi</th></tr></thead><tbody>";
	  
    $sql = mysql_query("SELECT * FROM category ORDER BY id DESC");
	  
    $no = 1;
	  
    while ($r=mysql\_fetch\_array($sql)){
		  
    echo"<tr><td>$no</td>
			  
    <td>$r[category]</td>
			  
    <td><a href=?mod=category&act=editkategori&id=$r[id]>Edit</a>
				  
    <a href=aksi.php?mod=category&act=hapus&id=$r[id]>Hapus</a>
			  
    </td>
			  
    </tr>";
		  
    $no++;
	  
    }
	  
    echo "</tbody></table>";
	  
    break;
    
    //Form Add Kategori
	  
    case "addkategori":
		  
    echo"<h2>Tambah Kategori</h2>
			  
    <form method=POST action=aksi.php?mod=category&act=input>
			  
    <table>
				  
    <tr><td>Nama Kategori</td>
					  
    <td>:<input type=text name=nama_kategori></td>
				  
    </tr>
				  
    <tr>
					  
    <td colspan=2>
						  
    <input type=submit name=submit value=Simpan>
						  
    <input type=button value=Batal onClick=self.history.back()>
					  
    </td>
				  
    </tr>
			  
    </table></form>";
	  
    break;
    
    //Form Edit Category
	  
    case"editkategori":
	  
    $edit = mysql\_query("SELECT * FROM category WHERE id=&#8217;$\_GET[id]&#8216;");
	  
    $r = mysql\_fetch\_array($edit);
    
    echo"<h2>Edit Kategori</h2>
		  
    <form method=POST action=aksi.php?mod=category&act=update>
			  
    <input type=hidden name=id value=$r[id]>
			  
    <table>
				  
    <tr><td>Nama Kategori</td>
					  
    <td>: <input type=text name=nama_kategori value=&#8217;$r[category]&#8216;></td>
				  
    </tr>
				  
    <tr><td colspan=2><input type=submit value=Update>
								    
    <input type=button value=Batal onClick=self.history.back()></td>
				  
    </tr>
			  
    </table>
		  
    </form>";
	  
    break;
  
    }
  
    ?>
    
    ### mod_produk.php
    
    <pre class="brush: php; title: ; notranslate" title="">&lt;?php
switch($_GET[act]){
	//Tampil Kategori
	default:
	echo"&lt;h2&gt;List Produk&lt;/h2&gt;
		&lt;input type=button value='Tambah Produk Baru' onClick=location.href='?mod=product&act=addproduct'&gt;
		&lt;table id='datatables' class='TableCart'&gt;
			&lt;thead&gt;&lt;tr&gt;&lt;th&gt;no&lt;/th&gt;&lt;th&gt;Nama Produk&lt;/th&gt;&lt;th&gt;Harga&lt;/th&gt;&lt;th&gt;aksi&lt;/th&gt;&lt;/tr&gt;&lt;/thead&gt;&lt;tbody&gt;";
		$sql = mysql_query("SELECT * FROM product ORDER BY id DESC");
		$no = 1;
		while ($r=mysql_fetch_array($sql)){
			echo"&lt;tr&gt;&lt;td&gt;$no&lt;/td&gt;
					&lt;td&gt;$r[product_name]&lt;/td&gt;
					&lt;td&gt;$r[price]&lt;/td&gt;
					&lt;td&gt;&lt;a href=?mod=product&act=editproduct&id=$r[id]&gt;Edit&lt;/a&gt;
						&lt;a href=aksi.php?mod=product&act=hapus&id=$r[id]&gt;Hapus&lt;/a&gt;
					&lt;/td&gt;&lt;/tr&gt;";
			$no++;
		}
		echo "&lt;/tbody&gt;&lt;/table&gt;";
		break;
	//Form Add Product
	case "addproduct":
		echo"&lt;h2&gt;Add Product&lt;/h2&gt;
			&lt;form enctype='multipart/form-data' method=POST action=aksi.php?mod=product&act=input&gt;
				&lt;table class='TableCart'&gt;
					&lt;tr&gt;&lt;td&gt;Nama Barang&lt;/td&gt;
						&lt;td&gt;&lt;input type=text name=product_name&gt;&lt;/td&gt;
					&lt;/tr&gt;
					&lt;tr&gt;&lt;td&gt;Kategori&lt;/td&gt;&lt;td&gt;&lt;select name=cat&gt;";
		$query = mysql_query("SELECT * FROM category");
			while ($t = mysql_fetch_array($query)){
				echo "&lt;option value=$t[id]&gt;$t[category]&lt;/option&gt;";
				}
			echo"&lt;/select&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=?mod=category&gt;Add Category?&lt;/a&gt;&lt;/td&gt;
				&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Harga&lt;/td&gt;&lt;td&gt;&lt;input type=text name=price&gt;&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Deskripsi&lt;/td&gt;&lt;td&gt;&lt;textarea name=deskripsi style='width: 277px; height: 67px;'&gt;&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Gambar&lt;/td&gt;&lt;td&gt;&lt;input type=file name='fgambar' size=40&gt;&lt;/td&gt;
				&lt;tr&gt;&lt;td colspan=2&gt;
						&lt;input type=submit name=submit value=Simpan&gt;
						&lt;input type=button value=Batal onClick=self.history.back()&gt;
					&lt;/td&gt;
				&lt;/tr&gt;
				&lt;/table&gt;&lt;/form&gt;";
		break;
	//Form Edit Product
	case"editproduct":
		$edit = mysql_query("SELECT * FROM product WHERE id='$_GET[id]'");
		$d = mysql_fetch_array($edit);
		echo"&lt;h2&gt;Edit Product&lt;/h2&gt;
			&lt;form method=POST enctype='multipart/form-data' action='aksi.php?mod=product&act=update'&gt;
				&lt;input type=hidden name=id value=$d[id]&gt;
				&lt;table class='TableCart'&gt;
					&lt;tr&gt;&lt;td&gt;Nama Barang&lt;/td&gt;
						&lt;td&gt;&lt;input onfocus=this.value='' type=text name='product_name' value='$d[product_name]'&gt;&lt;/td&gt;
					&lt;/tr&gt;
					&lt;tr&gt;&lt;td&gt;Kategori&lt;/td&gt;&lt;td&gt;&lt;select name=cat&gt;";
		$query = mysql_query("SELECT * FROM category");
			while ($t = mysql_fetch_array($query)){
				if($d['id_category'] == $t['id']) {
					echo "&lt;option value='$t[id]' selected&gt;$t[category]&lt;/option&gt;";
				} else {
					echo "&lt;option value=$t[id]&gt;$t[category]&lt;/option&gt;";
				}
			}
			echo"&lt;/select&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=?mod=category&gt;Add Category?&lt;/a&gt;&lt;/td&gt;
				&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Harga&lt;/td&gt;&lt;td&gt;&lt;input onfocus=this.value='' value='$d[price]' type=text name=price&gt;&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Deskripsi&lt;/td&gt;&lt;td&gt;&lt;textarea name=deskripsi style='width: 277px; height: 67px;'&gt;$d[deskripsi]&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;img width=100 src='../foto/$d[image]' /&gt;&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;Gambar&lt;/td&gt;&lt;td&gt;&lt;input type=file id=fgambar name=fgambar size=40&gt;&lt;/td&gt;
				&lt;tr&gt;&lt;td colspan=2&gt;
						&lt;input type=submit name=submit value=Simpan&gt;
						&lt;input type=button value=Batal onClick=self.history.back()&gt;
					&lt;/td&gt;
				&lt;/tr&gt;
				&lt;/table&gt;&lt;/form&gt;";
		break;
}
?&gt;
</pre>
    
    ### report
    
    <pre class="brush: php; title: ; notranslate" title="">&lt;?php
	$sid = session_id();
	$sql = mysql_query("SELECT * FROM order_product, product WHERE order_product.id_product=product.id");
	?&gt;
	&lt;h1 class="Judul"&gt;Laporan&lt;/h1&gt;
&lt;table id="datatables" class="TableCart"&gt;
	&lt;thead&gt;
	&lt;tr&gt;&lt;th&gt;No&lt;/th&gt;
		&lt;th&gt;Nama Produk&lt;/th&gt;
		&lt;th&gt;Nama Pemesan&lt;/th&gt;
		&lt;th&gt;Alamat Pemesan&lt;/th&gt;
		&lt;th&gt;Telepon&lt;/th&gt;
		&lt;th&gt;Jumlah&lt;/th&gt;
		&lt;th&gt;Status&lt;/th&gt;
	&lt;/tr&gt;
	&lt;/thead&gt;
	&lt;tbody&gt;
&lt;?php
	$no = 1;
	while ($r=mysql_fetch_array($sql)){
		echo"&lt;tr&gt;&lt;td&gt;$no&lt;/td&gt;
				&lt;td&gt;$r[product_name]&lt;/td&gt;
				&lt;td&gt;$r[name]&lt;/td&gt;
				&lt;td&gt;$r[address]&lt;/td&gt;
				&lt;td&gt;$r[phone]&lt;/td&gt;
				&lt;td&gt;$r[jumlah]&lt;/td&gt;
				&lt;td&gt;$r[status]&lt;/td&gt;
			 &lt;/tr&gt;";
	$no++;
	} ?&gt;
	&lt;/tbody&gt;&lt;/table&gt;
</pre>
    
    Baiklah untuk hasil akhir Membuat Toko Online – PHP dan MySQL Part 4 ini dapat di download
    
    <a href="http://www.hitamcoklat.com/download/?b4bd1746b85fbf4fc0178466708a06dc" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://www.hitamcoklat.com']);" class="download">Download File</a>
  
    <br clear="all" />