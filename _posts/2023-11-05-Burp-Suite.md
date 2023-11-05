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

<i style="color:#ff4500;">• Proxy:</i> Trafiği tarayıcınızdan Burp Suite'e yönlendirilen ve Burp Proxy üzerinden geçen trafiği temsil eder. Genellikle en temel trafiği bu araç üzerinden görebilirsiniz.

<i style="color:#ff4500;">• Repeater:</i> Kullanıcıların bir isteği yeniden göndermelerini sağlar. Bu, bir isteği değiştirerek tekrar tekrar göndermek ve yanıtları gözlemlemek için kullanılır.

<i style="color:#ff4500;">• Intruder:</i> Otomatik olarak bir dizi isteği göndermek ve yanıtları analiz etmek için kullanılır. Belirli parametreleri farklı değerlerle doldurarak bir web uygulamasının nasıl tepki verdiğini görmek için kullanılır.

<i style="color: yellow;">c. URL scope: </i> Bu kısım, hangi URL'lerin pasif taramaya dahil edileceğini belirtir.

<i style="color:#ff4500;">• Everything:</i> Bu seçenek aktif edildiğinde, tüm trafiği pasif taramaya dahil eder.

<i style="color:#ff4500;">• Suite scope:</i> Yalnızca Burp Suite'in kendi ayarlarında belirtilen URL'leri pasif taramaya dahil eder.

<i style="color:#ff4500;">• Custom scope:</i> Özel olarak belirlediğiniz URL'leri pasif taramaya dahil eder. Bu, belirli bir uygulamanın veya hizmetin trafiğini hedef almak için kullanılır.

<i style="color: yellow;">d. Deduplication: </i> Bu kısım, crawl işleminin daha verimli olmasını sağlamak için tekrar eden bilgilerin nasıl ele alınacağına dair ayarlara sahiptir.

<i style="color:#ff4500;">• Ignore duplicate items based on URL and parameter names:</i> Bu seçenek aktif edildiğinde, aynı URL ve parametre isimlerine sahip tekrar eden öğeler pasif taramada göz ardı edilir. Bu, gereksiz tekrarlarla işlem yükünün artmasını önlemek için kullanılır.

Bu ayarlar, pasif taramanın verimliliğini ve hedef odaklılığını artırmak için önemlidir. Özellikle büyük web uygulamalarında veya geniş ölçekli projelerde, gereksiz tekrarları ve trafiği filtrelemek, taramanın çok daha hızlı ve etkili olmasına yardımcı olabilir.<br><br>


<h3 style="color:yellow;">2. Scan configuration</h3>

Bu kısım, özelleştirilmiş tarama yapılandırmalarını oluşturmanıza, düzenlemenize ve seçmenize olanak tanır. Bu özellik, belirli bir test senaryosu veya uygulama için özel tarama ayarları oluşturmak istediğinizde oldukça kullanışlıdır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiVQMVls7bbAg_ByfANtWvv5rNPAStSs3MgxQHM6Y3Tcvtdbk9XdXU9f5Y8MEi_VZ9GYPzn7lbZXJfcevsNvWfHin8DcTR-jthpQ-IxjYoZJiOzl9usvjVR-byvjH_ZQhsMKgNtNVH7V4JSnVsGOZ-enjGwSb8ttIXp3_BpCEVhz8T2AHB-45i9bHPfn0iV/s1196/4.png" height="400" width="600">


<i style="color: yellow;">a. New Scanning Configuration: </i> Burp Suite'te bir tarama görevi başlattığınızda, bu özelleştirilmiş yapılandırmaları kullanarak taramanın nasıl yürütüleceğini belirleyebilirsiniz. New diyerek devam edelim;

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj7WnZztb7v_kfLmX4yeyZ_ki4bLEESOwtsUznKlutEhoOOkE2kkhU6lu76udJItJjC88haHdiHxiUg77IgvijFJ0UM5Gy9sXQr-1u8hGWOoKTgQaTWPBdeR0ZKgMwiWqrONs8LeqVPeFIerM0ficIS7mAEjlq3Unb_Bdj5WuU2phO6tMMGjm2RUNZbkmaw/s893/6.png" height="400" width="600">

**This type of live task analyses HTTP messages...:** Bu cümle, canlı pasif crawl görevinin, HTTP mesajlarını analiz ederek Target site map’e girişler eklediğini belirtir. Burada amaç, HTTP trafiğini dinleyerek web uygulamasının yapısını ve içeriğini otomatik olarak keşfetmektir.


