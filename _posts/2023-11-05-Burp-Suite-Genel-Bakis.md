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


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjk_vdrsYDr9i4exBfon9jysYlBtb0-0MPBMwuGyvqZFmpE709agrPid7PTXacY_xvw29p9uTgLevsrT3aR7ryfbhkL9jsWe_LeqryNnTjufHKXFXFqe3eeXSV_CTMGi02aCVvmgLe1SLXL0jJ-Z6R1kORpM8sWw-hTJ38YG7nmh90DUzXkN54a_Wb3quyf/s16000/13.png" height="" width="">

<i style="color:#ff4500;">If [2] consecutive audit checks fail, skip remaining checks in the current insertion point: </i>Bu ayar, belirli bir ekleme noktasında (insertion point) art arda belirtilen sayıda (örneğin 2) başarısız denetim kontrolü olması durumunda geriye kalan kontrollerin atlanmasını sağlar. Bu, hedef uygulamanın belirli bir ekleme noktasında sürekli hata vermesi durumunda, gereksiz yere daha fazla istek göndermemek için kullanılır.

<i style="color:#ff4500;">If [2] consecutive insertion points fail, skip remaining insertion points, and flag audit item as failed: </i>Bu ayar, art arda belirtilen sayıda ekleme noktasının başarısız olması durumunda, geriye kalan ekleme noktalarının atlanmasını ve denetim öğesinin başarısız olarak işaretlenmesini sağlar. Bu, bir denetim öğesinin tüm ekleme noktalarında hata alması durumunda denetimin hızla sonlandırılmasına yardımcı olur.

<i style="color:#ff4500;">Pause the task if: [15] consecutive audit items fail. </i>Bu, art arda belirtilen sayıda denetim öğesinin başarısız olması durumunda tarama görevinin duraklatılmasını sağlar. Bu, geniş çaplı bir sorunun (örneğin ağ kesintisi) olup olmadığını belirlemek için kullanılır.


<i style="color:#ff4500;">[ ] % of audit items fail.: </i>Toplam denetim öğelerinin belirtilen bir yüzdesi başarısız olduğunda tarama görevini duraklatır. Bu, genel bir başarısızlık oranını izlemek için kullanılır.

<i style="color:#ff4500;">On completion of each audit phase, do [1] follow-up passes to retry failed operations.: </i>Her denetim aşamasının tamamlanmasının ardından, başarısız operasyonları yeniden denemek için belirtilen sayıda takip denemesi yapar. Bu, geçici hatalar nedeniyle başarısız olan istekleri yeniden denemek için kullanılır.

Bu ayarlar, tarama sırasında karşılaşılabilecek hatalara karşı Burp Suite'in tepkisinin nasıl olacağını kontrol eder. Özellikle büyük ve karmaşık uygulamaları tarama sırasında, bu ayarların doğru bir şekilde yapılandırılması önemlidir.


<i style="color: yellow;">d. Insertion Point Types:</i> Bu bölüm saldırı yüklerinin (payloads) isteklerin neresine ekleneceğini belirtir. Burp Suite’in otomatik tarama işlevi, belirttiğiniz yere saldırı yüklerini ekleyerek zafiyetleri tespit etmeye çalışır. 

Şimdi bu seçenekleri detaylıca inceleyelim:

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEie7jp7L_Mw5yG5ziHCzq3rKkrwAqAalJQ3-QrN5F37z6czwEVJiU_Cfa_x_D5l8J4Fp3NpUGfqSHaxAcrfWoVrGXKKfFE_hjJHpvBo-iP6nJZGB-U1TYzqEMIya3igKVaCHmb6gQNIo61oDd31gMSkQ9-dZSgwTJljMEmG8BLP-tYXIEhkJNd-ZLUHN99R/s16000/13,5.png" height="" width="">


<i style="color:#ff4500;">URL parameter values:</i>Bu seçenek aktif olduğunda, Burp Suite, URL'de yer alan parametre değerlerini değiştirerek bu kısımlara saldırı yükleri ekler. Örneğin, example.com/page?param1=value1&param2=value2 şeklinde bir URL'de "value1" ve "value2" yerlerine saldırı yükleri eklenir.

<i style="color:#ff4500;">Body parameter values:</i>HTTP isteğinin gövdesinde (body) yer alan parametre değerleri üzerinde saldırı yükleri eklemek için bu seçeneği kullanabilirsiniz. Özellikle POST metodunda gönderilen verilere yük eklemek için kullanılır.

<i style="color:#ff4500;">Cookie parameter values:</i>Bu seçenekle, HTTP isteklerinde gönderilen çerez (cookie) değerlerine saldırı yükleri eklenir.

<i style="color:#ff4500;">Parameter name: </i>Normalde saldırı yükleri parametre değerlerine eklenir. Ancak bu seçenek sayesinde parametre isimlerine de saldırı yükleri eklenir.

<i style="color:#ff4500;">HTTP headers:</i>Bu seçenek aktif olduğunda, Burp Suite, HTTP başlıklarına (headers) saldırı yükleri ekler. Örneğin, User-Agent veya Referer başlıklarında değişiklikler yaparak bu başlıkların değerlerini değiştirebilir.

<i style="color:#ff4500;">Entire body (for relevant content types):</i>Bu seçenekle, HTTP isteğinin tüm gövdesine, uygun içerik türleri için saldırı yükleri eklenir.

<i style="color:#ff4500;">URL path filename:</i>URL'de yer alan dosya isimlerine saldırı yükleri eklemek için bu seçeneği kullanabilirsiniz. Örneğin, example.com/files/document.pdf şeklinde bir URL'de "document.pdf" ismine saldırı yükleri eklenir.

<i style="color:#ff4500;">URL path folders:</i>URL'de belirtilen klasör yollarına saldırı yükleri eklemek için bu seçenek kullanılır. Örneğin, example.com/folder1/folder2/page.html şeklinde bir URL'de "folder1" ve "folder2" klasör yollarına yükler eklenir.


Her bir ekleme noktası (insertion point), belirli bir güvenlik zafiyetini tespit etmek için önemli olabilir. Ancak, tüm ekleme noktalarını kullanmak, taramanın süresini uzatabilir ve hedef uygulamaya gereksiz yere yük bindirebilir. Bu nedenle, hedef uygulamanın yapısını ve tarama hedeflerinizi göz önünde bulundurarak hangi ekleme noktalarını kullanacağınıza karar vermelisiniz.


<i style="color: yellow;">e. Modifying Parameter Locations:</i> Bu bölüm belirli bir istekteki parametrelerin konumlarını değiştirmek için kullanılır. Bu, bazı filtreleri aşmak için kullanılabilir, çünkü birçok uygulama sadece belirli yerlere gelen parametreleri doğrulama veya filtreleme eğilimindedir. Parametrelerin yerlerini değiştirerek, bu tür doğrulamaları veya filtrelemeleri atlatmak mümkün olabilir. Ancak bu, çok daha fazla tarama isteği gönderilmesi anlamına gelir ve tarama süresini uzatabilir. Şimdi bu seçenekleri detaylıca inceleyelim:

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjtkt1T53psHMGVRwzkuLkxIJuEi-z7WJ2MsuNFNnzR2RB183uqaZSFockffAmySEWiaGS6Pm7HOR8k4qRIKb8LekN_KTovNrZO0shOQhse8Pvrp9K5KuTOj2AUSEq7bYVUrJEru1HFcEe3k3tT4O-JJVL3wLb0U-voktp826ovkF950knPEyDjepy-OBUF/s16000/14.png" >

<i style="color:#ff4500;">URL to body: </i>Bu seçenek, URL'deki parametreleri isteğin gövdesine (body) taşır. Örneğin, bir GET isteği **example.com/page?param=value** şeklinde ise bu, POST isteği şeklinde **example.com/page** URL'ine ve gövdesine param=value olarak değiştirilir.

<i style="color:#ff4500;">URL to cookie: </i>URL'deki parametreleri bir çerez (cookie) olarak taşır. Bu, **example.com/page?param=value** URL'sini **example.com/page** şeklinde ve bir çerez olarak param=value şeklinde değiştirir.

<i style="color:#ff4500;">Body to URL: </i>Bu seçenek, isteğin gövdesindeki (body) parametreleri URL'ye taşır.

