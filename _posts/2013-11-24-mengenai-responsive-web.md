---
id: 970
title: 'Membuat Responsive Web Part 1 &#8211; Hello World'
date: 2013-11-24T20:05:22+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=970
permalink: /2013/11/24/mengenai-responsive-web/
categories:
  - Design
  - Tutorial
  - Website
tags:
  - halaman responsive
  - responsive desain
  - responsive web
  - website responsive
---
Seperti yang telah kita ketahui bahwa penggunaan tablet dan beberapa perangkat mobile lainnya yang membuat penting bahwa bagaimana anda harus memperhatikan hal tersebut, oleh karena itu website anda harus siap dengan perubahan tersebut. Mungkin sekarang ini berbeda dengan zaman dulu. Masih inget jaman dimana kita mengakses halaman web dengan ponsel, ketika kita mengakses halaman tersebut maka tampilannya berantakan atau kita akan dialihkan ke halaman WAP nya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />. Betapa berantakannya halaman website itu hahaha  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

Dengan perkembangan teknologi saat ini dimana smartphone dan tablet semakin maraknya, disinilah desain website yang responsive sangat dibutuhkan. Salah satu keuntungan yang diberikan ketika kita membangun website dengan desain yang responsive adalah bahwa website kita dapat memberikan rasa yang berbeda kepada pengunjung website kita yang menggunakan beberapa perangkat yang berbeda (dalam hal ini ukuran layarnya ya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />).

## Langkah Pertama

Buatlah sebuah file index.html

<pre class="brush: xml; title: ; notranslate" title="">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
	&lt;head&gt;
		&lt;meta charset="utf-8"&gt;
		&lt;title&gt;Belajar Responsive&lt;/title&gt;

		&lt;!-- main css --&gt;
		&lt;link href="css/style.css" rel="stylesheet" type="text/css" /&gt;
		&lt;link href="css/responsive.css" rel="stylesheet" type="text/css" /&gt;
	&lt;/head&gt;

	&lt;body&gt;

		&lt;div id="pagewrap"&gt;

			&lt;header id="header"&gt;

				&lt;hgroup&gt;
					&lt;h1 id="site-logo"&gt;&lt;a href="#"&gt;Hitamcoklat&lt;/a&gt;&lt;/h1&gt;
					&lt;h2 id="site-description"&gt;Blogging&lt;/h2&gt;
				&lt;/hgroup&gt;

				&lt;nav&gt;
					&lt;ul id="main-nav" class="clearfix"&gt;
						&lt;li&gt;&lt;a href="#"&gt;Home&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Profil&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Contact&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Portfolio&lt;/a&gt;&lt;/li&gt;
					&lt;/ul&gt;
					&lt;!-- akhir main nav --&gt;
				&lt;/nav&gt;

				&lt;form id="searchform"&gt;
					&lt;input type="search" id="s" placeholder="Search" /&gt;
				&lt;/form&gt;
			&lt;/header&gt;
			&lt;!-- akhir bagian header --&gt;

			&lt;div id="content"&gt;

				&lt;article class="post clearfix"&gt;

					&lt;header&gt;
						&lt;h1 class="post-title"&gt;
							&lt;a href="#"&gt;Judul Postingan&lt;/a&gt;
						&lt;/h1&gt;
					&lt;/header&gt;
					&lt;figure class="post-image"&gt;
						&lt;img src="images/snoopy.jpg" /&gt;
					&lt;/figure&gt;

					&lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum..&lt;/p&gt;
				&lt;/article&gt;
				&lt;!-- akhir postingan --&gt;
			&lt;/div&gt;
			&lt;!-- akhir content --&gt;

			&lt;aside id="sidebar"&gt;

				&lt;section class="widget"&gt;
					&lt;h4 class="widgettitle"&gt;Sidebar&lt;/h4&gt;
					&lt;ul&gt;
						&lt;li&gt;&lt;a href="#"&gt;Wordpress&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Design&lt;/a&gt;&lt;/li&gt;
						&lt;li&gt;&lt;a href="#"&gt;Design&lt;/a&gt;&lt;/li&gt;
					&lt;/ul&gt;
				&lt;/section&gt;
				&lt;!-- akhir bagian section widget --&gt;

			&lt;/aside&gt;
			&lt;!-- akhir sidebar aside --&gt;

			&lt;footer id="footer"&gt;

				&lt;p&gt;Tutorial by, &lt;a href="#"&gt;Hitamcoklat&lt;/a&gt;&lt;/p&gt;
			&lt;/footer&gt;
			&lt;!-- akhir footer --&gt;
		&lt;/div&gt;
		&lt;!-- akhir page wrap --&gt;
	&lt;/body&gt;

&lt;/html&gt;
</pre>

