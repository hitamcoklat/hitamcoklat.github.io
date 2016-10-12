---
title: Migrasi Ke Platform Jekyll
date: 2016-10-12T
author: admin
layout: post
permalink: /2016/10/12/migrasi-ke-platform-jekyll/
categories:
  - php
  - Tutorial
tags:
  - Jekyll
---
![enter image description here](http://res.cloudinary.com/hitamcoklat/image/upload/v1476279476/logo-2x_vy16hr.png)

Setelah berpikir lumayan lama, akhirnya jatuh pilihan pada platform ***Jekyll*** ini. Ya, ***jekyll*** merupakan sebuah platform blog. Secara sekilas bagi pengunjung blog ini mungkin tidak ada perbedaan dari sisi desain dan tampilan (yaa emang gak akan ada perbedaan dari sisi tampilan soalnya browser hanya menampilan HTML, CSS dan Javascript). Terus perbedaannya ada dong dengan platform ***Wordpress***, ***Blogpost*** dan lainnya?

Nah, yang jadi perbedaan ***Jekyll*** dengan platform yang lainnya adalah secara teknis ***Jekyll*** akan mengonfersikan atau meng-konvert *aduh ribet juga ya bahasanya hehe. Jadi maksudnya ***Jekyll*** ini merubah CMS atau sistem platform postingan anda ke dalam bentuk file statis. Otomatis dengan proses pembacaan file statis ini dapat lebih mempercepat proses eksekusi di server bahkan sangat cepat sekali hehe. Ini sangat cocok sekali bagi anda yang memiliki hostingan dengan memori yang sangat kecil. Apalagi kita tahu sendiri bahwa jumlah memori yang disediakan pada shared hosting sangat kecil sekali *sedikit curhat mengenai hostingan yang saya pakai :)

Alasan kedua saya menggunakan platform ***Jekyll*** ini adalah kemudahan dalam melakukan postingan. Karena ***Jekyll*** ini menggunakan ***Markdown*** sebagai format penulisannya yang nantinya akan di rubah menjadi HTML secara otomatis dan tentu saja di generate ke dalam file statis.

    Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML). Thus, “Markdown” is two things: (1) a plain text formatting syntax; and (2) a software tool, written in Perl, that converts the plain text formatting to HTML.

Selanjutnya adalah ternyata banyak sekali dukungan terhadap ***Jekyll*** ini. Sudah banyak sekali developer yang mengembangkan themes secara open-source yang super keren2 tampilannya *mungkin saya yang ketinggalan jaman haha. Bagaimana dengan teks editornya? apakah kita harus mengerti format2 ***Markdown*** itu sendiri? menurut saya bagus sih kalo kita mau belajar sedikit tentang format ***Markdown*** itu sendiri soalnya simpel banget format nya :) coba deh, atau jika agan pengen teks editor seperti ***Wordpress*** punya, silahkan *download* atau coba aplikasi ini [https://stackedit.io/editor](https://stackedit.io/editor) dijamin gampang deh pake teks editor itu ;)

Terakhir berhubung ***Jekyll*** ini di build menggunakan ***ruby*** agan harus install dulu ***ruby*** di OS agan. Silahkan langsung aja ketik sintaks dibawah ini di Terminal agan:

    $ gem install jekyll

Setelah itu lanjut membuat folder dan platform ***Jekyll*** nya dengan mengetik sintaks dibawah ini

    ~ $ gem install jekyll bundler
    ~ $ jekyll new myblog
    ~ $ cd myblog
    ~/myblog $ bundle exec jekyll serve

**Jekyll serve** merupakan proses me-live kan hasil dari kompilasi yang agan buat. Nah setelah itu buka browser agan ketik

    http://127.0.0.1:4000 atau http://localhost:4000

Secara default **Jekyll** akan menggunakan port **4000**.

Terus bagaimana bagi agan yang sudah terlanjur menggunakan ***Wordpress*** dan postingannya sudah lumayan banyak dan ingin bermigrasi ke platform **Jekyll** ini? Nanti dibahas di postingan selanjutnya aja ya gan :)

Jika ada pertanyaan atau masukan silahkan di kolom komentar.

**Salam Blogger!**