<i style="color:#ff4500;">Body to cookie: </i>İsteğin gövdesindeki parametreleri bir çerez (cookie) olarak taşır.

<i style="color:#ff4500;">Cookie to URL: </i>Çerezlerdeki parametreleri URL'ye taşır.

<i style="color:#ff4500;">Cookie to body: </i>Çerezlerdeki parametreleri isteğin gövdesine (body) taşır.

Bu özellik, belirli güvenlik mekanizmalarını veya filtreleri aşmak istendiğinde kullanışlıdır. Örneğin, bir web uygulamasının sadece URL'deki parametreleri filtrelediğini ve gövdedeki veya çerezdeki parametreleri filtrelemediğini fark ederseniz, bu seçeneklerle bu tür filtreleri atlayabilirsiniz. Ancak unutulmamalıdır ki bu, taramanın genel süresini ve karmaşıklığını artırabilir. Bu nedenle, bu seçeneklerin ne zaman ve neden kullanılacağına dair stratejik bir yaklaşım benimsemek önemlidir.



<i style="color: yellow;">f. Ignored Insertion Points:</i> Bu bölüm tarama sırasında belirli enjeksiyon testlerinin atlanması için tasarlanmıştır. Bu, belirli parametrelerin ya da değerlerin zaten güvenli olduğunu bilerek veya tarama süresini kısaltarak bazı kontrol noktalarını (insertion points) atlamak istediğinizde kullanışlıdır. Ayrıca, hedef uygulamanın yanıt vermediği veya tarama nedeniyle hata verdiği belirli parametreler üzerinde testler yapmak istemeyebilirsiniz. Bu bölümün amacı, bu tür durumları ele alarak taramayı daha verimli ve hedefe özgü hale getirmektir.


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi7y7MRvtO_IOEtl8-qnZm2OjDYIxb1kp8XZ6uPDN177MPyrC5_tqeIb7S7rsTxwBqn4gbtFuBBbctNIx7Gqs3CwBnYtOt3gXP3sFmyWHmCMcgYn2oCuP63QwmQpg1dMFPx-6J-Ut0w1CQBDPrHlOWf9iviXSbMtAY0B_HADL9oy16qCqwquE7xPvroFM8K/s16000/16.png" height="" width="">


<i style="color:#ff4500;">Skip server-side injection tests for these parameters:</i>Bu bölüm, sunucu tarafı enjeksiyon testlerinin belirli parametreler için atlanmasını sağlar. Bu, belirli parametrelerin ya da değerlerin zaten güvenli olduğunu bilerek ya da potansiyel olarak yanıltıcı pozitif sonuçlardan kaçınmak için bazı kontrolleri (insertion points) atlamak istediğinizde kullanışlıdır. Örneğin, bir CSRF belirteci ya da oturum tanımlayıcısı gibi dinamik değerlere sahip parametreler üzerinde sunucu tarafı enjeksiyon testleri yapmanın gereksiz ya da yanıltıcı olabileceğini düşünebilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Enable: </i> Bu sütun, belirli bir parametrenin ya da değerin testten atlanıp atlanmayacağını belirtir. Örneğin, belli bir parametrenin geçici olarak test edilmemesini istiyorsanız, bu seçeneği kaldırabilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Parameter: </i> Atlamak istediğiniz parametrenin adı.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Item: </i> Parametrenin hangi bölümünde olduğunu belirtir (örn. URL, Body, Header).

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Match Type: </i> Parametrenin nasıl eşleştirileceğini belirtir (örn. tam eşleşme, regex).

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Expression: </i> Eşleştirme için kullanılacak değer ya da ifade.


<i style="color:#ff4500;">Skip all tests for these parameters:</i>Bu bölüm, belirli parametreler için tüm testlerin atlanmasını sağlar. Bu, belirli bir parametrenin ya da değerin tamamen güvenli olduğunu bildiğinizde veya tarama sırasında dikkate almak istemediğinizde kullanışlıdır.



<i style="color: yellow;">g.	Frequently Occurring Insertion Points:</i> Bu bölüm, Burp Suite'in tarama sırasında aynı ekleme noktasının büyük sayıda istekte gözlemlendiğinde daha verimli bir hızlı tarama gerçekleştirmesini sağlar. Bu, özellikle büyük uygulamalarda, belirli ekleme noktalarının yüksek frekansta tekrarlandığı durumlarda kullanışlıdır. Bu özelliğin amacı, tekrarlayan ve sonuçta değişiklik olmayan ekleme noktaları için tarama sürecini hızlandırmaktır.



<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgidZ1TYo8Doh_4IC28Of0DDAcD756KiH2WHU3MAX9RCAeK55OmlOSqZdD_tCyEsAA5cr07io6BSf5i_LksZg5WWGnl7He_XDpskk5nSHqaPNqe0erihxAylyEzRikUGmKXeMry4Yl93xxl7_6hlmb_idKPSobFH-91hUYFnwQ1pevinKoFBtUVZl8DJVb8/s16000/17.png" height="" width="">


Bu seçeneklerin aktivasyonu, hangi ekleme noktalarının hızlı taramaya tabi tutulacağını belirler. Eğer bir ekleme noktası bu listede işaretlenmemişse, standart tarama süreci uygulanacaktır. Bu özellik, özellikle büyük projelerde tarama süresini önemli ölçüde azaltabilir.



<i style="color: yellow;">h.	Misc Insertion Point Options:</i> Bu bölüm, Burp Suite'in tarama sırasında nasıl ekleme noktaları oluşturduğunu kontrol etmenizi sağlar. Bu seçenekler, özellikle karmaşık ve iç içe geçmiş veri yapılarıyla çalışırken taramanın nasıl davranacağını ayarlar.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg7ctzAhN_OjNfZsJP33XOA6Nd_0nt91fcMShq_BVIZaE0MKNbfchOS9tmQ72-A4xK367JbOdy85Jtf9Odx0KbKCbQs18BsS6PvnXCsWlh1hmzRJVYjXuyNk-m7wzxrvEJ2WUzwCLRUeZZP0NEkaj9lJbMJCA_ZrV14U0zpuUKD0YTbOAB_qKxmAJTTAFKS/s16000/18.png" height="" width="">

<i style="color:#ff4500;">Use nested insertion points (İç içe geçmiş ekleme noktalarını kullan):</i>Bu seçenek, iç içe geçmiş (nested) veri yapılarında ekleme noktaları oluşturulup oluşturulmayacağını kontrol eder. Örneğin, bir uygulama iç içe geçmiş JSON yapısını kabul ediyorsa, bu seçenek aktif edildiğinde, Burp iç içe geçmiş her bir değer için ekleme noktası oluşturacaktır.

**{
    "user": {
        "id": 123,
        "details": {
            "name": "kamil",
            "address": "123 asdfg"
        }
    }
}**

Eğer bu seçenek aktif edilirse, "id", "name" ve "address" gibi iç içe geçmiş alanlar için ekleme noktaları oluşturulacaktır.


<i style="color:#ff4500;">Maximum insertion points per base request (Temel istek başına maksimum ekleme noktası):</i>Bu seçenek, her bir temel istek için oluşturulacak maksimum ekleme noktası sayısını belirtir. Genellikle, bir istekte çok sayıda parametre veya potansiyel ekleme noktası olduğunda, tarama süresini azaltmak ve taramanın daha yönetilebilir olmasını sağlamak için bu limiti belirlemek yararlı olabilir. Örneğin, 30 olarak belirlenirse, Burp her bir temel istek için en fazla 30 ekleme noktası oluşturacaktır.

<i style="color: yellow;">i.	JavaScript Analysis:</i> Bu bölüm, Burp Scanner'ın JavaScript analizi davranışını kontrol etmenizi sağlar. Aşağıda, bu bölümde bulunan ayarlar ve seçenekler detaylı bir şekilde açıklanmıştır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgx6z2T1m4YgiOXT1BXKQ9DKVLyAuB3gUCUhVvA3ApXQljCt6cxBfXkAGykq2m5-QNhulQG0LfjM4d5-dyLtbI1-v83mjn1jOqzG0mUW63GBY_VdpYfqWDk1PUhSH5uO-TkVPGaUF3HbLrCmH4t-S4h4Z6RCwH0z33oOrmF1twaWL_cp6QsE3oVsTbLiYYB/s16000/19.png" height="" width="">

