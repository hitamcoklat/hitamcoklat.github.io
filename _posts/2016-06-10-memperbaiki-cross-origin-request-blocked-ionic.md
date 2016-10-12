---
id: 1273
title: 'Memperbaiki Cross-Origin Request Blocked: IONIC'
date: 2016-06-10T08:07:43+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=1273
permalink: /2016/06/10/memperbaiki-cross-origin-request-blocked-ionic/
categories:
  - Mobile
tags:
  - data parsing
  - ionic
---
Terjadi permasalahan ketika proses pengambilan data dari API (dalam kasus ini API yang digunakan menggunakan PHP) dan proses pengambilan data ini menggunakan ionic

Error yang terjadi adalah **Cross-Origin Request Blocked:** padahal setelah di cek menggunakan plugin mozilla **HTTP PARSER** data-nya berhasil di dapat. Untuk penjelasan mengenai **CORS** ini silahakan lihat penjelasan mengenai **CORS** tersebut <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS" onclick="javascript:_gaq.push(['_trackEvent','outbound-article','http://developer.mozilla.org']);" title="CORS">disini</a> ya

Langkah selanjutnya silahakan buka file **API** yang telah kamu buat, lalu masukan sintaks dibawah ini

<pre class="brush: php; title: ; notranslate" title="">if (isset($_SERVER['HTTP_ORIGIN'])) {
        header("Access-Control-Allow-Origin: {$_SERVER['HTTP_ORIGIN']}");
        header('Access-Control-Allow-Credentials: true');
        header('Access-Control-Max-Age: 86400');    //cache 1 hari
    }
</pre>

Semoga Bermanfaat!  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />