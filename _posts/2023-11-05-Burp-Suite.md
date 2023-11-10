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


<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEijTYTzjbsCmTWBKCanqJpwosbG9WbwumrOZNPYRJKeDApSVvr7vHRCONDzZ8Y8FDXEMJiHTok65xTW-FEyDB7cNQPG_O0TV39ix_DLb-pBvJD5Qrzg6ELvUhNKph-FWOy_9V2OWnvmiIFH6n_jv5C49YiU91xDZ3J0ejlCSwLI4sdqMZ4c6pW01b6FMQi9/s16000/24.png" height="" width="">











