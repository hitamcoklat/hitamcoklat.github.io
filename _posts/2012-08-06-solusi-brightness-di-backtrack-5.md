---
id: 452
title: Solusi Brightness di Backtrack 5
date: 2012-08-06T16:42:08+00:00
author: admin
layout: post
guid: http://hitamcoklat.com/?p=452
permalink: /2012/08/06/solusi-brightness-di-backtrack-5/
categories:
  - Lainnya
  - Tutorial
  - Uncategorized
tags:
  - brightness backtrack
  - brightness bermasalah
  - brightness linux
  - masalah brightness linux
  - Solusi Brightness di Backtrack 5
---
Backtrack 5 merupakan Distro Linux yang berfokus pada sistem penetrasi. Emang ga bisa disangkal lagi kali ya, si Backtrack ini ga tanggung-tanggung punya lebih dari 30 kalo tools yang sangat berguna sekali dalam masalah sistem kemanan baik itu web maupun jaringannya. Wow emang bener-bener keren nih distro. hohohoho&#8230;.

Ya sekitar 5 hari yang lalu saya menginstall Backtrack 5 ini. Yaaa awalnya sih sekedar untuk mencoba-coba, disisi lain ubuntu yang sebelumnya saya pakai sudah tidak bersahabat lagi apalagi tampilannya yang sekarang sudah menjadi &#8216;unity&#8217; maksudnya saya tidak suka dengan tampilan ubuntu yang sekarang. Tapi kenapa harus beralih ke Backtrack ya? padahal kan bisa aja download Desktop Environmet kaya

  * xfce
  * lxde
  * openbox
  * dan masih banyak lainnya,

Mungkin lebih tepat nya pengen ngerasain kaya apa sih program-program Pentest itu..yaa ga ada salahnya nyoba Backtrack. Oh ya sekarang ini Backtrack 5 memiliki base Ubuntu, jadi kita bisa tetep pake aplikasi yang ada di ubuntu&#8230;waaaaahhhh enak banget yaaaa, udah aplikasi keamanannya sejubel ditambah kita masih bisa install aplikasi ubuntu yang sekian banyaknya&#8230;hohohoho, langsung aja ke pembahasan yah udah makin ga jelas suasana blog ini..  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />

Setelah cari tau sana-sini dan cukup banyak melakukan kegagalan akhirnya dapet juga cara agar brightness di komputer beejalan dengan baik menggunakan Backtrack 5 ini&#8230;huuuhhh. Baiklah langsung aja ya ke prakteknya!! hehe,

Ada banyak sekali cara untuk memperbaiki fasilitas brightness pada komputer kita, berikut adalah beberapa cara yang sempat saya gunakan dan berhasil&#8230;

## Cara Pertama,

Cara pertama ini pada awalnya berhasil saya gunakan untuk memperbaiki brightness di Ubuntu saya tapi sewaktu saya beralih menggunakan Backtrack 5 ini ternyata tidak berfungsi sepenuhnya&#8230;, berikut adalah cara yang pertama saya gunakan barangkali dengan cara yang ini ada yang berhasil  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

  1. Buka terminal, silahkan buka file **grub **dengan menggunakan editor yang anda sukai, dalam kasus ini saya menggunakan **gedit **dengan mengetikan, 
    <pre>gedit /etc/default/grub</pre>

  2. Jika sudah terbuka file-nya maka akan tampil isi dari GRUB yang kita buka tadi, maka cari baris GRUB\_CMDLINE\_LINUX_DEFAULT=”quiet splash” lalu sisipkan script **acpi_osi=Linux** 
    <pre>GRUB_CMDLINE_LINUX_DEFAULT=”quiet <strong>acpi_osi=Linux</strong> splash</pre>

  3. Setelah langkah tersebut selesai, save file-nya..
  4. Terakhir silahkan melakukan update-grub dengan mengetikan, 
    <pre>update-grub</pre>

  5. Restart Komputer, (semoga semuanya berjalan dengan lancar) hehe

Bagaimana? apakah cara tersebut berhasil? ya..mungkin ada yang berhasil dan mungkin ada yang gagal seperti saya..huhuhu.., Baiklah jika cara yang tadi tidak berhasil maka jangan putus asa dulu!! coba cara yang satu ini, semoga berhasil&#8230;

## Cara kedua

Cara yang kedua ini memang cukup ribet, tapi berjalan baik di komputer saya hohoho  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_smile.gif' alt=':)' class='wp-smiley' />

  1. Install terlebih dahulu **mousepad **melalui terminal, dengan mengetikan 
    <pre>apt-get install mousepad</pre>
    
    Biasanya belum terinstall, tapi jika sudah terinstall langsung aja ke tahap selanjutnya..</li> 
    
      * Setelah masih dalam terminal, jalankan mousepad dengan mengetikan 
        <pre>mousepad ./backlight_d.sh</pre>
    
      * Kopi Paste kode berikut, 
        <pre>#!/bin/bash

old_b=9;
declare -i curr_b=240;
declare -i target_b=240;

while : ; do
b=`cat /sys/class/backlight/acpi_video0/brightness`;
delay="0.5"

if [ $old_b != $b ]; then
old_b=$b
let "target_b=$b * 20 + 12"
#printf "Target: %10d\n" $target_b
fi

hex_b=".";

if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$curr_b + 2"
if [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
elif [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$curr_b - 2"
if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
fi

if [ $hex_b != "." ] ; then
hex_b=`printf "%02X" $curr_b`
delay="0.005"
setpci -s 00:02.0 F4.B=$hex_b
fi

sleep $delay
done</pre>
    
      * Setelah itu Save,
      * Kembali ke terminal ketikan 
        <pre>cp ./backlight_d.sh /etc/ && sudo chmod +x /etc/backlight_d.sh</pre>
    
      * Masih pada layar terminal ketikan 
        <pre>mousepad /etc/rc.local</pre>
    
      * Terakhir akan muncul rc.local dengan editor mousepad, lalu ketikan kode berikut sebelum **exit 0, ** 
        <pre>nohup /etc/backlight_d.sh &</pre>
    
      * Oke selanjutnya restart komputer,</ol> 
    
    Bagaimana? berhasilkah? ya semoga berhasil yaa&#8230;  <img src='http://localhost/hitamcoklat/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' />
    
    Salam Blogger !!!
    
    *saya menggunakan Acer Aspire 4736  dengan VGA intel GMA 4500MHD