---
id: 82
title: Amarok CMS
date: 2012-03-12T16:13:35+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=82
permalink: /2012/03/12/amarok-cms/
image:
  - 
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
categories:
  - Internet
  - Website
tags:
  - amarok cms
  - CMS
  - install amarok cms
---
<p style="text-align: center;">
  <a href="http://hitamcoklat.com/wp-content/uploads/2012/03/amarok-1491-222x300.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[82]" title="amarok-cms"><img class="size-full wp-image-86 aligncenter" title="amarok-cms" src="http://hitamcoklat.com/wp-content/uploads/2012/03/amarok-1491-222x300.png" alt="" width="222" height="300" /></a>
</p>

Hari ini browsing-browsing cari sini sana buat nyari CMS yang super simple dan ringan yaa iseng-iseng aja sih walaupun sebenernya dengan CMS yang saya pake sekarang &#8220;WordPress&#8221; ini cukup simple tapi pas masuk ke bagian administrator nya cukup berat sih dengan tampilan admin nya..Mungkin agak lebay yah?   <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />hehe, yap memang cukup berat menurut saya apalagi bagi yang hanya butuh buat posting artikel doang. Tapi akhirnya saya ketemu dengan CMS yang satu ini namanya &#8220;Amarok CMS&#8221;, mungkin bagi pengguna Linux tidak asing lagi dengan kata &#8220;Amarok&#8221; sendiri..biasanya di OS linux amarok digunakan sebagai musik player.<!--more-->

**Fitur dari Amarok CMS sendiri yaitu,**

  1. WYSIWYG html editor
  2. XHTML Template System
  3. Image/File upload
  4. page SEO options
  5. Page Sidebar
  6. Custom slugs
  7. Multi-Level menu
  8. Page menu orders

Selain itu, kamu juga mungkin terkesan betapa simple halaman administrator amarokCMS ini dibanding CMS yang lainnya!!!!

Baiklah ini screenshot-nya!!! **CHECK THIS OUT!**

<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/admin-2012-01-20-15-07-01.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[82]" title="admin amarokcms"><img class="wp-image-83 aligncenter" title="admin amarokcms" src="http://hitamcoklat.com/wp-content/uploads/2012/03/admin-2012-01-20-15-07-01.png" alt="" width="596" height="223" /></a>

Oke tanpa basa-basi lagi langsung aja ke tahap install CMS super simple ini!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

  * Pertama silahkan download file-nya <a href="http://sourceforge.net/projects/amarokcms/files/latest/download" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://sourceforge.net']);" target="_blank">disini</a>
  * Setelah download extract file-nya lalu copy-kan ke C:\xampp\htdocs\amarokcms. atau jika anda pengguna WAMP silahkan copy ke  C:wamp\www\amarokcms.
  * Langkah selanjutnya, buatlah database dengan nama terserah anda. Disini saya memberi nama database-nya dengan nama &#8220;amarok&#8221;.
  * Selanjutnya, jika anda menginstall-nya di folder root (htdocs &#8211; XAMPP atau www &#8211; WAMP) maka buka file .htaccess-nya maka akan terlihat tulisan seperti dibawah ini..

`RewriteEngine On<br />
RewriteBase /<br />
RewriteCond %{REQUEST_URI} ^system.*<br />
RewriteRule ^(.*)$ /index.php/$1 [L]<br />
RewriteCond %{REQUEST_FILENAME} !-f<br />
RewriteCond %{REQUEST_FILENAME} !-d<br />
RewriteRule ^(.*)$ index.php/$1 [L]`

Ganti file .htaccess diatas dengan dibawah ini,
  
`RewriteEngine On<br />
RewriteBase /amarokcms<br />
RewriteCond %{REQUEST_URI} ^system.*<br />
RewriteRule ^(.*)$ /index.php/$1 [L]<br />
RewriteCond %{REQUEST_FILENAME} !-f<br />
RewriteCond %{REQUEST_FILENAME} !-d<br />
RewriteRule ^(.*)$ index.php/$1 [L]`

&#8211;Dalam kasus ini saya menyimpan file amarokCMS ini di C:wamp\www\amarokcms&#8211;

Selanjutnya, masuk ke bagian instalasi yaitu masuk ke URL http://127.0.0.1/amarokcms/install seperti nampak pada gambar dibawah ini, Setelah field ini terisi Klik Install Now.

<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/canvas.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[82]" title="amarokcms"><img class="size-full wp-image-84 aligncenter" title="amarokcms" src="http://hitamcoklat.com/wp-content/uploads/2012/03/canvas.png" alt="" width="456" height="458" /></a>

*Keterangan, Hostname(nama host anda &#8211; disini host name kita adalah localhost) || username (disini menuju ke username yang dipakai database) || Password(Password) || Database name (Nama database yang akan digunakan oleh amarokCMS ini)

Selanjutnya, jika berhasil akan muncul tampilan seperti ini,

<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/AmarokCMS-installation-2012-01-20-14-58-02.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[82]" title="AmarokCMS installation"><img class="size-full wp-image-85 aligncenter" title="AmarokCMS installation" src="http://hitamcoklat.com/wp-content/uploads/2012/03/AmarokCMS-installation-2012-01-20-14-58-02.png" alt="" width="418" height="323" /></a>

*Ini menandakan bahwa pemasangan amarokCMS ini sudah berhasil,

Untuk masuk halaman admin silahkan masuk ke localhost/amarokcms/admin dengan username dan password default yaitu &#8220;admin&#8221;

Bagaimana? Mudahkan? selamat mencoba!!!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />