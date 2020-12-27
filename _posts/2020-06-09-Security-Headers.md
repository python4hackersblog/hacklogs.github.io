---
title: Security Headers
description: Security Headers
layout: Yazılar
permalink: Security-Headers
---

Burada temel seviyede  bir kaç bir şey karalayacağım  http olsun https olsun http security headers gibi basit muhabbetler.Zaman oldukça güncelleyeceğim.Temel terimlerden başlayalım.
<br>

<h3 style="color:yellow;">HTTP Nedir ?</h3>
<br>
Http’nin açılımı **Hyper Text Transfer Protocol**’dür.Yani Türkçe karşılığı Hiper Metin Transfer Protokolü.Bu protokol ağ üzerinden web sayfalarının görüntülenmesini sağlar.Kullanıcı ile sunucu arasındaki kurallarıda bu protokol belirler.Başlangıçta statik metin tabanlı kaynakları almak için geliştirilmiş basit bir prokoldü.Ozamandan bu yana oldukça genişletilip,geliştirildi.
<br>
HTTP Protokolü temelde bağımsızdır.HTTP iletişim olarak TCP kullansada,her istek ve yanıt cevapları farklı bir TCP bağlantısı kullanabilir.Siz sunucuya bir istek yollarsınız , isteğiniz browserlar ile karşıya iletilir , sonra sunucu yolladığınız isteği web sunucu programları(IIS,Apache vs.) yardımıyla cevap verir.Günümüzün tüm web uygulamaları tarafından kullanılmaktadır.

<br>
<h3 style="color:yellow;">HTTP Mesajları </h3>

<br>

<p style="color:yellow;">HTTP Request</p>

HTTP mesajları (request,response) gövdesinde her biri ayrı satırda bulunan bir veya birden fazla başlıktan oluşur.İsteğe bağlı mesaj gövdesi de bulunur.Klasik bir HTTP İsteği aşağıdaki gibidir.

<img src="https://1.bp.blogspot.com/-9zgsHJbPHz8/Xt95P_9eWyI/AAAAAAAAAY4/mUSH-xHwFx8u-mugUZBiVKtKdOAwHJwxQCNcBGAsYHQ/s1600/1.png" >
<br>

http isteğinin ilk boşluklar ile ayrılmış 3 bölümden oluşmaktadır.Yukarıda görüldüğü üzere ilk satır şu şekildedir ;

<p style="color:red;">GET /login.php HTTP/1.1</p>

İlk satır birinci bölüm **GET** http methodunu gösterir.En yaygın methoddur.GET isteklerinin bir mesaj gövdesi yoktur.
İlk satır ikinci bölüm yukarıdaki istekte bu **/login.php** kısmıdır.Parametre içerir istemcinin hedefe ilettiği parametreleri içerir.
İlk satır üçüncü bölüm  burada da **HTTP/1.1** Kullanılan http sürümü.

Diğer noktalarada kısaca değinelim ;

<p style="color:red;">Referer:</p>İsteğin kaynaklandığı URL’i belirtmek için kullanılır.
<p style="color:red;">User-Agent:</p>İsteği oluşturduğumuz tarayıcı veya diğer istemci taraflı yazılımları hakkında bilgiyi barındırır.
<p style="color:red;">Host:</p>isteğin yollandığı ana bilgisayar adı diyebiliriz.Aynı sunucuda birden fazla web sitesi barındırıldığında bu gereklidir.
<p style="color:red;">Cookie:</p>Burada sunucunun istemciye verdiği ek parametreleri göndermek için kullanılır.

<br><br>

<p style="color:yellow;">HTTP Response</p>

Yolladğımız istekler doğrultusunda sunucunun  bize verdiği cevaplar diyebiliriz.

Klasik bir response örneği şu şekildedir.

<img src="https://1.bp.blogspot.com/-jotSdUmD-cQ/Xt95QDmFaaI/AAAAAAAAAZA/TCR2wB1nnhI_wTGtpCE19Cb0T-jqv_VzgCNcBGAsYHQ/s1600/2.png">
<br>

Yukarıdaki istekte görüldüğü üzere ilk satırımız 3 kısımdan oluşmakdtadır.
İlk satır ilk kısım kullanılan HTTP sürümü.
İlk satır ikinci kısım yolladğımız istek sonucunu gösteren http durum kodu.Yukarıdaki isteğimizde 200 olduğunu görüyoruz en yaygın durum kodudur.İsteğin başarılı olduğunu anlıyoruz…

<p style="color:red;">Server:</p> sunucu yazılımı hakında bilgi. Vs.
<p style="color:red;">Content-Length:</p> mesajın bayt cinsinden uzunluğunu gösterir.

Zaten görüldüğü gibi başlıklar basit ve anlaşılır bunlara biraz daha detaylı olarak değineceğiz.

<br><br>

<h3 style="color:yellow;">HTTP Methodları</h3>

Http methodları ile ister istemez çok haşır neşir olacaksınız.Çok detaya inmeden üstün körü neyin ne olduğuna değineceğiz.**Get** ve **Post** methodları bizim için çok önemlidir.Bu methodların önemsenmemesi uygulamanın güvenliğini etkiler.
<p style="color:red;">GET</p>methodu kaynakları almak için geliştirilmiş bir methodtur.Zaten yukarıda az çok anladık get methodunu ufak bir örnek ile..İstediğimiz kaynağa parametre göndermek için kullanılabilir.Get ile Post arasındaki farkları iyice bilmek gerekir bunun içinde ufak bir araştırma yapmanız sizin yararınıza olur.
<p style="color:red;">POST</p>Bu method ile request’de bahsettiğimiz parametreler , yani istek parametreleri hem URL sorgu dizesinde hem de mesajın gövdesinde gönderilebilir.
<p style="color:red;">HEAD</p>Get  ile aynı şekilde çalışır.Tek fark sunucudan dönen response içeriğinde mesaj gövdesi yoktur.
<p style="color:red;">TRACE</p>Teşhis işlemleri için kullanılır.
<p style="color:red;">OPTIONS</p>sunucudan belirli bir kaynak için kullanılabilen http methodlarını bildirmesini ister.
<p style="color:red;">PUT</p>isteğin gövdesinde bulunan içeriği kullanrak belirtilen kaynağı sunucuya yüklemeye çalışır.
<p style="color:red;">DELETE</p>belirtilen kaynağı siler
<p style="color:red;">CONNECT</p>kaynak tarafından belirtilen sunucuya bir bağlantı oluşturur.
<p style="color:red;">SEARCH</p>kaynakları sorgulamak için kullanılabilir.

<br><br>

<h3 style="color:yellow;">HTTP Başlıkları Nelerdir?</h3>
<br>
Yukarıda az çok değindik birazdaha ayrıntılı olarak değinmekte fayda var.Genel olarak karşılaştıklarımızdan kısa kısa bahsedelim :
<p style="color:red;">Connection:</p>Http transferi tamamlandıktan sonra bağlantının kapatıp kapatılmayacağını beldirir.
<p style="color:red;">Content-Length:</p>Mesaj gövdesinin uzunluğunu bayt cinsinden gösterir.
<p style="color:red;">Content-Encoding:</p>Mesaj gövdesinde bulunan gzip gibi uygulamalar tarafından daha hızlı iletişim için response(yanıtlar) sıkıştırmak amacıyla ne tür bir encode yöntemi kullandığını belirtir.
<p style="color:red;">Content-Type:</p>İçerik Tipi.text/html</p>
<p style="color:red;">Transfer-Encoding:</p>Http üzerinden aktarımı kolaylaştırmak için gerçekleştirilen kodlamayı belirtir.

<br>

<h3 style="color:yellow;">Request Başlıkarı Nelerdir ?</h3>
<p style="color:red;">Accept:</p>Kabul edilebilir medya tiplerini belirtir.
<p style="color:red;">Accept-Encoding:</p>Accept’e benzer fakat , İstemcinin hangi tür kodlamayı kabul ettiğini belirtir.
<p style="color:red;">Authorization:</p>Yetkilendirme http kimlik doğrulama türlerinden biri için sunucuya bilgi gönderir.
<p style="color:red;">Cookie:</p>Çerez, websitesinin içerisinde bulundurduğu bilgiler yer alır diyebiliriz.
<p style="color:red;">Host:</p>Ana makine adı.
<p style="color:red;">If-Modified-Since:</p>Tarayıcının istenen kaynağı en son ne zaman aldığını belirtir.
<p style="color:red;">If-None-Match:</p>Mesaj gövdesinin içeriğini gösteren bir Varlık etiketi belirtir.
<p style="color:red;">Origin:</p> İsteklerin kaynaklandığı etki alanını belirtmek için kullanılır. 
<p style="color:red;">Referer:</p>Geçerli isteğin kaynaklandığı URL’i belirtir.
<p style="color:red;">User-Agent:</p>Tarayıcı veya isteği oluşturan diğer istemci taraflı yazılımlar hakkında bilgi sağlar.

<br>

<h3 style="color:yellow;">Response Başlıkları Nelerdir ?</h3>
<p style="color:red;">Access-Control-Allow-Origin:</p>Kaynağın Ajax istekleri aracılığıyla alınıp alınamayacağını belirtir.
<p style="color:red;">Cache-Control:</p>Önbellek kontrolü, önbellek kurallarını tarayıcıya iletir ;örnek: no,cache
<p style="color:red;">Location:</p> konum, Yönlendirmenin hedefini belirtmek.
<p style="color:red;">Server:</p>Kullanılan web sunucusu yazılımı hakkında bilgi.
<p style="color:red;">X-Frame-Options:</p>Mevcut yanıtın nasıl yükleneceğini belirtir.
<p style="color:red;">Set-Cookie:</p>Sunucuya geri gidecek çerezler diyebiliriz.

<br>

==>**Cookie** demişken biraz değinmekte fayda görüyorum: Cookieler çoğu zaman Web uygulamalarının güvendiği HTTP protokolünün önemli bir parçasıdır.Güvenlik açıklarından yararlanmak için bir aracı olarak kullanılabilirler.Diğer paramatre türlerinden farklı olarak cookieler  uygulama ve kullanıcı tarafından özel bir işlem yapılmadığı takdirde her istekte yeniden gönderilmeye devam eder.

<p style="color:red;">Set-Cookie</p>, tarayıcının cookie’yi nasıl ele alacağını kontrol etmek için kullanılabilecek isteğe bağlı bazı özellikleri içerebilir;
<p style="color:red;">Expires:</p>Son kullanma tarihi , cookie’nin geçerli olacağı tarihi ayarlar.Kullanılmaz ise cookie sadece geçerli tarayıcı oturumunda kullanılır.
<p style="color:red;">Domain:</p>Cookie’nin geçerli olduğu domaini belirtir.
<p style="color:red;">Path:</p>Çerezin geçerli olduğu URL yolunu belirtir.
<p style="color:red;">Secure:</p>Bu özellik ayarlanırsa cookie yalnızca HTTPS isteklerinde gönderilir.
<p style="color:red;">HttpOnly:</p>Bu özellik  ayarlanırsa istemci tarafından tanımlama bilgisine doğrudan JavaScript aracılığı ile erişilemez.
Bu özelliklerin her biri uygulamaların güvenliğini etkileyebilir.Daha fazla detaya inilebilir tabi ön bilgi olsun diye detaya inmeden değinmek istedim bunlar hakkında daha detaylı bir araştırma yapabilirsiniz…

<br>


<h3 style="color:yellow;">HTTP Güvenlik Başlıkları ?</h3>

Web uygulamalarıda güvenlik önlemleri alırken göz önünde bulundurmamız gereken birçok şey vardır.HTTP güvenlik başlıklarını keşfetmek başlangıç için iyi olacaktır.Uygulanması kolaydır.HTTP güvenlik başlıkları saldırıları,zafiyetleri azaltmaya yardımcı olur.

Eğer daha detaylı bir şekilde incelemek isterseniz <a href="https://owasp.org/www-project-secure-headers/">BURADAN</a> inceleme yapabilirsiniz...

<br>

Peki bu güvenlik başlıkları nelerdir ?
<br>

<p style="color:yellow;">a)	X-XSS-protection</p>

X-XSS Koruma başlığı Cross-site-scripting (xss) filtresini etkinleştirmek için geliştirilmiştir.Öncesinde tabi xss zafiyetlerinin giderilmesi gerekmektedir.

<p style="color:red;">X-XSS-Protection: 1; mode=block</p>

<br>
<p style="color:yellow;">b)Strict-Transport-Security Header</p>

Kısaca HSTS web iletişimini  her istek için HTTPS kullanmasına zorlar.

<p style="color:red;">Strict-Transport-Security: max-age=315360</p>

Farklı durumlarda ortaya çıkabilecek (MITM) saldırısının önlenmesine yardımcı olur.

<br>

<p style="color:yellow;">b)	X-Frame-Options Header</p>

Clickjacking güvenlik açığını önlemek için  X-Frame-Options başlığı kullanılabilir.Bu headerı kullanrak saldırganın frame/iframe çağrısı yapmasının önüne geçebiliriz.
<p style="color:red;">
X-Frame-Options: deny
X-Frame-Options: SAMEORIGIN
</p>

Bu başlığın 3 tane parametresi vardır.