<i style="color: yellow;">a. Types of items to add: </i> Bu bölüm, site haritasına hangi öğe türlerinin eklenmesi gerektiğini belirtir.      

<i style="color:#ff4500;">• Links:</i> Web sayfalarında bulunan bağlantıları temsil eder. Bu, başka sayfalara veya kaynaklara yönlendiren URL'leri ifade eder.

<i style="color:#ff4500;">• Form submissions:</i> Web sayfalarında bulunan form gönderimlerini temsil eder. Bu, kullanıcının veri girdiği ve gönderdiği form elemanlarını ifade eder.

<i style="color: yellow;">b. URL's to add: </i> Bu bölüm, site haritasına hangi URL'lerin ekleneceğini belirtir.

<i style="color:#ff4500;">• Everything:</i> Tüm trafiği site haritasına ekler.

<i style="color:#ff4500;">• The item itself:</i> Yalnızca analiz edilen öğeyi site haritasına ekler.

<i style="color:#ff4500;">• Items on the same domain:</i> Aynı etki alanında bulunan tüm öğeleri site haritasına ekler. Bu, analiz edilen öğenin aynı etki alanında (domain) bulunan diğer URL'leri ifade eder.

<i style="color:#ff4500;">• URLs in scope:</i> Burp Suite'in kendi ayarlarında belirtilen URL'leri site haritasına ekler.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Suite scope:</i> Burp Suite'in genel ayarlarında belirlenen URL'leri ve etki alanlarını ifade eder.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Custom scope:</i> Özel olarak belirlediğiniz URL'leri ve etki alanlarını ifade eder.
<br><br>

<h3 style="color:yellow;">B. Live audit from Proxy (all traffic)</h3>

Bu özellik, Burp Suite'in en güçlü araçlarından birini, yani otomatik zafiyet tespitini temsil eder. Bu mod, Burp Proxy üzerinden geçen tüm trafiği gerçek zamanlı olarak analiz eder ve potansiyel güvenlik açıklıklarını otomatik olarak tespit etmeye çalışır.


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQsKGdaKUrrnaFoBjIVjzhtrpdeTM7Nyqaas4P52vquavyZabVLcxATI8v8pN2dzpp2noA6tqtPiV2AL4x1c4SNT28RUAFBjhbRzd5ErymiV4QykzI6tDvuD-Rz2acrPEpM6QlXUvVQDW6giOL-NSHw4UH5fxXa9Om8XY4aukHRCC4wasQ__UCRdOGLIi1/s684/7.png" height="" width="">

Bu özellik ne anlam ifade eder ?

Diyelim ki bir web uygulamasını test ediyorsunuz. Tarayıcınızdan bir sayfaya erişim sağladığınızda veya bir form gönderdiğinizde bu trafiği Burp Suite'in Proxy özelliği sayesinde dinliyorsunuz. Eğer "Live audit from Proxy" aktif ise, bu trafiği dinlerken aynı zamanda bu trafiğin içeriğini analiz edip olası güvenlik açıklıklarını tespit etmeye çalışır.

Bir online alışveriş sitesini düşünelim. Bu sitede bir ürün sepete eklendiğinde bir HTTP isteği gönderiliyor. Bu istek içerisinde "price" adında bir parametre yer alıyor ve bu parametre ürünün fiyatını belirtiyor. "Live audit from Proxy" özelliği, bu tür trafiği analiz ederken, bu "price" parametresinin manipüle edilip edilemeyeceğini, yani fiyatın değiştirilip değiştirilemeyeceğini kontrol eder. Eğer bu parametre ile oynanarak fiyat değiştirilebiliyorsa, bu bir güvenlik açığı olarak raporlanır.

Bu özellik, manuel olarak her bir işlevi test eden bir sızma testi uzmanı için zaman kazandırır. Ancak, otomatik taramaların sonuçları her zaman kesin değildir ve bu nedenle otomatik tarama sonuçlarını teyit etmek için **manuel testlerin** yapılmasını şiddetle öneriyoruz.

Şimdi sağ taraftaki ayar iconundan detaylara bakalım ;


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjsQ9s-mhKNxC3ujVxAktx4mBL-GhQIr4R-glaMtDpiLMJvE2sfZYQNIMTUUGgwVEbyWn4FK-eoQNCHps08cS_7cUcUvsaN6Ca9MbmUBA8w808vhQWbE-07y7ZOeO73YNQFV_ChSnYQhnWxVFwXPv-VY4CwRghX9jjywgVdBMTQLqsE55TPQh5zssLQy1Nx/s878/9.png" height="400" width="600">