<i style="color:#ff4500;">Make requests for missing site resources:</i> Bu seçenek, web sitesinin eksik kaynakları için otomatik istekte bulunulup bulunulmayacağını belirler. Bu, daha önce taranmamış olan veya keşfedilmemiş olan kaynakların tespiti için önemlidir. Örneğin ; Eğer bir web sayfası başka bir JS dosyasını çağırıyorsa ancak bu dosya daha önce taranmamışsa, bu seçenek sayesinde Burp Scanner eksik olan bu JS dosyasını otomatik olarak isteyip analiz edebilir.

<i style="color:#ff4500;">Fetch previously undiscovered resources and data from out-of-scope hosts:</i> Bu seçenek, daha önce keşfedilmemiş kaynak ve verilerin, belirlenen kapsamın dışındaki sunuculardan alınıp alınmayacağını belirler. Örneğin; Bir web sayfası, harici bir CDN'den (İçerik Dağıtım Ağı) bazı dosyaları çağırıyorsa, bu seçenek aktif olduğunda Burp Scanner bu dosyaları otomatik olarak çekip analiz edebilir.

<i style="color:#ff4500;">Use dynamic analysis techniques & Use static analysis techniques:</i> Bu seçenekler, Burp Scanner'ın JavaScript kodunu dinamik ve statik olarak nasıl analiz edeceğini belirler. Dinamik analiz, kodun gerçekte nasıl çalıştığına dair gerçek zamanlı bir analiz sağlarken; statik analiz, kodun çalıştırılmadan yapılandırmasını ve içeriğini analiz eder. Örneğin; Bir JavaScript fonksiyonu, kullanıcının girdiği verilere göre farklı çıktılar üretiyorsa, dinamik analiz bu çıktıları gerçek zamanlı olarak değerlendirirken, statik analiz sadece fonksiyonun nasıl yazıldığına bakar.

<i style="color:#ff4500;">Maximum dynamic/static analysis time peri tem (in seconds):</i> Bu değerler, her bir öğe için harcanacak maksimum analiz süresini saniye cinsinden belirtir. Bu, taramanın ne kadar süre alacağını ve kaynak kullanımını kontrol altında tutmaya yardımcı olur. Örneğin; Eğer bu değer 30 saniye olarak ayarlandıysa, Burp Scanner her bir JavaScript kodu veya fonksiyonu için en fazla 30 saniye analiz yapar.

Bu ayarlar, Burp Scanner'ın JavaScript kodları üzerindeki analizini daha etkili ve optimize edilmiş bir şekilde yapmasını sağlar.


<i style="color: yellow;">j.	Audit Project Option Overrides:</i> Bu bölüm, denetim görevi için belirlenen ayarların, genel Proje Seçeneklerinde tanımlanan ayarların üzerine yazılmasına izin verir. Eğer bir ayar boş bırakılırsa, bu ayar otomatik olarak Proje Seçeneklerinde tanımlanan değeri alır. Örneğin; Diyelim ki Proje Seçeneklerinde bir timeout değeri 10 saniye olarak belirlendi, ancak bu denetim görevi için bu değeri 20 saniye olarak belirtmek istiyorsunuz. "Audit Project Option Overrides" bölümünden bu değeri 20 saniye olarak ayarlayabilirsiniz ve bu ayar sadece bu denetim görevi için geçerli olacaktır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHIfUBJtk1T3aSMdY5Fz493Chpp3SvZsH8lHjMSU3PM-jwPk7stinFick9J26LlLjmHMXVQV3wKBQP-68BaenDKrVVcHei2rEhqkBhVtxXGDcceNqsiTzLZ6m_3N30jz-sKzOgclkA3JEQGpjCAYZqMgv0O_V33EmrdzLboSOFMU2_LivGZIC3_COaTrOz/s16000/20.png" height="" width="">

<i style="color:#ff4500;">Maximum dynamic/static analysis time peri tem (in seconds):</i> Bu ayarlar, çeşitli ağ görevleri için kullanılacak zaman aşımı sürelerini belirtir. Değerler saniye cinsindendir. Bir görevin asla zaman aşımına uğramaması için ilgili seçeneği sıfıra ayarlayabilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Connect: </i> Bu değer, bir sunucuya bağlantı kurma işlemi sırasında ne kadar süre beklenmesi gerektiğini belirtir. Eğer belirtilen süre içerisinde bağlantı kurulamazsa, bağlantı zaman aşımına uğrar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Normal: </i> : Bu değer, normal ağ istekleri için beklenmesi gereken maksimum süreyi belirtir. Örneğin, bir web sayfasını yüklemek veya bir API isteğini tamamlamak için ne kadar süre beklenmesi gerektiği bu değer ile belirlenir.


Örnek; Connect değeri 5 saniye olarak ayarlandıysa, Burp Suite sunucuya bağlantı kurmaya çalışırken 5 saniye bekler. Eğer bu süre zarfında bağlantı kurulamazsa, bağlantı zaman aşımına uğrar ve istek başarısız olur.

Bu bölüm, Burp Suite kullanıcısına, belirli bir denetim görevi için farklı ayarlar kullanma esnekliği sağlar. Bu sayede, farklı hedefler ve farklı denetim görevleri için optimize edilmiş ayarlar kullanılabilir.



<h3 style="color:yellow;">3. Resource Pool</h3>
Bu bölüm genellikle birden fazla tarama görevi yürütürken sistem kaynaklarını yönetmek için kullanılır. Eğer sistemde birden fazla tarama veya görev yürütülüyorsa, belirli bir görevin diğerleri üzerinde çok fazla kaynak kullanmamasını sağlamak için bu özellik kullanılır. Aşağıda, bu bölümdeki seçeneklerin ne anlama geldiği ve nasıl yapılandırılması gerektiği ile ilgili ayrıntılı bir açıklama bulabilirsiniz.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjdhR-brQW1Ql_Hu2XYFU4p4A3BTmQcDKxaKHrDEttrMhO-jnLlYNDkMyUgeieafWe-38jpdTGCWGnA_xfQ9C4InW47qmqrlUYmC0Lkhsd6bja-yeSxnz_zxNvJn66yfXZ6iIALvN8SpoR_yP228oAvpI34cH-9Zkp3SYm2bKPi8zIAgJncosXbctYWvUq-/s16000/21.png" height="" width="">


<i style="color:#ff4500;">Use existing resource pool:</i> Eğer daha önce oluşturulmuş bir kaynak havuzu varsa, bu seçeneği işaretleyerek o kaynak havuzunu kullanabilirsiniz.

<i style="color:#ff4500;">Selected:</i> Bu sütun, hangi kaynak havuzunun seçildiğini belirtir.

<i style="color:#ff4500;">Resources pool:</i> Bu sütun, oluşturulan kaynak havuzlarının isimlerini gösterir.

<i style="color:#ff4500;">Concurrent requests:</i> Bu, aynı anda kaç isteğin gönderilebileceğini belirtir. Örneğin, eğer bu değer 5 olarak ayarlanırsa, tarama sırasında aynı anda en fazla 5 istek gönderilir. Bu değeri, hedef sunucunun kapasitesine göre ayarlamalısınız. Eğer hedef sunucu çok sayıda isteği kaldırabilecek kapasitede değilse, bu değeri düşük tutmalısınız.

<i style="color:#ff4500;">Request delay:</i> Bu, istekler arasındaki gecikme süresini belirtir. Örneğin, eğer bu değer 100 milisaniye ayarlanırsa, her istekten sonra 100 milisaniye beklenir.

<i style="color:#ff4500;">Random delay:</i> Bu, istekler arasındaki gecikme süresine ek olarak rastgele bir gecikme süresi ekler. Bu, taramanın daha "insan benzeri" olmasını sağlar ve potansiyel olarak bazı WAF veya IDS sistemlerini atlatmada yardımcı olabilir.

<i style="color:#ff4500;">Delay increment:</i> Eğer tarama sırasında hedef sunucudan hatalar alınırsa, bu değer kadar gecikme süresi arttırılır. Bu, hedef sunucunun aşırı yüklenmesini önlemeye yardımcı olabilir.
<br><br><br>


<h1 style="color:yellow;">TARGET EKRANI</h1>

