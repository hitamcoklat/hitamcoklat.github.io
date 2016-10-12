---
id: 46
title: Memasang Jquery Tabs
date: 2012-03-11T12:37:46+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=46
permalink: /2012/03/11/memasang-jquery-tabs/
image:
  - 
seo_follow:
  - 'false'
seo_noindex:
  - 'false'
categories:
  - Lainnya
  - Tutorial
  - Website
tags:
  - Jquery tabs
  - Memasang Jquery Tabs
  - tabs
---
<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/jquery-tools-tabs.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[46]" title="jquery-tools-tabs"><img class="alignnone  wp-image-52" title="jquery-tools-tabs" src="http://hitamcoklat.com/wp-content/uploads/2012/03/jquery-tools-tabs.jpg" alt="" width="510" height="180" /></a>

Pernahkan kalian sewaktu berkunjung ke sebuah blog atau website melihat satu kotak yang berisi tentang artikel dan di salah satu sisinya tedapat tombol atau bagian yang ketika kita klik bagian tersebut maka akan konten isi nya akan beralih ke konten berikutnya..?? ya mungkin itu contoh realnya.

Jquery tabs ini berfungsi untuk mengefisienkan konten-konten yang mungkin terlalu banyak kedalam satu halaman atau bagian, setelah itu merapikannya serta mengelompokan ke dalam suatu bagian atau disini disebut dengan TABS, dan setiap konten tab tersebut dapat ditampilkan dengan mengklik bagian tabs tersebut.

Baiklah tanpa panjang lebar langsung saja ke tahap pemasangannya, biar anda yang menyimpulkannya.
  
hehehe&#8230;

Oke! langkah pertama buat file html yang isinya sebagai berikut,

<pre class="brush: xml; title: ; notranslate" title="">&lt;link href="tabs.css" rel="stylesheet" type="text/css"&gt;
&lt;script src="jquery.js" type="text/javascript"&gt;
&lt;/script&gt;

&lt;script type="text/javascript"&gt;

$(document).ready(function(){
$("ul.tabs").tabs("div.panes &gt; div");
});

&lt;/script&gt;

&lt;div&gt;
   &lt;ul&gt;&lt;li&gt;&lt;a href="#"&gt;Tab 1&lt;/a&gt;&lt;/li&gt;
       &lt;li&gt;&lt;a class="" href="#"&gt;Tab 2&lt;/a&gt;&lt;/li&gt;
       &lt;li&gt;&lt;a class="" href="#"&gt;Tab 3&lt;/a&gt;&lt;/li&gt;
   &lt;/ul&gt;
&lt;div&gt;
      &lt;div style="display: block;"&gt;Isikan Konten Disini 1.&lt;/div&gt;
      &lt;div style="display: none;"&gt;Isikan Konten disini 2.&lt;/div&gt;
      &lt;div style="display: none;"&gt;Isikan konten disini 3.&lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;

</pre>

Selanjutnya buat file CSS yang isisnya sebagai berikut,

<pre class="brush: css; title: ; notranslate" title="">/* root element for tabs  */
.wrap {
 width: 600px;
 margin: 0 auto;
 }
ul.tabs {
 list-style:none;
 margin:0 !important;
 padding:0;
 border-bottom:1px solid #666;
 height:30px;
}

/* single tab */
ul.tabs li {
 float:left;
 text-indent:0;
 padding:0;
 margin:0 !important;
 list-style-image:none !important;
}

/* link inside the tab. uses a background image */
ul.tabs a {
 background: url(tb.png) no-repeat -420px 0;
 font-size:11px;
 display:block;
 height: 30px;
 line-height:30px;
 width: 134px;
 text-align:center;
 text-decoration:none;
 color:#333;
 padding:0px;
 margin:0px;
 position:relative;
 top:1px;
}

ul.tabs a:active {
 outline:none;
}

/* when mouse enters the tab move the background image */
ul.tabs a:hover {
 background-position: -420px -31px;
 color:#fff;
}

/* active tab uses a class name "current". it's highlight is also done by moving the background image. */
ul.tabs a.current, ul.tabs a.current:hover, ul.tabs li.current a {
 background-position: -420px -62px;
 cursor:default !important;
 color:#000 !important;
}

/* Different widths for tabs: use a class name: w1, w2, w3 or w2 */

/* width 1 */
ul.tabs a.s    { background-position: -553px 0; width:81px; }
ul.tabs a.s:hover  { background-position: -553px -31px; }
ul.tabs a.s.current  { background-position: -553px -62px; }

/* width 2 */
ul.tabs a.l    { background-position: -248px -0px; width:174px; }
ul.tabs a.l:hover  { background-position: -248px -31px; }
ul.tabs a.l.current  { background-position: -248px -62px; }

/* width 3 */
ul.tabs a.xl    { background-position: 0 -0px; width:248px; }
ul.tabs a.xl:hover  { background-position: 0 -31px; }
ul.tabs a.xl.current { background-position: 0 -62px; }

/* initially all panes are hidden */
div.panes div.pane {
 display:none;
}

/* tab pane styling */
div.panes div {
 display:none;
 padding:15px 10px;
 border:1px solid #999;
 border-top:0;
 height:100px;
 font-size:14px;
 background-color:#fff;
}

/* end tab styling */

body {
 font-family:"Lucida Grande","Lucida Sans Unicode","bitstream vera sans","trebuchet ms",verdana;
}

 /* get rid of those system borders being generated for A tags */
 a:active {
   outline:none;
 }
 :focus {
   -moz-outline-style:none;
 }
</pre>

Jika semuanya sudah benar maka tampilannya aka seperti gambar dibahwa ini,

<a href="http://hitamcoklat.com/wp-content/uploads/2012/03/2012-01-20-18-48-45.png" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[46]" title="tabs jquery"><img class="alignnone  wp-image-51" title="tabs jquery" src="http://hitamcoklat.com/wp-content/uploads/2012/03/2012-01-20-18-48-45.png" alt="" width="533" height="145" /></a>
  
Oke langkah terakhir untuk mendownload file yang sudah jadi silahkan 

<div id='wpdm_file_1' class='wpdm_file wpdm-only-button'>
  <div class='cont'>
    <div class='btn_outer'>
      <div class='btn_outer_c' style=''>
        <a class='btn_left  ' rel='1' title='Tab' href="http://localhost/hitamcoklat/?wpdmact=process&did=MS5ob3RsaW5r"   >Download</a><span class='btn_right'>&nbsp;</span>
      </div>
    </div>
    
    <div class='clear'>
    </div>
  </div>
</div>