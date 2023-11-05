---
title: Burp Suite Genel Bakış 
description: Burp Suite Genel Bakış 
layout: Yazılar
permalink: Burp-suite
---

Bu konuya neden değinme gereği duydum. Genelde piyasaya baktığımda kısıtlı bir **Burp Suite** kullanımı mevcut olduğunu görüyorum. Türkçe kaynaklarda da genelde basit kullanımlar mevcut. Bu konu sürekli güncellenecek olup sadece **Burp Suite** anlatmakta kalmayıp çeşitli zafiyetlerin hem keşifleri hem de **Burp Suite** üzerinden istismarlarını da işleyeceğiz. En azından plan bu yönde 😊

Şimdi **Burp Suite** nedir ne değildir vs gibi konulara değinmek istemiyorum. Zaten bu işlere başlamış kişiler **Burp Suite** hakkında bilgi sahibidirler. Daha çok Burp Suite ekranlarını tanımaya,ayarlamaları yapmaya yönelik bir anlatım olmasını istiyorum...
<br><br>
<h1 style="color:yellow;">DASHBOARD EKRANI</h1>
<h3 style="color:yellow;">A. Live Passive Crawl From Proxy (all traffic)</h3>
<p>Bu kısım, Burp Proxy'den gelen tüm trafiği pasif olarak crawl için dinler. Yani, gerçek zamanlı olarak, kullanıcının tarayıcısından geçen trafiği analiz eder ve bu trafiği Burp Suite'in içeriğini keşfetme mekanizmasına yönlendirir. Bu, uygulamada kullanılan URL'leri, parametreleri ve diğer endpoint noktalarını otomatik olarak belirlemek için kullanılır.</p>
<p>Şimdi Bu kısmın ayarlarına bir göz atalım nedir ne değildir anlamaya çalışalım;</p>

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhfQq8P5bhjHt0hIPI1F1FWPyg3NHTq4hbHoHaHcHNPBKuS749K1iEIPuZN75b4mld60ZlIg4K6nStaI4lZ7sO0aykeDrSuQ0O6sawNEfJaQJtP7spJvqc5Cv25MhY6dI90PXp6kM9W0lHymiNyLxp3vXvgSEcMfigi39RdzF8yQAWwqfP6i8FoyS-Uudip/s320/2.png" height="" width="">

<h4 style="color:yellow;">1. Scan Details</h4>

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEibi4AJVmz5jZSUJkpaypt6r5l9R1dpFVLwxB-Foc7jU6s3lwt9lb-rIHU0sh7rvAFzJ2i2gWnCdWJFZ4mZisbdtGxN0cAOCHaxghcPrqUW601IwBVqiy7uetTenUqQaD37N4uxWk3QCXeT4jAcqxjjsxyYFzNdhxMknc-tVw70OK_lHQC3zieP9WBiislG/s1200/3.png" height="500" width="950">

<p>Şimdi yukarıda da gözükeceği üzere Scan details kısmını inceleyelim ;<br><br>
Bu bölüm, canlı pasif tarama görevinin genel detaylarına dair bilgileri içerir. Pasif tarama, aslında uygulamada aktif bir değişiklik yapmadan trafiği dinleyip analiz eden bir tarama türüdür.
</p>