Pada file diatas berisi sintaks HTML biasa yang digunakan dalam membangun sebuah halaman website. Selanjutnya kita akan membuat file CSS agar halaman tersebut terlihat enak dilihat heheh. Berikut adalah sintaks CSS nya

## Langkah 2 [CSS]

Silahkan anda ketikan sintaks CSS berikut

<pre class="brush: css; title: ; notranslate" title="">/************************************************************************************
RESET
*************************************************************************************/
html, body, address, blockquote, div, dl, form, h1, h2, h3, h4, h5, h6, ol, p, pre, table, ul,
dd, dt, li, tbody, td, tfoot, th, thead, tr, button, del, ins, map, object,
a, abbr, acronym, b, bdo, big, br, cite, code, dfn, em, i, img, kbd, q, samp, small, span,
strong, sub, sup, tt, var, legend, fieldset {
	margin: 0;
	padding: 0;
}

img, fieldset {
	border: 0;
}

/* set image max width to 100% */
img {
	max-width: 100%;
	height: auto;
	width: auto\9; /* ie8 */
}

/* set html5 elements to block */
article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section {
    display: block;
}

/* STYLE GENERAL */
body {
	background-color: #EAEAEA;
	font: .81em/150% Arial, Helvetica, sans-serif;
	color: #666;
}
a {
	color: #026acb;
	text-decoration: none;
	outline: none;
}
a:hover {
	text-decoration: underline;
}
p {
	margin: 0 0 1.2em;
	padding: 0;
}

/* AKHIR STYLE GENERAL */

/* list */
ul, ol {
	margin: 1em 0 1.4em 24px;
	padding: 0;
	line-height: 140%;
}
li {
	margin: 0 0 .5em 0;
	padding: 0;
}

/* heading */
h1, h2, h3, h4, h5, h6 {
	line-height: 1.4em;
	margin: 20px 0 .4em;
	color: #000;
}
h1 {
	font-size: 2em;
}
h2 {
	font-size: 1.6em;
}
h3 {
	font-size: 1.4em;
}
h4 {
	font-size: 1.2em;
}
h5 {
	font-size: 1.1em;
}
h6 {
	font-size: 1em;
}

/* reset webkit input search */
input[type=search] {
	-webkit-appearance: none;
	outline: none;
}
input[type="search"] :: -webkit-search-decoration,
input[type="search"] :: -webkit-search-cancel-button {
	display: none;
}

/* struktur halaman */
#pagewrap {
	width: 980px;
	margin: 0 auto;
}

/* header */
#header {
	position: relative;
	height: 160px;
}

/* site logo */
#site-logo {
	position: absolute;
	top: 10px;
}
#site-logo a {
	font: bold 30px/100% Arial, Helvetica, sans-serif;
	color: #fff;
	text-decoration: none;
}

/* site deskripsi */
#site-decription {
	font: italic 100%/130% "Times New Roman", Times, serif;
	color: #fff;
	position: absolute;
	top: 55px;
}

/* search form */
#searchform {
	position: absolute;
	right: 10px;
	bottom: 6px;
	z-index: 100;
	width: 160px;
}
#searchform #s {
	width: 140px;
	float: right;
	background: #fff;
	border: none;
	padding: 6px 10px;
	/* transition */
	-webkit-transition: width .7s;
	-moz-transition: width .7s;
	transition: width .7s;
}
/* BAGIAN NAVIGASI */
#main-nav {
	width: 100%;
	background: #ccc;
	margin: 0;
	padding: 0;
	position: absolute;
	left: 0;
	bottom: 0;
	z-index: 100;
}
#main-nav li {
	margin: 0;
	padding: 0;
	list-style: none;
	float: left;
	position: relative;
}
#main-nav li:first-child {
	margin-left: 10px;
}
#main-nav a {
	line-height: 100%;
	font-weight: bold;
	color: #000;
	display: block;
	padding: 14px 15px;
	text-decoration: none;
}
#main-nav a:hover {
	color: #fff;
	background: #474747;
}
/* BAGIAN KONTEN */
#content {
	background: #fff;
	margin: 30px 0 30px;
	padding: 20px 35px;
	width: 600px;
	float: left;
}

/* post */
.post {
	margin-bottom: 40px;
}
.post-title {
	margin: 0 0 5px;
	padding: 0;
	font: bold 26px/120% Arial, Helvetica, sans-serif;
}
.post-title a {
	text-decoration: none;
	color: #000;
}
.post-meta {
	margin: 0 0 10px;
	font-size: 90%;
}
.post-image {
	margin: 0 0 15px;
}

/* SIDEBAR */
#sidebar {
	width: 280px;
	float: right;
	margin: 30px 0 30px;
}
.widget {
	background: #fff;
	margin: 0 0 30px;
	padding: 10px 20px;
}
.widgettitle {
	margin: 0 0 5px;
	padding: 0;
}
.widget ul {
	margin: 0;
	padding: 0;
}
.widget li {
	margin: 0;
	padding: 6px 0;
	list-style: none;
	clear: both;
	border-top: solid 1px #eee;
}

