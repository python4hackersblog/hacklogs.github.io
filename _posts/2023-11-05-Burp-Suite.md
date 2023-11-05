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

<h3 style="color:yellow;">1. Scan Details</h3>

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEibi4AJVmz5jZSUJkpaypt6r5l9R1dpFVLwxB-Foc7jU6s3lwt9lb-rIHU0sh7rvAFzJ2i2gWnCdWJFZ4mZisbdtGxN0cAOCHaxghcPrqUW601IwBVqiy7uetTenUqQaD37N4uxWk3QCXeT4jAcqxjjsxyYFzNdhxMknc-tVw70OK_lHQC3zieP9WBiislG/s1200/3.png" height="400" width="600">

<p>Şimdi yukarıda da gözükeceği üzere Scan details kısmını inceleyelim ;<br><br>
Bu bölüm, canlı pasif tarama görevinin genel detaylarına dair bilgileri içerir. Pasif tarama, aslında uygulamada aktif bir değişiklik yapmadan trafiği dinleyip analiz eden bir tarama türüdür.
</p>

<i style="color: yellow;">a. Task type: </i> Bu, Burp Suite'te yürütülmekte olan görevin türünü gösterir. "Live passive crawl" seçeneği, Burp Proxy'den gelen trafiği gerçek zamanlı olarak (crawl) için dinlemek üzere ayarlanmıştır.

<i style="color: yellow;">b. Tools scope: </i> Bu kısım, hangi Burp Suite araçlarından gelen trafiğin pasif tarama görevine dahil edileceğini belirtir. Canlı görev tarafından işlenen öğeleri seçmek için trafiği denetlenecek araçları seçmemiz istenir.

<i style="color: red;">• Proxy:</i> Trafiği tarayıcınızdan Burp Suite'e yönlendirilen ve Burp Proxy üzerinden geçen trafiği temsil eder. Genellikle en temel trafiği bu araç üzerinden görebilirsiniz.

<i style="color: red;">• Repeater:</i> Kullanıcıların bir isteği yeniden göndermelerini sağlar. Bu, bir isteği değiştirerek tekrar tekrar göndermek ve yanıtları gözlemlemek için kullanılır.

<i style="color: red;">• Intruder:</i> Otomatik olarak bir dizi isteği göndermek ve yanıtları analiz etmek için kullanılır. Belirli parametreleri farklı değerlerle doldurarak bir web uygulamasının nasıl tepki verdiğini görmek için kullanılır.

<i style="color: yellow;">c. URL scope: </i> Bu kısım, hangi URL'lerin pasif taramaya dahil edileceğini belirtir.

<i style="color: red;">• Everything:</i> Bu seçenek aktif edildiğinde, tüm trafiği pasif taramaya dahil eder.

<i style="color: red;">• Suite scope:</i> Yalnızca Burp Suite'in kendi ayarlarında belirtilen URL'leri pasif taramaya dahil eder.

<i style="color: red;">• Custom scope:</i> Özel olarak belirlediğiniz URL'leri pasif taramaya dahil eder. Bu, belirli bir uygulamanın veya hizmetin trafiğini hedef almak için kullanılır.

<i style="color: yellow;">d. Deduplication: </i> Bu kısım, crawl işleminin daha verimli olmasını sağlamak için tekrar eden bilgilerin nasıl ele alınacağına dair ayarlara sahiptir.

<i style="color: red;">• Ignore duplicate items based on URL and parameter names:</i> Bu seçenek aktif edildiğinde, aynı URL ve parametre isimlerine sahip tekrar eden öğeler pasif taramada göz ardı edilir. Bu, gereksiz tekrarlarla işlem yükünün artmasını önlemek için kullanılır.

Bu ayarlar, pasif taramanın verimliliğini ve hedef odaklılığını artırmak için önemlidir. Özellikle büyük web uygulamalarında veya geniş ölçekli projelerde, gereksiz tekrarları ve trafiği filtrelemek, taramanın çok daha hızlı ve etkili olmasına yardımcı olabilir.<br><br>


<h3 style="color:yellow;">2. Scan configuration</h3>

Bu kısım, özelleştirilmiş tarama yapılandırmalarını oluşturmanıza, düzenlemenize ve seçmenize olanak tanır. Bu özellik, belirli bir test senaryosu veya uygulama için özel tarama ayarları oluşturmak istediğinizde oldukça kullanışlıdır.










