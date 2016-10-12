---
id: 374
title: Menampilkan PHP Tabel dengan Plugin Datatables
date: 2012-06-28T23:12:33+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=374
permalink: /2012/06/28/menampilkan-php-tabel-dengan-datatables/
categories:
  - Lainnya
  - php
  - Tutorial
  - Uncategorized
  - Website
tags:
  - datatables
  - datatables jquery
  - jquery datatables
  - menampilkan php table dengan datatables
  - php datatables
---
Datatables adalah salah satu dari sekian banyak plugin jquery yang sangat membantu bagi kalian yang sedang membuat suatu sistem report yang ditampilkan dalam bentuk tabel. Selain itu Plugin ini sangat fleksibel untuk berinteraksi dengan tabel HTML pokoknya kaya fitur banget lah!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Beberapa fitur yang sangat membantu kalian contohnya,

  1. Paging, ya dalam plugin ini sudah disertakan modul page atau halaman yang memudahkan kamu berpindah halaman tabel tanpa harus pusing-pusing coding lagi.
  2. Fitur pencarian, fitur ini sangat berguna untuk membantu pencarian data dalam database..ya tentu saja ini sudah disertakan dalam plugin nya.
  3. Mode pengurutan, dalam plugin datatables ini sudah disertakan mode ini yang berguna untuk mengurutkan data secara Ascending dan Descending.
  4. Mode pembatasan, mode ini berguna untuk membatasi data perhalaman yang ditampilkan sepanjang tabel.
  5. MASIH BANYAK LAGIIIII&#8230;.

wow jika dipikir-pikir ketika kita menggunakan PHP dan kita ingin membuat fungsi-fungsi tersebut akan lama dan banyak waktu diperlukan hehe&#8230;

Selain itu datatables ini memiliki tampilan yang sangat ciamik dan terlihat elegan, ya karena ketika kita menggunakan plugin ini sudah termasuk dengan file CSS dan tampilan layout-nya&#8230;
  
Waaaahhh&#8230; banyak sekali keunggulannya yaaa *lebay,

Intinya sih kita dapat menghemat waktu dalam membuat sistem report jika memanfaatkan plugin ini..
   
 <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Oke langsung aja kita coba keunggulan plugin ini&#8230;

Pertama buat dahulu database yang akan kita tampilin di datatables ini,

<pre class="brush: php; title: ; notranslate" title="">CREATE TABLE IF NOT EXISTS `mahasiswa` (
  `id` int(10) NOT NULL AUTO_INCREMENT,
  `nim` int(100) DEFAULT NULL,
  `nama` varchar(45) DEFAULT NULL,
  `fakultas` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=latin1 AUTO_INCREMENT=8 ;
</pre>

Setelah itu masukan data masing-masing ini,

<pre class="brush: php; title: ; notranslate" title="">INSERT INTO `mahasiswa` (`id`, `nim`, `nama`, `fakultas`) VALUES
(1, 1006677, 'Rina', 'FIP'),
(2, 1998378, 'Dodi', 'FPBS'),
(3, 1007786, 'Irwan', 'FIP'),
(4, 1006677, 'Arif', 'FIP'),
(5, 1898790, 'Dedi', 'FPKTK'),
(6, 8347890, 'Dani', 'FPBS'),
(7, 8293489, 'Dini', 'FMIPA');
</pre>

Untuk tampilan HTML-nya saya buat simple, jadi langsung tampilan table plugin datatables ini&#8230;hehe *biar ga ribet

<pre class="brush: xml; highlight: [22,35,44,45,46]; title: ; notranslate" title="">&lt;!DOCTYPE html&gt;
&lt;html&gt;
    &lt;head&gt;
        &lt;title&gt;Datatables&lt;/title&gt;
        &lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"&gt;
        
        &lt;script src="media/js/jquery.js" type="text/javascript"&gt;&lt;/script&gt;
        &lt;script src="media/js/jquery.dataTables.js" type="text/javascript"&gt;&lt;/script&gt;
        &lt;link rel="StyleSheet" href="css/style.css" type="text/css" /&gt;
        &lt;style type="text/css"&gt;
            @import "media/css/demo_table_jui.css";
            @import "media/themes/ui-lightness/jquery-ui-1.8.4.custom.css";
        &lt;/style&gt;
        
        &lt;style&gt;
            *{
                font-family: arial;
            }
        &lt;/style&gt;
        &lt;script type="text/javascript" charset="utf-8"&gt;
            $(document).ready(function(){
                $('#datatables').dataTable({
                    "sPaginationType":"full_numbers",
                    "aaSorting":[[2, "desc"]],
                    "bJQueryUI":true
                });
            })
            
        &lt;/script&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;div class="wrap"&gt;
			&lt;div class="header"&gt;
			&lt;/div&gt;
            &lt;table id="datatables" class="display"&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;No&lt;/th&gt;
						&lt;th&gt;NIM&lt;/th&gt;
                        &lt;th&gt;Nama&lt;/th&gt;
                        &lt;th&gt;Fakultas&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                      BAGIAN UNTUK MENAMPILKAN DATA DARI DATABASE
                &lt;/tbody&gt;
            &lt;/table&gt;
		&lt;div class="footer"&gt;
			&lt;p align="center"&gt;hitamcoklat&lt;/p&gt;
		&lt;/div&gt;
        &lt;/div&gt;
    &lt;/body&gt;
&lt;/html&gt;

</pre>

Bagian yang di highlight seperti plugin jquery lainnya yang merupakan bagian yang saling terikat dimana plugin ini akan mencari table dengan **&#8220;id&#8221;** <span style="text-decoration: underline;">datatables</span> yang telah di deklarasikan pada perintah jquery di bagian **<head></head>** *coba lihar baris **&#8220;26&#8243;**

Cukup mudah bukan?
   
 <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

**Screenshot &#8211; Klik untuk melihat lebih jelas**

<div id="attachment_399" class="wp-caption aligncenter" style="width: 310px">
  <a href="http://hitamcoklat.com/wp-content/uploads/2012/06/datatables-screenshot.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[374]" title="datatables - screenshot"><img class="size-medium wp-image-399" title="datatables - screenshot" src="http://hitamcoklat.com/wp-content/uploads/2012/06/datatables-screenshot-300x92.jpg" alt="datatables - screenshot" width="300" height="92" /></a>
  
  <p class="wp-caption-text">
    datatables - screenshot
  </p>
</div>

bagian kalian yang masih penasaran bisa langsung download aja file yang sudah jadi

<div id='wpdm_file_5' class='wpdm_file wpdm-only-button'>
  <div class='cont'>
    <div class='btn_outer'>
      <div class='btn_outer_c' style='background-image: url(http://localhost/hitamcoklat/wp-content/plugins/download-manager/icon/Download file.png);'>
        <a class='btn_left  ' rel='5' title='tables' href="http://localhost/hitamcoklat/?wpdmact=process&did=NS5ob3RsaW5r"   >Download</a><span class='btn_right'>&nbsp;</span>
      </div>
    </div>
    
    <div class='clear'>
    </div>
  </div>
</div>

Semoga bermanfaat&#8230;

Salam Blogger!