Bu bölüm Target ekranı, web uygulamalarını ve hizmetlerini test ederken kritik bir araçtır. Bu ekran, bir web sitesinin yapısını analiz etmek, belirli istekleri incelemek ve potansiyel güvenlik zafiyetlerini keşfetmek için kullanılır. Aşağıda bahsedilen bölümler, Target ekranının ana bileşenleridir.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbHxNy5doVqUBR078ho9m4u5rrMdyfEunpKqaIoGbWFRbcqv4eDltx22TRMOcG6RPxijYYTmG6YBinG72ZsEbfZmp1bJmYWJUAFAtumwyq7N3Vf4k57OLosMwU2NgB_qPooLaFkFRpb44EcOre5gvH06d7B6oFkmReR4fjAFlL3AMKOx6ZxoIT94TBq9EZ/s16000/22.png" height="" width="1000">

<h3 style="color:yellow;">1. Site Map</h3>
•	Site map, tarama sırasında keşfedilen tüm URL'leri hiyerarşik bir yapıda gösterir.
•	Buradan, belirli URL'lere, dizinlere veya dosyalara hızlıca göz atabilir ve onları detaylı bir şekilde inceleyebilirsiniz.

Örnek: Bir haber portalını taradığınızı düşünün. Site Map'te /news, /authors, /categories gibi endpoint'leri göreceksiniz. /news altında /news/sports veya /news/technology gibi alt kategorilere ayrılmış URL'leri de inceleyebilirsiniz.

•	Uzman bir kullanıcı, bu haritayı kullanarak hangi endpoint'lerin daha riskli olabileceğini veya hangi endpoint'lerin daha ilgi çekici olduğunu hızla belirleyebilir.


<i style="color:#ff4500;">Contents:</i> Bu sütun, oluşturulan kaynak havuzlarının isimlerini gösterir. İsteklerin metotları (GET, POST vs.), durum kodları, uzunlukları ve zaman damgaları gibi bilgileri de görebilirsiniz.
Örnek: “/login” endpoint'ini ele alalım. Contents kısmında bu endpoint'e yapılan POST veya GET isteklerini, hangi parametrelerin kullanıldığını ve bu isteklerin ne zaman yapıldığını görebilirsiniz..

<i style="color:#ff4500;">Issues:</i> Burp Suite'in otomatik taraması sırasında keşfedilen potansiyel güvenlik zafiyetlerini listeler. Her bir zafiyetin ayrıntılarına, seviyesine (örn. kritik, yüksek, orta, düşük) ve tespit edildiği URL'lere ulaşabilirsiniz.Örnek: XSS, SQL Enjeksiyonu veya CSRF gibi yaygın web zafiyetleri bu bölümde listelenebilir. Sızma testibug falan filan takılanlar için bu kısım, zafiyetlerin önceliklendirilmesi ve doğrulanması için başlangıç noktasıdır.

<i style="color:#ff4500;">Request:</i> Seçilen bir isteğin ayrıntılarına göz atmanızı sağlar.Burada HTTP başlıkları, parametreler, kullanılan metot ve isteğin gövdesi gibi detayları görebilirsiniz.

<i style="color:#ff4500;">Response:</i> Seçilen isteğin sunucudan aldığı yanıtın ayrıntılarını gösterir. HTTP durum kodu, başlıklar ve yanıtın içeriği gibi bilgileri içerir.
Örnek: “/products” endpoint'ine yapılan bir istekte, sunucunun döndürdüğü ürün listesi, HTTP durum kodları (örn. 200 OK, 404 Not Found) ve yanıttaki başlıklar bu bölümde analiz edilebilir.

<i style="color:#ff4500;">Inspector:</i> Hem istekleri hem de yanıtları derinlemesine analiz etmek için kullanılır.

<i style="color:#ff4500;">Advisory:</i> Bu bölüm, belirlenen güvenlik zafiyetleri için detaylı bilgi ve öneriler sağlar. Nasıl bir saldırı yapılabilir, bu zafiyetin potansiyel etkileri nelerdir ve bu zafiyeti nasıl düzeltebileceğiniz gibi bilgilere ulaşabilirsiniz.

Sonuç olarak, Target ekranı, Burp Suite içerisinde belki de en kritik analiz ve tespit işlemlerinin yapıldığı yerdir. Uygulama güvenliği uzmanları bu ekranı kullan arak, hedeflenen web uygulamasının veya web sitesinin derinlemesine analizini gerçekleştirirler.
Target ekranı, bir uygulamanın genel yapısını anlamak için harika bir araçtır. Uygulama içerisindeki tüm URL'leri, parametreleri, sunucu yanıtlarını ve olası zafiyetleri görebilmek, bir güvenlik uzmanı için altın değerindedir. Bu, hem manuel testler için bir başlangıç noktası sağlar hem de otomatik taramaların doğru ve verimli bir şekilde gerçekleştirilmesine yardımcı olur.

**Site map’in altındaki filtreleme seçeneklerine göz atalım;**

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiExvMNbGVXj62GpijAbtJ6bTBQYbxQGt7XViL8UdxlQU9i10tdK4XJ91LJb1KHmuIvlzkT3jqiLGyB6c4fcHgzF-juktBpyM-Wp5qncLXqbVLFVHkOK63loRy6ylszVp3QvEvwRN37ujTMhflcTXQJ3k0YfdHaUcuVjQloACUVjhOLmOYDWYTL7fFvf8HO/s16000/23.png" height="" width="">

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEijTYTzjbsCmTWBKCanqJpwosbG9WbwumrOZNPYRJKeDApSVvr7vHRCONDzZ8Y8FDXEMJiHTok65xTW-FEyDB7cNQPG_O0TV39ix_DLb-pBvJD5Qrzg6ELvUhNKph-FWOy_9V2OWnvmiIFH6n_jv5C49YiU91xDZ3J0ejlCSwLI4sdqMZ4c6pW01b6FMQi9/s16000/24.png" height="" width="">


<i style="color:#ff4500;">**Filter by Request Type:**</i>Bu kısım, görmek istediğiniz istek türlerini belirlemenizi sağlar. Hangi türdeki isteklerin sitemap'te görüntüleneceğini seçebilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Show only in-scope items: </i> Bu, sadece belirlenen hedef kapsamındaki öğeleri gösterir. Özellikle büyük uygulamalarla çalışırken, sadece belirli bir bölüm veya alt alan adı üzerinde çalışıyorsanız bu oldukça değerlidir. Bu özellik, gözden kaçan potansiyel açıkları tespit etmeye yardımcı olabilir. 

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Show only requested items:</i> Burp Suite kullanıcı tarafından manuel olarak yapılan istekleri gösterir. Bu, manuel olarak tetiklenen belirli istekler üzerinde çalışmak istediğinizde kullanışlıdır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Show only parameterized requests:</i> Sadece parametre içeren istekleri gösterir. Özellikle potansiyel olarak enjeksiyon, XSS veya CSRF zafiyetlerini araştırıyorsanız bu seçenek hayati önem taşır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Hide not-found items:</i> 404 gibi "bulunamadı" yanıtlarını gizler, böylece yanıltıcı veya gereksiz bilgilere odaklanmazsınız.


<i style="color:#ff4500;">**Filter by MIME Type:**</i> Web uygulamalarının cevap olarak döndürdüğü içerik tiplerini temsil eden MIME türlerini filtreler.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	HTML,Script,Other text vs:</i> Örneğin, cross-site scripting (XSS) gibi belirli zafiyetleri araştırıyorsanız, 'Script' veya 'HTML' türlerine odaklanmak isteyebilirsiniz.


<i style="color:#ff4500;">**Filter by Status Code:**</i> HTTP protokolüne göre belirli yanıt kodlarına göre filtreleme yapabilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	2xx [success]:</i> Başarılı istekleri gösterir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	3xx [success]:</i> Yönlendirme yanıtlarını gösterir, potansiyel olarak tehlikeli yönlendirmeleri veya açık yönlendirmeleri tespit etmek için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	4xx [success]:</i> Kötü istekler, yani genellikle istemci hatası sonucu oluşan yanıtlar.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	5xx [success]:</i> Sunucu hatalarını gösterir, potansiyel olarak sunucuda bir sorun olup olmadığını kontrol etmek için kullanılır.


