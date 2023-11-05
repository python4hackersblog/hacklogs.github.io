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

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiVQMVls7bbAg_ByfANtWvv5rNPAStSs3MgxQHM6Y3Tcvtdbk9XdXU9f5Y8MEi_VZ9GYPzn7lbZXJfcevsNvWfHin8DcTR-jthpQ-IxjYoZJiOzl9usvjVR-byvjH_ZQhsMKgNtNVH7V4JSnVsGOZ-enjGwSb8ttIXp3_BpCEVhz8T2AHB-45i9bHPfn0iV/s1196/4.png" height="400" width="600">


<i style="color: yellow;">a. New Scanning Configuration: </i> Burp Suite'te bir tarama görevi başlattığınızda, bu özelleştirilmiş yapılandırmaları kullanarak taramanın nasıl yürütüleceğini belirleyebilirsiniz. New diyerek devam edelim;

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj7WnZztb7v_kfLmX4yeyZ_ki4bLEESOwtsUznKlutEhoOOkE2kkhU6lu76udJItJjC88haHdiHxiUg77IgvijFJ0UM5Gy9sXQr-1u8hGWOoKTgQaTWPBdeR0ZKgMwiWqrONs8LeqVPeFIerM0ficIS7mAEjlq3Unb_Bdj5WuU2phO6tMMGjm2RUNZbkmaw/s893/6.png" height="400" width="600">

**This type of live task analyses HTTP messages...:** Bu cümle, canlı pasif crawl görevinin, HTTP mesajlarını analiz ederek Target site map’e girişler eklediğini belirtir. Burada amaç, HTTP trafiğini dinleyerek web uygulamasının yapısını ve içeriğini otomatik olarak keşfetmektir.


<i style="color: yellow;">a. Types of items to add: </i> Bu bölüm, site haritasına hangi öğe türlerinin eklenmesi gerektiğini belirtir.

<i style="color: red;">• Links:</i> Web sayfalarında bulunan bağlantıları temsil eder. Bu, başka sayfalara veya kaynaklara yönlendiren URL'leri ifade eder.

<i style="color: red;">• Form submissions:</i> Web sayfalarında bulunan form gönderimlerini temsil eder. Bu, kullanıcının veri girdiği ve gönderdiği form elemanlarını ifade eder.

<i style="color: yellow;">b. URL's to add: </i> Bu bölüm, site haritasına hangi URL'lerin ekleneceğini belirtir.

<i style="color: red;">• Everything:</i> Tüm trafiği site haritasına ekler.

<i style="color: red;">• The item itself:</i> Yalnızca analiz edilen öğeyi site haritasına ekler.

<i style="color: red;">• Items on the same domain:</i> Aynı etki alanında bulunan tüm öğeleri site haritasına ekler. Bu, analiz edilen öğenin aynı etki alanında (domain) bulunan diğer URL'leri ifade eder.

<i style="color: red;">• URLs in scope:</i> Burp Suite'in kendi ayarlarında belirtilen URL'leri site haritasına ekler.

<i style="color: red;">&nbsp;&nbsp;&nbsp;• Suite scope:</i> Burp Suite'in genel ayarlarında belirlenen URL'leri ve etki alanlarını ifade eder.

<i style="color: red;">&nbsp;&nbsp;&nbsp;• Custom scope:</i> Özel olarak belirlediğiniz URL'leri ve etki alanlarını ifade eder.
<br><br>

<h3 style="color:yellow;">B. Live audit from Proxy (all traffic)</h3>

Bu özellik, Burp Suite'in en güçlü araçlarından birini, yani otomatik zafiyet tespitini temsil eder. Bu mod, Burp Proxy üzerinden geçen tüm trafiği gerçek zamanlı olarak analiz eder ve potansiyel güvenlik açıklıklarını otomatik olarak tespit etmeye çalışır.


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQsKGdaKUrrnaFoBjIVjzhtrpdeTM7Nyqaas4P52vquavyZabVLcxATI8v8pN2dzpp2noA6tqtPiV2AL4x1c4SNT28RUAFBjhbRzd5ErymiV4QykzI6tDvuD-Rz2acrPEpM6QlXUvVQDW6giOL-NSHw4UH5fxXa9Om8XY4aukHRCC4wasQ__UCRdOGLIi1/s684/7.png" height="400" width="600">