<p style="color:red;">ALLOW-FROM:</p>Yalnızca belirli bir URI üzerindne frame çağrısını kabul et.
<p style="color:red;">SAMEORIGIN:</p>Sadece kendi domainimizi frame/iframe içerisinde çağrılmasını kabul et başka domainleri engelle.
<p style="color:red;">DENY:</p>Domainin herhangi bir frame/iframe içerisinde çağrılmasını engelle.

<br>

<p style="color:yellow;">c)	X-Content-Type-Options</p>
Bu headerı kullandığımız zaman MIME Type Sniffing risklerini önleyebiliriz. 
<p style="color:red;">X-Content-Type-Options: nosniff</p>

<br>

<p style="color:yellow;">d)Content Security Policy</p>
Bu headerı kullanarak XSS,Clickjacking,code injection gibi saldırılarının riskini  aza indirebiliriz.CSP ,tarayıcıya izin verilen içeriği yüklemesi talimatını verir.Uygulamadan önce doğrulamak gerekir çünkü tüm tarayıcılar CSP’yi desteklememektedir. 
CSP’Yİ uygulamak için bir çok parametre vardır. En çok kullanılan iki yönteme değinelim:
<p style="color:red;">default-src:</p>Tanımlanan kaynaktan herşeyi yükle.
<p style="color:red;">script-src:</p> Eklentilerin nereden yükleneceğini belirtin. 

<p style="color:red;">Content-Security-Policy: script-src 'self' https://www.google-analytics.com</p>

Detaya inmeden üstün körü bahsediyoruz CSP’yi uygulamak için birden fazla parametre vardır bunun için ve daha adetaylı bilgi için şu linki bırakıyorum: <a href="https://owasp.org/www-project-secure-headers/#Content-Security-Policy">Content Security Policy</a>

<br>

<p style="color:yellow;">e)	HTTP Public Key Pinning</p>
Sertifikayı sabitleyip MITM saldırılarını en aza indirir.

<p style="color:red;">Report-uri=”url” , pin-sha256=”sha256key”,max-age=,IncludeSubDomains gibi 4 farklı parametre almaktadır.</p>

<br>

<p style="color:yellow;">f)	X-Permitted-Cross-Domain-Policies</p>
PDF,Flash  vs gibi  ürünleri kullanıyorsak.Tarayıcıya istekleri bir etki alanı üzerinden ele alınması gerektiğini bildirmek için,kötüye kaynak kullanımını önlemek için ,sitenin varlıklarını diğer alanlardan yüklemeyi kısıtlamak için kullanabiliriz.

<p style="color:red;">all:</p>Her şey serbest.
<p style="color:red;">none:</p>Policy’e izin verilmiyor.
<p style="color:red;">master-only</p>Sadece ana policy’e izin verir.
<p style="color:red;">by-ftp-only</p>Sadece FTP server için geçerlidir.
<p style="color:red;">by-content-only:</p>Belirtilen  türdeki içeriğe izin vermek için kullanılır.

<p style="color:red;">X-Permitted-Cross-Domain-Policies "none"</p>


<p style="color:yellow;">g)	Referrer-Policy</p>
Web sayfaları üzerinden başbir adrese erişim sağlandığı zaman Referer ile  kendi adresini belirtirmektedir.
Detaylı inceleme için : <a href="https://owasp.org/www-project-secure-headers/#Content-Security-Policy">Content Security Policy</a>

<p style="color:red">Header set Referrer-Policy "no-referrer”</p>

<br>

<p style="color:yellow;">h)	Feature-Policy</p>

Bu başlık developerların  tarayıcı özelliklerini ve API’lerin kullanımlarını seçici oalrak etkinleştirmelerine ve devre dışı bırakmalarına yarar.

<p style="color:red;">Feature-Policy: vibrate 'none'; geolocation 'none'</p>

<br>

<h3 style="color:yellow;">Security Header Scanner</h3>

Web sayfalarının güvenlik durumları hakkında bilgi toplamak için kullanabileceğimiz web sayfalarından birtanesi <a href="https://securityheaders.com/">SecurityHeaders.Com</a>'dur.

Bu web sayfası HTTP başlıklarını analiz eder ve  web sayfasının temel analizini hakkında bize bilgi verir. 

http://testphp.vulnweb.com/ adresini tarayarak nasıl sonuçlar elde ettiğimize bakalım.