/* FOOTER */
#footer {
	clear: both;
	color: #ccc;
	font-size: 85%;
}
#footer a {
	color: #fff;
}
/************************************************************************************
CLEARFIX
*************************************************************************************/
.clearfix:after { visibility: hidden; display: block; font-size: 0; content: " "; clear: both; height: 0; }
.clearfix { display: inline-block; }
.clearfix { display: block; zoom: 1; }
</pre>

Baiklah jika selesai maka silahkan coba jalankan file index.html tersebut, maka akan tampil sebuah halaman website. Setelah itu coba kamu resize window kita maka akan tampil sebagai berikut&#8230;

<a href="http://hitamcoklat.com/wp-content/uploads/2013/11/respon1.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[970]" title="respon1"><img class="alignnone size-full wp-image-974" title="respon1" src="http://hitamcoklat.com/wp-content/uploads/2013/11/respon1.jpg" alt="respon1" width="566" height="404" /></a>

Ya bisa dilihat bahwa halaman yang kita buat tadi masih belum responsive, lalu bagaimana kita membuat halaman yang responsive? Baiklah sekarang masuk ke tahap selanjutnya.. Silahkan ketikan sintaks berikut

## Langkah 3 [responsive.css]

Langkah selanjutnya adalah menambah sintaks CSS yang tadi telah kita buat dengan menambahkan fungsi responsive web kepada CSS website kita seperti dibawah ini. Buatlah file baru bernama _**responsive.css**_

<pre class="brush: css; title: ; notranslate" title="">/* UNTUK UKURAN LEBIH KECIL DARI 980 PIXEL */
@media screen and (max-width: 980px) {

	/* pagewrap */
	#pagewrap {
		width: 95%;
	}

	/* content */
	#content {
		width: 60%;
		padding: 3% 4%;
	}

	/* sidebar */
	#sidebar {
		width: 30%;
	}

	#sidebar .widget {
		padding: 8% 7%;
		margin-bottom: 10px;
	}

	/* embedded videos */
	.video embed,
	.video object,
	.video iframe {
		width: 100%;
		height: auto;
		min-height: 300px;
	}

}

/* UNTUK UKURAN LEBIH KECIL DARI 650 PIXEL */
@media screen and (max-width: 650px) {

	/* header */
	#header {
		height: auto;
	}

	/* searchform */
	#searchform {
		position: absolute;
		top: 5px;
		right: 0;
		z-index: 100;
		height: 40px;
	}

	#searchform #s {
		width: 70px;
	}
	#searchform #s:focus {
		width: 150px;
	}

	/* main nav */
	#main-nav {
		position: static;
	}

	/* site logo */
	#site-logo {
		margin: 15px 100px 5px 0;
		position: static;
	}

	/* site description */
	#site-description {
		margin: 0 0 15px;
		position: static;
	}

	/* content */
	#content {
		width: auto;
		float: none;
		margin: 20px 0;
	}

	/* sidebar */
	#sidebar {
		width: 100%;
		margin: 0;
		float: none;
	}
	#sidebar .widget {
		padding: 3% 4%;
		margin: 0 0 10px;
	}
	/* embedded videos */
	.video embed,
	.video object,
	.video iframe {
		min-height: 250px;
	}
}

/* UNTUK UKURAN KURANG DARI 480 PIXEL */
@media screen and (max-width: 480px) {

	/* disable webkit text size adjust for iPhone */
	html {
		-webkit-text-size-adjust: none;
	}

	/* main nav */
	#main-nav a {
		font-size: 90%;
		padding: 10px 8px;
	}

}
</pre>

Baiklah sekarang sudah selesai membuat halaman website dengan desain yang responsive. Jika anda sudah selesai coba jalankan file index.html tadi dengan menambahkan file CSS responsive tadi.. yap benar dengan menambahkan pada head html yang telah kita buat tadi dengan sintaks

> _**<link rel=&#8221;stylesheet&#8221; href=&#8221;responsive.css&#8221; type=&#8221;text/css&#8221; />**_

Jika kita jalankan filenya maka akan tampil seperti dibawah ini

<a href="http://hitamcoklat.com/wp-content/uploads/2013/11/respon2.jpg" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://hitamcoklat.com']);" rel="lightbox[970]" title="respon2"><img class="alignnone size-full wp-image-976" title="respon2" src="http://hitamcoklat.com/wp-content/uploads/2013/11/respon2.jpg" alt="respon2" width="501" height="289" /></a>

Bagaimana? ya.. semoga dengan tutorial yang sederhana ini dapat bermanfaat bagi yang sedang belajar web responsive ini seperti saya  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Salam Blogger!