<i style="color:#ff4500;">**Folders**</i>

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Hide empty folders:</i> İçerisinde öğe bulunmayan klasörleri gizler, böylece daha derli toplu bir görünüm elde edersiniz.


<i style="color:#ff4500;">**Filter by search term** :</i> Belirli kelimeler veya regex ifadeleriyle istek ve yanıtlarda arama yapmanızı sağlar.

<i style="color:#ff4500;">**Filter by File Extension** :</i> Belirli dosya uzantılarına sahip istekleri gösterme veya gizleme imkanı tanır. Örneğin; sadece sunucu tarafı kodunun çalıştığı ".php, .asp, .jsp" gibi uzantıları görmek veya potansiyel olarak ilgisiz ".jpg, .png" gibi kaynakları gizlemek için bu seçenekleri kullanabilirsiniz.


<i style="color:#ff4500;">**Filter by Annotation** :</i> Belirli dosya uzantılarına sahip istekleri gösterme veya gizleme imkanı tanır. Örneğin; sadece sunucu tarafı kodunun çalıştığı ".php, .asp, .jsp" gibi uzantıları görmek veya potansiyel olarak ilgisiz ".jpg, .png" gibi kaynakları gizlemek için bu seçenekleri kullanabilirsiniz.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Show only commented items:</i> Özellikle uzun süreli testlerde, daha önce yorum eklediğiniz veya not aldığınız öğeler üzerinde çalışmak için kullanışlıdır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Show only highlighted items:</i> Dikkat çekmek istediğiniz veya daha sonra incelemek üzere işaretlediğiniz öğeleri görüntüler.


<h3 style="color:yellow;">2. Scope Settings</h3>


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj9RHRsME5T2si1TIEIMtNnh6I78a3fbDTqWNUgxtOQo2KCxlI3nkSZWE5gp6N4zuBOsMNI1gJdJRPlF32wGRSLIaQ5-J2VDbzDmaNbTK42pC4GlcAUxF7yXaOAGAAUy5PWBHr6enXpnXj7fxRV9q-bdQDEV5fS4TsmL956WUr9YqH5KiHN5Bbb3zTxDAuE/s16000/25.png" height="" width="">

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg5UepXfC4cVQH2AjtiyGSaP6TeTcwdw46w0IVxMfI9bpYyvDDvH5s_xOUWe3aHvDG4nST7lqL4aoIEUheO22nn4R_broaXPusgrFH6mfIILCINIPhAiXUqs9AWLHFzJ5vwQ3vwYlnqnFA2AOR65KszFLjXW7TtKZMj4rJB3Wea_-pPjJcXR0HyXNvNde0c/s16000/26.png" height="" width="">

Bu bölüm, Burp Suite içinde çalışırken hangi hedeflerin aktif olarak dikkate alınacağını tanımlamak için kullanılır. Bu ayarlar, Burp Suite'in içerisindeki birçok aracın davranışını etkiler. Şimdi bu bölümü detaylı bir şekilde inceleyelim.

<i style="color:#ff4500;">Use Advanced Scope Control:</i> Etkinleştirildiğinde, kapsamı detaylı bir şekilde ayarlamanızı sağlar. Özellikle geniş uygulamalarda, belirli endpoint'leri veya servisleri izole ederek tarama yapmanız gerektiğinde bu özellik oldukça kullanışlıdır.

<i style="color:#ff4500;">Include in Scope:</i> Örneğin, hedefiniz example.com ise fakat sadece example.com/admin bölümünü tarayıp, diğer kısımları pas geçmek isterseniz, bu alana https://example.com/admin/* şeklinde bir prefix eklersiniz.

<i style="color:#ff4500;">Exclude from Scope:</i> Hassas bölümleri ya da belirli endpoint'leri taramanın dışında tutmak için kullanılır. Örneğin; example.com/payment bölümünün taranmasını istemiyorsanız, bu alana ekleyerek dışarıda bırakabilirsiniz.


<i style="color:#ff4500;">Out-of-Scope Request Handling </i> 

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Drop All Out-of-Scope Requests:</i> Kapsam dışı tüm istekleri otomatik olarak durdurur. Bu, yanlışlıkla kapsam dışı bir bölgeye istek gönderilmesini engeller. Özellikle canlı sistemlerde, hedef dışı bir servise zarar vermekten kaçınmak için bu seçenek oldukça kritiktir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Use Suite Scope:</i> Genel suite kapsamını kullanır. Bu, global ayarlarınıza dayanarak kapsam dışı isteklerin nasıl ele alınacağını belirtir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Use Custom Scope:</i> Spesifik bir tarama için özel kapsam tanımlar. Bu, belirli bir görev için global kapsam ayarlarınızdan farklı bir kapsamda çalışmanıza olanak sağlar.
<br><br><br>

<h1 style="color:yellow;">PROXY EKRANI</h1>

Burp Suite'in Proxy modülü, bir güvenlik uzmanının oyun alanıdır. Intercept özelliği sayesinde uygulama ve sunucu arasında geçen trafik anında yakalanabilir, incelenebilir ve hatta modifiye edilebilir. Bu, potansiyel güvenlik açıklarını keşfetme ve hedef uygulamanın tepkilerini test etme yeteneği kazandırır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhcDcBOow9TPfaAecwg9TzAwqovH2OtiEc5kaDa9dHVaWb_w3GR8psHmHCnuuTv49nVa-UCC71y79KWe2XbU9WqXz3N-gpTydgXa1liFAOiA_ymyXU6Udsf55Np4SWnfrC2SGOIHWppJa3m9aDkqFjpjGsTarw5CrqvGN6HLpBceeQHexQDdkIFLNabBnuk/s16000/27.png" height="" width="1000">

<i style="color:#ff4500;">Intercept: </i> HTTP(S) trafiğini gerçek zamanlı olarak ele geçirme yeteneği, bir pentester için altın değerindedir. Man-in-the-Middle (MitM) saldırı senaryolarını simüle ederken, istekleri ve yanıtları değiştirerek hedef uygulamanın nasıl tepki verdiğini gözlemlemek kritiktir.

<i style="color:#ff4500;">HTTP History & WebSockets History: </i> Bu kayıtlar, yapılan tüm hareketleri incelemek için idealdir. Özellikle WebSockets, modern web uygulamalarının dinamik içerik aktarma yöntemidir. Bu protokol üzerindeki potansiyel açıklıklar, kritik bilgilere erişim kazandırabilir.

<i style="color:#ff4500;">Forward (ileri):</i> Bu buton, Intercept modunda yakaladığınız bir isteği veya yanıtı orijinal hedefine doğru ilerletmenizi sağlar. Özellikle bir istek üzerinde değişiklik yaptıktan sonra bu değişikliği uygulamaya veya sunucuya göndermek istediğinizde bu butonu kullanırsınız.

<i style="color:#ff4500;">Drop (Bırak): </i> Yakalanan bir isteği veya yanıtı hedefine ulaşmadan iptal etmek istediğinizde bu butonu kullanırsınız. Bu, belirli bir isteği veya yanıtı test etmek istemediğinizde veya bir süreci durdurmak istediğinizde kullanışlıdır.

<i style="color:#ff4500;">Intercept Off (Yakalamayı Kapat): </i> Bu seçenek, Intercept modunun aktif olup olmadığını kontrol eder. Intercept aktifken, istekler ve yanıtlar gerçek zamanlı olarak yakalanır. Eğer trafiği sürekli olarak gözlemlemek istemiyorsanız bu özelliği kapatabilirsiniz.

<i style="color:#ff4500;">Intercept On (Yakalamayı Aç): </i> Bu özellik, Burp Suite'in Proxy modülünde trafiği gerçek zamanlı olarak yakalamasını sağlar. Aktif olduğunda, tarayıcınız ve hedef web sunucusu arasında gerçekleşen tüm HTTP ve HTTPS trafiği yakalanır. Yakalama süreci, analiz, modifikasyon ve trafiği değiştirme gibi birçok aktivite için oldukça kullanışlıdır.

<i style="color:#ff4500;">Action (Eylem): </i> "Action" menüsü, yakalanan istek veya yanıt üzerinde çeşitli eylemleri gerçekleştirmenize olanak tanır. Bu eylemler arasında, isteği farklı bir araçla (örn. Repeater, Intruder) gönderme, isteği kaydetme veya analiz için bir not eklemek gibi seçenekler bulunur.