Scan details kısmı diğeriyle aynı olduğu için o kısmı anlatmadan geçiyoruz.

<h3 style="color:yellow;">1. Scan configuration</h3>

Bu kısım, özelleştirilmiş tarama yapılandırmalarını oluşturmanıza, düzenlemenize ve seçmenize olanak tanır. Bu özellik, belirli bir test senaryosu veya uygulama için özel tarama ayarları oluşturmak istediğinizde oldukça kullanışlıdır.

Şimdi New diyerek  yeni bir ayar yapalım;

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhQSbLP_C04GLT68bnitjCFp0bBL73ENsDYVd9DYqcBUJ48ByQWzSakZJ5nAGSoxB3-oQ5yMbk4Y0jcCe8qgGoXwycocQj0Zi1D56djckyiucnvYKdvsZKBmJEMWTdmj4qjSU9Yl9IgeaJS0AHwKxzDU43qrCTq0l7xANte-TBIw90-yyH8Xg0ngMEy7S0J/s885/10.png" height="400" width="600">

Evet New diyerek ayarlarımızı açtık ilk  ayarlama yapacağımız bölüm  Audit Optimization bu bölüm nedir ne değildir inceleyelim.


<i style="color: yellow;">a. Audit Optimization: </i> Bu bölüm, denetim (audit) sürecinin nasıl çalışacağına dair bir dizi ayar içerir. Burada, hedef uygulamanın doğası ve denetimin amacına göre denetim mantığının davranışını kontrol edebilirsiniz.


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg6LXmiK1Tndcli9LLNuGQ5UzqdHgvU8SBnMuPAsfphk_mCBeG1fDQECJ4PexU8vPmORH0LCKSJ6JpB9xU_AU0GBA9BuWriE5p_fUzII5mBDaGRk6RFkMK73KwTU7ZRs3YqxA9FmloSW6PZnEPcPN8EamjofiAE0tGuXrKgnci7c5XJTap3LgmA4_-1byc-/s878/11.png" height="" width="">

<i style="color:#ff4500;">Audit Speed:</i> Bu ayar, denetimin ne kadar hızlı çalışacağını belirtir. Daha hızlı bir tarama, daha az derinlemesine ve kapsamlı olabilirken, daha yavaş bir tarama genellikle daha derinlemesine ve ayrıntılı olur.

<i style="color:#ff4500;">Audit Accuracy:</i> Bu, denetimin ne kadar hassas olacağını belirleyen bir ayardır. Daha yüksek hassasiyet, daha az yanıltıcı pozitif sonuç verir, ancak tarama süresi artabilir.

<i style="color:#ff4500;">Maximum total crawl and audit time:</i> Bu ayar, tarama ve denetim sürecinin toplamda ne kadar sürmesi gerektiğini belirler. Bu, belirli bir zaman dilimi içinde tarama yapmak istediğinizde kullanışlıdır. Bu ayar, sadece denetim işlemi için yapılan taramalarda uygulanmaz.

<i style="color:#ff4500;">Skip checks unlikely to be effective due to insertion point’s base value:</i> Bu seçenek, belirli bir ekleme noktasının temel değeri nedeniyle etkili olması muhtemel olmayan kontrolleri atlamak için kullanılır. Örneğin, sayısal bir değer beklenen bir parametrede SQL enjeksiyonu kontrolü yapmak gibi.

<i style="color:#ff4500;">Consolidate frequently occurring passive issues:</i> Bu seçenek, sıkça rastlanan pasif sorunları birleştirmek için kullanılır. Böylece, aynı türden birçok zayıflık için ayrı ayrı bildirimler almak yerine, bu zayıflıklar tek bir bildirimde konsolide edilir.

<i style="color:#ff4500;">Automatically maintain sessions:</i> Bu seçenek, tarama sırasında oturumun (session) otomatik olarak sürdürülmesini sağlar. Bu, oturum tabanlı kimlik doğrulamaları olan uygulamalarda kullanışlıdır. Audit-only taramaları için bu seçenek uygulanmaz.

<i style="color:#ff4500;">Follow redirections where necessary:</i> Bu seçenek, tarama sırasında gerekli olduğunda yönlendirmeleri (redirections) takip etmeyi sağlar. Bu, uygulamanın farklı sayfalara veya alt domainlere yönlendirme yapması durumunda önemlidir.


Bu ayarlar, tarama işleminin hedeflenen doğrulukta ve hızda gerçekleştirilmesini sağlamak için kritik öneme sahiptir. Genellikle, bir denetim sürecinin başlangıcında bu ayarları inceleyerek, denetimin amacına ve hedef uygulamanın özelliklerine uygun şekilde optimize edilmesi önerilir.