<img src="https://1.bp.blogspot.com/-tSGfkavRw8s/Xt95RMd6kdI/AAAAAAAAAZM/i9UvmtkjwQgPAmIN_iPCpGE-Tp2YBbeCgCNcBGAsYHQ/s1600/6.jpg">

yukarıda görüldüğü üzere eksik başlıkları görebiliyoruz...

<br><br>

<h3 style="color:yellow;">HTTP Durum Kodları ? </h3>

<p style="color:red;">1xx:</p>Bilgilendirici
<p style="color:red;">2xx:</p>Başarılı
<p style="color:red;">3xx:</p>Yönlendirme
<p style="color:red;">4xx:</p>İstemci Hatası
<p style="color:red;">5xx:</p>Sunucu Hatası
<br>
Bir web uygulaması ile haşır neşir olurken karşılaşabileceğiniz bir çok özel kod vardır…
<br>
<p style="color:red;">100 Continue:</p>Talepte sıkıntı yok devam 
<p style="color:red;">200 OK:</p>İstek başarılı
<p style="color:red;">301 Moved Permanently:</p>Kaynağın  kalıcı olarak başka bir yere taşındığını bildirip yönlendirme sağlar.
<p style="color:red;">302 Found:</p>Geçici olarak farklı bir yere yönlendirme.
<p style="color:red;">304 Not Modified: Değiştirilmedi:</p>Tarayıcıya, istenilen kaynağın önbelleğe alınmış kopyasını kullanmasını söyler.
<p style="color:red;">400 Bad Request:</p>İstek hatalı.Geçersiz bir http isteği gönderildiğini gösterir.
<p style="color:red;">401 Unauthorized:</p>Yetkisiz istek , istek yapılmadan önce sunucunun http kimlik doğrulaması gerektiğini söyler.
<p style="color:red;">403 Forbidden:</p>Yasak , kimlik doğrulamasına bakılmaksızın istenen kaynağa izin verilmediğini gösterir.
<p style="color:red;">404 Not Found: Bulunamadı</p>İstenen kaynağın mevcut olmadığını gösterir.
<p style="color:red;">405 Method Not Allowed:</p>Yönteme izin verilmiyor,kullanılan yöntem desteklenmiyor.
<p style="color:red;">413 Request Entity Too Large:</p>Varlık isteği çok büyük, Buffer overflow kasıyorsanız karşılaşabilirsiniz.
<p style="color:red;">414 Request URI Too Long:</p> 413 yanıtına benzer.
<p style="color:red;">500 Internal Server Error:</p>Sunucuda hata oluştur ve istek yerine getirilmedi.
<p style="color:red;">503 Service Unavaliable:</p>Hizmet kullanılamıyor. 

<br><br>

<h3 style="color:yellow;">HTTPS Nedir ? </h3>
<br>
HTTP protokolü aktarım mekanizması olarak düz TCP kullanır, Şifreleme yoktur. HTTPS aslında http ile aynı uygulama katmanı protokolüdür. HTTPS güvenli aktarım mekanizması olan Secure Sockets Layer (SSL) üzerinden tünellenir.
Bu da ağ üzerinden geçen verilerin gizliliğini ve bütünlüğünü korur.SSL’in günümüzde yerini TLS (Transport Layer Security) almıştır.

SSL/TLS  kullanılan sistemlerin kimlik bilgileri şifreli bir anahtar ile dijital şekilde bağlanır ve veri akışlarının ifşa edilmesinin önüne geçilir.SSL/TLS her oturum için güvenli bir oturum anahtarı oluşturarak çalışmaktadır.

<br>

<h3 style="color:yellow;">HTTP/2 Nedir Farkları Nelerdir?</h3>
<br>
Http/1.1 protokolü  css,video,resim,js vb. gibi her dosya için ayrı ayrı istek gönderir.Buda süre bazlı uzamaya neden olmaktadır.
Http/2 Protokolünd eistekler toplu olarak alınır.Süre bakımından hızlı olmaktadır.

Http/2 ,htp mesajlarının istemci ve sunucu arasında nasıl ele alındığını ve aktarıldığını belirleyen Binary Framing Layer  (İkili Çerçeveleme Katmanı) sunar.

Http/2  mesajları,, http1.1 gibi düz metin protokolü kullanmaz.Herbiri ikili(binary) formatında kodlanmış küçük mesajlara ve çerçevelere bölünür.

Üstün körü değinmiş olduk daha detaylı incelemenizi tavsiye ediyorum ve şu linki buraya bırakıyorum…
<a href="https://developers.google.com/web/fundamentals/performance/http2">HTTP/2</a>










 