<i style="color:#ff4500;">Open Browser (Tarayıcıyı Aç): </i> Bu özellik, yakalanan bir isteği doğrudan Burp Suite içerisinde bulunan yerleşik tarayıcıyla açmanıza imkan tanır. Bu sayede, bir isteğin sonucunu doğrudan görsel olarak kontrol edebilir ve belirli bir web sayfasının nasıl göründüğünü analiz edebilirsiniz.


Buradaki önemli noktalardan biri olan **Proxy Settings** kısmına değinelim ;

<i style="color:#ff4500;">**Proxy Settings**</i> 

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgoXMqR_dVlFSFOrp82JLvwcX1Wveo-_6LglYGDszHDRqalWVT5jbSZyuNX1xG61J0S4mZ1M3sX7zLPAj8_PhwWIov6AYALB_tNfN_4jjo_H5siJdO7dstjjwjHPn5R5s96vzWj71x9JuXxY_5L5qpyOUWmGhqpeVVakY6j7hJRSLMt0ajnjzCKnuu1Wwml/s16000/28.png" height="" width="">

<i style="color:#ff4500;">Proxy Listeners:</i>  Burp Suite'in Proxy modülünün merkezi bileşenlerinden biri "Proxy Listeners"dir. Bu, Burp Suite'in yerel ağ trafiğini dinlemek için kullandığı arayüzdür.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEirJKgovTowFXSPyWRENkdg0Td_CxlSvcBK9iTZNvQJqfbnhkZr3MMAiCJJTzu-jFz9ojA2mU2YGILONNrIO9ReyNjzkBAHyhY1ybd2m8aB5Olvr4XkYcKra6iNmavA5s6KiEEJdpUQ87F2qmpPmg5MjYDIOaz38-H8stsr0SAf6Lev3CMV_JynFVBtSxcq/s16000/29.png" height="" width="">

**"Burp Proxy uses listeners to receive incoming HTTP requests from your browser. You will need to configure your browser to use one of the listeners as its proxy server."**
Bu ifade, Burp Proxy'nin tarayıcınızdan gelen HTTP isteklerini dinlemek için "listeners" (dinleyiciler) kullandığını belirtir. Etkili bir şekilde çalışması için tarayıcınızın, Burp'in dinlediği bir port ve adres üzerinden trafiği yönlendirmesi gerekmektedir.

<i style="color:#ff4500;">Running:</i>  Bu sütun, belirli bir dinleyicinin şu anda çalışıp çalışmadığını gösterir.

<i style="color:#ff4500;">Interface:</i>  Bu, dinleyicinin hangi ağ arayüzünde (genellikle bir IP adresi ve port kombinasyonu) çalıştığını gösterir. Örneğin, "127.0.0.1:8080" genellikle varsayılan yerel adres ve porttur.

<i style="color:#ff4500;">Invisible:</i>  Bu mod, dinleyiciyi "şeffaf proxy" olarak çalıştırmanızı sağlar. Bu, hedef cihazın aslında bir proxy üzerinden bağlandığının farkında olmadığı anlamına gelir.

<i style="color:#ff4500;">Redirect:</i>  Bu, gelen isteklerin başka bir sunucuya yönlendirilip yönlendirilmeyeceğini kontrol eder.

<i style="color:#ff4500;">Certificate:</i>  Burp Proxy'nin, SSL/TLS üzerinden güvenli bağlantılar için hangi sertifikayı kullandığını gösterir.

<i style="color:#ff4500;">TLS Protocols:</i>  Hangi TLS protokollerinin desteklendiğini belirtir. Bu, belirli bir web uygulamasının sadece belirli TLS sürümleriyle çalışması durumunda yararlıdır.

<i style="color:#ff4500;">Support HTTP/3:</i>  Bu, dinleyicinin HTTP/3 protokolünü destekleyip desteklemediğini belirtir. HTTP/3, web performansını artırmak için tasarlanmış yeni bir protokoldür ve bazı modern web uygulamaları ve tarayıcılar tarafından desteklenmektedir.

Bu tablo, Burp Suite içindeki farklı dinleyicilerin konfigürasyonlarını ve durumlarını hızla gözden geçirmenizi sağlar. Ayrıca, spesifik bir web uygulaması veya hedef için özelleştirilmiş dinleme yapılandırmaları oluşturmanıza olanak tanır.
<br><br>

<i style="color:#ff4500;">Request interception rules:</i>  Burp Suite, ağ trafiğini dinlerken hangi isteklerin "Intercept" sekmesinde durdurulup görüntüleneceğini ve düzenleneceğini kontrol etmenize olanak tanır. Bu özellik, belirli koşullara uyan istekleri ve yanıtları otomatik olarak yakalamak ve düzenlemek istediğinizde kullanılır. Özellikle, belirli bir hedefe veya belirli bir tür isteğe odaklanmak istediğinizde bu kurallar oldukça yararlıdır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg8T22F77bouKHNVGt9cQqEFe6p_M7YLQpUDkZPFVdeCbz9EvErjK0ZbZp-MU-rASgQlgvUhPL7cYJhjSdOGqSeUhuyh_OpUftkFrhNbRw7pJE5lQ9CqP8M7jbyKIFXZ8LT93CAFRsms-DMqfbPgn2jlL-sWuL_-NproZZ7ufmUmXV834uzSa2riXwo-a0a/s16000/30.png" height="" width="">

**"Use these settings to control which requests are stalled for viewing and editing in the Intercept tab."**
Bu ifade, "Request Interception Rules" bölümündeki ayarların, hangi isteklerin "Intercept" sekmesinde durdurulacağını kontrol etmek için kullanıldığını belirtir.

**"Intercept requests based on the following rules: Master interception is turned off"**
Bu seçenek, belirli kurallara göre isteklerin yakalanıp yakalanmayacağını belirtir. "Master interception" kapalıyken, Burp tüm istekleri otomatik olarak yakalar. Ancak bu özellik etkinleştirildiğinde, sadece belirli kurallara uyan istekler yakalanır.

**"Automatically fix missing or superfluous new lines at end of request "**
Bu özellik, bir isteğin sonunda eksik veya fazladan bulunan yeni satır karakterlerini otomatik olarak düzenler. HTTP istekleri ve yanıtları, başlangıç satırı, başlık alanları ve boş bir satırı takiben isteğin gövdesi olmak üzere belirli bir yapıya sahiptir. Boş bir satır (yani iki ardışık yeni satır karakteri), başlıkların sonunu ve gövdenin başlangıcını belirtir. Bu nedenle, doğru yapıya sahip olmayan istekler hedef sunucu tarafından yanlış yorumlanabilir. Bu özellik, bu tür yapısal hataları otomatik olarak düzelterek, manuel olarak istekleri düzenlerken yapılan hataların potansiyel etkilerini azaltır.

**"Automatically update Content-Length header when the request is edited "**
"Content-Length" başlığı, bir HTTP isteğinin veya yanıtının gövdesindeki bayt cinsinden uzunluğunu belirtir. Eğer bir isteğin içeriğini manuel olarak değiştirirseniz, bu başlığın değeri artık doğru olmayabilir. Bu başlığın yanlış bir değere sahip olması, sunucunun veya istemcinin isteği veya yanıtı yanlış yorumlamasına neden olabilir. Bu seçenek, isteğin içeriği düzenlendiğinde "Content-Length" başlığını otomatik olarak günceller, böylece isteğin doğru bir şekilde işlenmesini sağlar.

Bu iki özellik, özellikle manuel test sırasında trafiği dinlerken ve düzenlerken kullanıcının hatalarını minimize etmeye yardımcı olur. Yapılan değişikliklerin doğru bir şekilde yorumlanmasını ve isteğin hedefine doğru bir şekilde ulaşmasını garanti eder. Bu, test sırasında karşılaşılan potansiyel sorunları azaltır ve test sürecini daha verimli hale getirir.

<br><br>

<i style="color:#ff4500;">Response interception rules:</i>  Aynı muhabbet biraz bakınca zaten anlıyorsunuz o yüzden bu kısmı geçiyorum 😊

<br><br>