<i style="color: yellow;">b. Issues Reported:</i> Burp Suite'in tarama sırasında hangi güvenlik zafiyetlerini kontrol edeceği ile ilgili ayarları içerir. Bu ayarları özelleştirerek, denetiminizin ne kadar derinlemesine ve ne kadar geniş kapsamlı olacağını kontrol edebilirsiniz. 

Şimdi bu ayarları ayrıntılı bir şekilde inceleyelim:


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjlM6-0VMs54PXBs3CqGCfJPiCNN7AVNjYX_bwsphUOSFLnT7xRyDeSXNPmhBuiyBBoXtEXuFoEdwHEFdSjGJkMNe5xLlmxmHm6i3kxiBhkmpnhSV926rTMCQVd8LX_ypfEcs_ucuCRBCy1Fg7-0zdtSdoANiqhtldXyZQwzZdbsjr1F1jkx884D3eKnC91/s864/12.png" height="400" width="600">

<i style="color:#ff4500;">Select by scan type:</i> Bu seçenek, tarama tipine göre zafiyetleri kontrol etmek isteyip istemediğinizi belirtir. Aşağıda listelenen farklı tarama tipleri bulunmaktadır:


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Passive:</i> Bu tarama türü, trafik üzerinde değişiklik yapmadan, sadece trafiği dinleyerek (passively) zafiyetleri tespit eder. Örneğin, güvensiz içerik karışımı, cookie'lerde güvenlik bayrağının eksik olması gibi zafiyetler bu yöntemle tespit edilebilir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Light active:</i> Bu tarama, hedef uygulamaya çok hafif etkili aktif istekler gönderir. Bu, daha az tespit yöntemiyle hızlı bir tarama yapar ve genellikle uygulamaya minimum etki yapar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Medium active:</i> Bu, Light taramasından biraz daha ayrıntılıdır ve hedef uygulamaya daha fazla aktif istek gönderir. Bu, daha derinlemesine bir tarama yapar fakat daha fazla sistem kaynağı kullanabilir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• Intrusive active:</i> Bu tarama türü, potansiyel olarak hedef uygulamaya zarar verebilecek derinlemesine testler yapar. Örneğin, SQL Enjeksiyonu veya DOS atakları gibi saldırıları simüle edebilir. Bu tarama tipi kullanılırken dikkatli olunmalıdır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;• JavaScript analysis: </i> Bu tarama, web uygulamalarında sıkça bulunan JavaScript zafiyetlerini analiz etmek için kullanılır.


<i style="color:#ff4500;">Select individual issues:</i> Bu seçenek, Burp Suite'in hangi zafiyetleri kontrol edeceğini tek tek belirlemenize olanak tanır. Özellikle belli bir zafiyet türü hakkında bilgi almak istiyorsanız bu seçenek kullanılır. Ayrıca, bu seçenekte belirli bir zafiyet türü için kullanılacak tespit yöntemlerini de belirleyebilirsiniz.

Sonuç olarak, Issues Reported bölümü, denetiminizin ne kadar kapsamlı ve ne kadar derinlemesine olacağını özelleştirmenizi sağlar. Genel bir tarama yapmak için tarama tipine göre seçenekleri kullanabilir veya belirli zafiyetler üzerinde yoğunlaşmak için bireysel zafiyet seçeneklerini kullanabilirsiniz.


<i style="color: yellow;">c.	Handling Application Errors During Audit:</i> Tarama süreci sırasında karşılaşılan uygulama hatalarının nasıl ele alınacağını kontrol eden ayarlardır. Özellikle büyük web uygulamalarında yüzlerce, hatta binlerce istek yapıldığında, bazen bağlantı hataları veya zaman aşımı gibi sorunlarla karşılaşılabilir. Bu bölümde belirtilen ayarlar, bu gibi sorunlar karşısında Burp Suite'in nasıl tepki vereceğini belirlemenize yardımcı olur. 

Şimdi ayarları detaylı bir şekilde inceleyelim: 


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjk_vdrsYDr9i4exBfon9jysYlBtb0-0MPBMwuGyvqZFmpE709agrPid7PTXacY_xvw29p9uTgLevsrT3aR7ryfbhkL9jsWe_LeqryNnTjufHKXFXFqe3eeXSV_CTMGi02aCVvmgLe1SLXL0jJ-Z6R1kORpM8sWw-hTJ38YG7nmh90DUzXkN54a_Wb3quyf/s864/13.png" height="" width="">