<i style="color:#ff4500;">WebSocket interception rules:</i>  WebSocket, gerçek zamanlı uygulamalar için kullanılan bir iletişim protokolüdür. WebSockets, tam çift yönlü iletişim kanalları sağlar ve bu, HTTP'nin talep-yanıt mekanizmasından farklıdır. WebSocket'ler, özellikle oyunlar, ticaret uygulamaları ve sohbet platformları gibi gerçek zamanlı etkileşim gereksinimleri olan uygulamalarda sıkça kullanılır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi6anv5U0mNqBoOKrRFW3vZRu-ICSDJwxJlYkJUrhE_RH2t63FOiwkXQnV2uf8N4WKUMpUXiWoaHphed-GdcWphmUaJfD-JE02BX3K49lMIz9kAXg73Dnr_V2WhoTzAul_FzbZnE8lnTCNjCYGFvEw9Wy8CsmUsETkCxJqEZiYOI86dH-LAoOWKm9F5FEiv/s16000/31.png" height="" width="">

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Intercept client-to-server messages: </i> Bu seçenek, istemciden sunucuya giden WebSocket mesajlarının yakalanmasını ve Intercept sekmesinde durdurulmasını sağlar. Bu, bir güvenlik uzmanının, istemciden sunucuya giden veriyi manuel olarak incelemesine, değiştirmesine veya manipüle etmesine olanak tanır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Intercept server-to-client messages: </i> Bu seçenek, sunucudan istemciye dönen WebSocket mesajlarını yakalamak için kullanılır. Sunucudan gelen veriyi incelemek ve değiştirmek, bir güvenlik uzmanının sunucunun nasıl tepki verdiğini görmesine ve bu tepkileri manuel olarak değiştirerek potansiyel güvenlik açıklıklarını belirlemesine yardımcı olabilir. Genel olarak, WebSockets interception kuralları, WebSockets trafiğini gerçek zamanlı olarak incelemek ve manipüle etmek isteyen güvenlik profesyonelleri için oldukça yararlıdır. Bu, özellikle gerçek zamanlı uygulamalarda potansiyel güvenlik sorunlarını belirlemek için kritik bir özelliktir.
<br><br>

<i style="color:#ff4500;">Response modification rules:</i>  Burp Suite'in bu bölümü, web uygulamalarının sunucudan istemciye gönderdiği yanıtları otomatik olarak nasıl değiştireceğini kontrol etmek için kullanılır. Bu, belirli güvenlik testleri sırasında yanıtları değiştirerek uygulamanın farklı senaryolara nasıl tepki verdiğini gözlemlemek için kullanılır.


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj9HPDmmBomnqir8vqIzw-LFv9LUhbDvkm66CCeVvvxVhfRrZvBDeUzofNRAZtOkDv4eA0lvD4sOM4fe81HAlB_jW4hnuQgW6MFAQgO9a7f6VNWtCulluJyomLvkSZRN1_-RE9Dp78WiwD8Q3zf1AIld-jM33hBJBrCgJBNehhWhHXSo-0xaeXgowY7LK9J/s16000/32.png" height="" width="">

**“Use these settings to control how Burp automatically modifies responses”**
Bu açıklama, kullanıcının yanıtları otomatik olarak nasıl değiştireceğine dair ayarları yapabileceğini belirtir.

Aşağıda verilen seçeneklerin her biri, bir web uygulamasının sunucudan dönen yanıtını belirli bir şekilde değiştirmek için kullanılır:


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Unhide hidden form fields: </i> Bu seçenek, istemciden sunucuya giden WebSocket mesajlarının yakalanmasını ve Intercept sekmesinde durdurulmasını sağlar. Bu, bir güvenlik uzmanının, istemciden sunucuya giden veriyi manuel olarak incelemesine, değiştirmesine veya manipüle etmesine olanak tanır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Prominently highlight unhidden fields: </i> Gizliliği kaldırılan form alanlarını belirgin bir şekilde vurgular. Bu, testerin hangi alanların değiştirildiğini hızla tespit etmesine yardımcı olur.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Enable disabled form fields: </i> Devre dışı bırakılmış form alanlarını etkinleştirir. Bu, bazı alanların neden devre dışı bırakıldığını anlamak ve bu alanlar üzerinde testler yapmak için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove input field length limits:  </i> Form alanlarının giriş uzunluk sınırlamalarını kaldırır. Bu, uzun veri girişlerinin bir uygulamaya nasıl etki ettiğini test etmek için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove JavaScript form validation: </i> JavaScript ile gerçekleştirilen form doğrulamasını kaldırır. Bu, sunucu tarafı doğrulamanın nasıl çalıştığını anlamak için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove all JavaScript: </i> Yanıttaki tüm JavaScript kodlarını kaldırır. Bu, JavaScript'ten bağımsız olarak bir uygulamanın nasıl çalıştığını görmek için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove <object> tags: </i> Yanıttaki tüm <object> etiketlerini kaldırır. Bu, bu tür etiketlerin uygulama üzerindeki potansiyel etkilerini analiz etmek için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Convert HTTPS links to HTTP:  </i> Yanıtlardaki HTTPS bağlantılarını HTTP'ye dönüştürür. Bu, bir uygulamanın şifrelenmemiş bağlantılara nasıl tepki verdiğini görmek için kullanılır.


<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove secure flag from cookies:  </i> Çerezlerden güvenli bayrağını kaldırır. Bu, bir çerezin güvenli olmayan bir bağlantı üzerinden nasıl iletilip iletilmediğini kontrol etmek için kullanılır.

<br><br>

<i style="color:#ff4500;">Match and replace rules:</i> Bu bölüm, Burp Suite Proxy içinden geçen istek ve yanıtların belirli bölümlerinin otomatik olarak nasıl değiştirileceğini kontrol eder. Özellikle, belirli desenleri eşleştiren ve belirli bir değerle değiştiren kuralları tanımlamanıza olanak tanır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiqVC9E6i_xcsCx5ejwOhODXVEN1sypiub6-PQ73D_qeBxr2KzKv0H_Ox4aSw2ZgrIc4DdR7IkhKZjmC3ONwTDE2LBPElGdPT-AfJwBl7RoC0Q8dRZJ2ap6eLnoVA-Wl4G_B-MkXtS_NuYWH2tkDghs0N03F-35K7wZXvsaePuLOSH9y_SgXHPFYYSMAQS4/s16000/33.png" height="" width="">

**“Use these settings to automatically replace parts of requests and responses passing through the Proxy”**
Bu cümle, bu bölümün, Burp Suite Proxy'den geçen istek ve yanıtların spesifik kısımlarını otomatik olarak nasıl değiştireceğine dair ayarları yapılandırmanıza yardımcı olacağını belirtir.

<br><br>

<i style="color:#ff4500;">TLS pass through:</i> Burp Suite'in "TLS Pass Through" özelliği, belirli hedef web sunucuları için TLS bağlantılarının doğrudan geçirilmesini sağlar. Bu, belirli sunucularla yapılan bağlantıların Burp Proxy tarafından engellenmeden doğrudan kurulmasına olanak tanır. Bu, özellikle belirli sunucularla SSL/TLS bağlantısı kurarken yaşanan sorunlarda veya belirli bir sunucuyla yapılan trafiği incelemek istemediğinizde faydalıdır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLRlopk90-AY_TlMtds3eZTOuB-vwQ3LVFU2ViyRsk5DPaS6tdgShh7eaRd6uOskFfopDLRNf3Cg8wuOkECmTXgf2pJwOsEfP-MMtoLHAO_5LiMfr3bxVlrS1h2nrpZQdp-DcKQSRmIF5FMLq1AmFq0ZaHxdSgjTroyCKEwuerLPpI0JK4QaJ0NoqiQwuo/s16000/34.png" height="" width="">

Bağlantılar doğrudan geçirildiğinde, bu bağlantılardan geçen istek veya yanıtların detayları Proxy'de görüntülenmez. Yani, eğer bir web sunucusunu bu listeye eklerseniz, bu sunucuyla olan trafiğinizi Burp Suite içinde göremezsiniz.

**Enabled:** Bu, belirli bir kuralın aktif olup olmadığını belirtir. Eğer bu kutucuk işaretliyse, belirli IP aralığı veya host için TLS trafiği doğrudan geçirilir.
**Host / IP range:** Burada hangi web sunucusu veya IP aralığının TLS trafiğinin doğrudan geçirileceğini belirtirsiniz.
**Port:** TLS trafiğinin hangi port üzerinden geçirileceğini belirtir. Örneğin, standart HTTPS portu 443'tür.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Automatically add entries on client TLS negotiation failure:</i> Eğer bu seçenek işaretliyse, bir TLS müzakere hatası oluştuğunda, hataya neden olan sunucu otomatik olarak "TLS Pass Through" listesine eklenir. Bu, bazı SSL/TLS sorunlarıyla karşılaşıldığında trafiği hızla doğrudan geçirerek sorunların üstesinden gelmeye yardımcı olabilir.

<br><br>

<i style="color:#ff4500;">Proxy history logging:</i> Burp Suite'in "Proxy History Logging" özelliği, Proxy'nin kapsam dışı kalan öğeleri geçmişe ve diğer araçlara otomatik olarak gönderip göndermemesi gerektiğini seçmenizi sağlar. Bu, özellikle belirli bir hedef veya etki alanı üzerinde çalışırken, diğer gereksiz trafiği filtrelemek ve odaklanmak istediğiniz trafiği gözlemlemek için oldukça yararlıdır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgrFSkodK8738tASxY56wZWIWX1lcjXmsN4uG8URoU8iFxpRAnaQnLO_PNz8F_vK2jFRJZ5upVYTJbUhi9sPpOqk62pAYj0zqv1os0RfSkDHuubOCPqGoXlX5aj0TWdban4uclbzlLUUlH7kdxOFjuLvDYujCO0m1yZbqnvYFHeWs7aQWf5zgxdtay9TsZu/s16000/35.png" height="" width="">

Target kapsamına bir öğe eklediğinizde, bu ayar Proxy'nin kapsam dışı kalan öğeleri geçmişe ve diğer araçlara nasıl yönlendireceğini belirlemenizi sağlar. Bu, özellikle belirli bir hedefe odaklanmak istediğinizde trafiği sınırlamak için kullanılır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Stop logging out-of-scope items:</i> Bu seçenek seçildiğinde, kapsam dışı kalan öğeler otomatik olarak geçmişe ve diğer araçlara gönderilmez. Bu, gereksiz trafiği azaltmanıza yardımcı olabilir.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Ask me what to do each time: </i> Bu seçeneği seçerseniz, her kapsam dışı öğe için ne yapılması gerektiğine dair bir uyarı alırsınız. Bu, belirli durumlarda daha granüler bir kontrol sağlar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Do nothing: </i> Bu seçenek seçildiğinde, Proxy kapsam dışı öğeleri normal şekilde geçmişe ve diğer araçlara göndermeye devam eder. Bu, tüm trafiği gözlemlemek istediğinizde kullanılır.

<br><br>

<i style="color:#ff4500;">Default Proxy interception state:</i> Bu bölüm, Burp Suite'u başlattığınızda Proxy'nin trafiği yakalama (interception) durumunu nasıl başlatmak istediğinizi belirlemenizi sağlar. Bu özellik, sık sık aynı konfigürasyonları kullanıyorsanız veya belirli bir duruşla Burp'u başlatmak istiyorsanız oldukça kullanışlıdır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiwAVb3NjuL-YpPvlKSRwnbapEcd0_oCdLmQaqEGkLRSGwSG0bmx2K2VzCg2ec1f9MEp3Mf2jFfABNTSNQYhEYSn7v2KRg1O83bFDykQH5kQARJ1NCKEqckTgaj5av3sc7vW82Sns2Xn-LpoGfvx9M3xziqTop_URsJOssAOnhFXD66BzSjVJhq5dxmi_2L/s16000/36.png" height="" width="">

Burp Suite'i başlattığınızda, Proxy'nin trafiği otomatik olarak yakalayıp yakalamayacağını (intercept) veya son kapatıldığında hangi durumdaydıysa o durumu sürdürüp sürdürmeyeceğini seçebilirsiniz. Bu, sık sık farklı test senaryoları arasında geçiş yapıyorsanız, her seferinde ayarları manuel olarak değiştirmek zorunda kalmadan hızlıca başlamak için oldukça kullanışlıdır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Enable Interception: </i> Bu seçeneği seçerseniz, Burp Suite'i her başlattığınızda trafiğin otomatik olarak yakalanmasını (intercept) sağlar. Bu, aktif olarak bir web uygulamasının trafiğini incelemek istediğinizde kullanışlıdır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Disable Interception: </i> Bu seçenek seçildiğinde, Burp Suite'u başlattığınızda otomatik olarak trafiği yakalamaz. Genel gözlem veya belirli bir hedef olmadan tarama yapmak istediğinizde bu seçenek kullanılır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Restore the settings that was selected in the Proxy > Bu seçeneği seçerseniz, Burp'u son kapatışınızdaki konfigürasyonla başlatır. Yani, eğer trafiği yakalama modunda kapatıldıysa, bu modda başlatır; yakalama modunda değilse, yakalama modunda başlamaz. Bu seçenek, önceki oturumunuzdaki çalışma durumunuzu sürdürmek istediğinizde kullanılır.
<br><br>

<i style="color:#ff4500;">Miscellaneous:</i> Bu bölüm, Burp Proxy'nin varsayılan davranışını özelleştirmek için bir dizi seçeneği içerir. Bu seçenekler, belirli test senaryolarınıza veya karşılaştığınız özel durumlara göre Burp Suite'in davranışını ince ayar yapmanıza olanak tanır.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh5hZLHuwwnIMXhxk-vuPgoa9VTqW1eEZmTNwY4d8Ajkzg2LOq3g4ZxhRcb7GoLzH9UJunjlkzDocTuhNFpeGEju3ipg_laSSmJBN4K3Vu3_UDV8gp54_uONj6uPysUXvfDxevOkS4QA0drXBTc0olYDeO4gTqIfd5Jb_wSQWWLzgxSIukYnXsKbbLH8vQF/s16000/37.png" height="" width="">

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Use http/1.0 in requests to server:</i> Bu seçenek, sunucuya yapılan isteklerde HTTP/1.0 protokolünün kullanılmasını zorlar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Use http/1.0 in responses to client: </i> Cevaplar için HTTP/1.0 protokolünün kullanılmasını zorlar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Set response header “Conection:close”:</i> Bu, sunucudan dönen yanıtlarda "Connection: close" başlığının ayarlanmasını sağlar, böylece bağlantının her yanıttan sonra kapatılmasını zorlar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Set ‘Connection’ header on incoming requests when using HTTP/1: </i> Gelen isteklerde HTTP/1 kullanılırken "Connection" başlığını ayarlar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Strip Proxy-* headers in incoming requests: </i> Gelen isteklerde bulunan ve "Proxy-*" ile başlayan HTTP başlıklarını kaldırmak için kullanılır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Remove unsupported encoding from Accept-Encoding headers in incoming requests:</i> Gelen isteklerdeki "Accept-Encoding" başlıklarından desteklenmeyen kodlamaları kaldırır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Strip Sec-WebSocket-Extensions headers in incoming requests:</i> Gelen isteklerdeki "Sec-WebSocket-Extensions" başlıklarını kaldırır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Unpack gzip/deflate in requests:</i> İsteklerde sıkıştırılmış içeriği (gzip veya deflate kullanılarak) açar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Unpack gzip/deflate in responses:</i> Yanıtlarda sıkıştırılmış içeriği (gzip veya deflate kullanılarak) açar.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Disable web interface at http://burpsuite:</i> http://burpsuite adresindeki web arayüzünü devre dışı bırakır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Suppress Burp error messages in browser:</i> Tarayıcıda görünen Burp hata mesajlarını bastırır.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Don’t send items to Proxy history or live tasks:</i> Öğelerin Proxy geçmişine veya canlı görevlere gönderilmesini engeller.

<i style="color:#ff4500;">&nbsp;&nbsp;&nbsp;•	Don’t send items to Proxy history or live tasks, if out of scope:</i> Eğer öğeler kapsam dışındaysa, Proxy geçmişi veya canlı görevlere gönderilmesini engeller.

<br><br><br>

<h1 style="color:yellow;">INTRUDER EKRANI</h1>










