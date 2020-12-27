---
title: HTML Injection
description: HTML Injection - BWAPP
layout: Yazılar
permalink: html-injection
---

**HTML Injection** basit bir zafiyettir.Az biraz HTML bilgisi bilmek gerekir.**Cross Site Scripting(XSS)**'e benzer fakat **HTML Injection** da enjecte edilen içerik XSS'de olduğu gibi komut dosyası değil düz mhtml etiketleridir.XSS'e göre daha az tehlikelidir.Fakat bu kötü amaçlı kullanılamayacağı anlamına gelmez.Tamamen istemci taraflı saldırılardır.İki tür HTML Injection vardır;**Stored** ve **Reflected**.

**HTML Injection** web sayfalarının savunmasız kısımlarında rastgele HTML kodu çalıştırıldığında ortaya çıkan bir zafiyettir diyebiliriz.Bu saldırılar web sayfalarında değişiklik yapmak kimlik bilgileri çalmak vs vs gibi sonuçlara yol açabilmektedir. 

<br>

<h3 style="color:yellow;">HTML Injection Türleri</h3>

<p style="color:yellow;">Reflected Html Injection</p>
Reflected(yansıyan) html injeciton.Html kodu web sunucusunda kalıcı olarak saklanmaz.Yazdığımız girdiye cevap verir.Reflected Html Injection HTTP yöntemlerine göre farklı şekillerde gerçekleştirilebilir.

**A)** HTML Injection Reflected GET<br>
**B)** HTML Injection Reflected POST<br>
**C)** HTML Injection Reflected URL<br><br>

<p style="color:yellow;">A) HTML Injection Reflected GET</p>

<img src="https://1.bp.blogspot.com/-vWl-w7rrHVs/Xxg9QvkpipI/AAAAAAAAAak/TitNufAcRoAah6xDTVaaIFje7_yhhzlcACPcBGAYYCw/s1600/1.png"> <br>
<img src="https://1.bp.blogspot.com/-3TTwmg4jnDI/Xxg9QvEBvzI/AAAAAAAAAak/hLd8BTjZG4MzadHUQ8XR41NFixk4m1qzwCPcBGAYYCw/s1600/get%2Burl.png"> <br>

Görüldüğü üzere bizden adımızı,soyadımızı girmemizi isteyen bir ekranımız var url kısmına baktığımızda girdilerimizin direkt gözüktüğünü farkediyoruz,bu bize GET olduğunu gösteriyor.Şimdi ilk önce kursad:kursad şeklinde bir girdi yollayalım ve sonrasında html tagımızı kullanarak <h1>kursad</h1> şeklinde bir kullanım ile sonucumuza bakalım.<br>

<img src="https://1.bp.blogspot.com/-zQnZQKrzvVE/XxhB7v79I4I/AAAAAAAAAas/VmeFSn1jqOsOxn-vTd4elmCBcIt7Wc29wCNcBGAsYHQ/s1600/2.png"><br>
<img src="https://1.bp.blogspot.com/-q1Pwm6-GAII/XxhB7mPnjQI/AAAAAAAAAa0/uC-eyaOmF8U67rXR9qMFJHDxk0sKaJ7DQCNcBGAsYHQ/s1600/3.png"><br>
<img src="https://1.bp.blogspot.com/-z3aWgBM-h-A/XxhB7vKdKGI/AAAAAAAAAaw/Tj796X24fh8A8S4KOy7rRzyeIJyAxCVGACNcBGAsYHQ/s1600/4.png"><br><br>


Diğer örneğimize göz atalım bu örneğimizde bir tık önlem alınmış, html taglarımızı kullanarak devam edelim ;<br><br>

<img src="https://1.bp.blogspot.com/-JHwlYlXz4K0/XxhD9yoRdGI/AAAAAAAAAbM/fHiTpHCDrqwGD_Gb2vzvJRvGjjsaLEMrwCNcBGAsYHQ/s1600/5.png"><br>

Görüldüğü üzere bu sefer ekrana bir yansıma olmadı..<br><br>

<img src="https://1.bp.blogspot.com/-8MjanSWZPJM/XxhD94wvh2I/AAAAAAAAAbI/1iPpH0_Jhts8-WtJSnnT68nXEtHSExQdgCNcBGAsYHQ/s1600/6.png"><br><br>

Kaynağa baktığımızda "<","&",">" karakterlerinin başka karakterlere dönüştüğünü görebiliyoruz.Bu nedenle basit şekilde URL encode kullanarak ifltrelemeyi atlatıp sonuç almaya çalışalım.<br>

<img src="https://1.bp.blogspot.com/-UrYhLsFZXE4/XxhD-c9DoaI/AAAAAAAAAbU/bOd6_Krn5ukSc0vsr59eDkzY21_A_OfdwCNcBGAsYHQ/s1600/8.png"><br>

<img src="https://1.bp.blogspot.com/-5OBeL2TMKkc/XxhD9xpGOsI/AAAAAAAAAbQ/h29hjdmXU2AhFAsWoZvez-cHx0-C7XtggCNcBGAsYHQ/s1600/7.png"><br><br>

Zafiyetli bir web sayfamız var ekstradan onuda şuraya ekliyorum;<br>

<img src="https://1.bp.blogspot.com/-w6Q9PrW_zOM/XxhD-i-z3tI/AAAAAAAAAbY/-KztnPlb7MsJ3XlDaCqkwSDHqDHRM53rQCNcBGAsYHQ/s1600/9.png"><br><br><br>

<p style="color:yellow;">B) HTML Injection Reflected POST</p><br>

<img src="https://1.bp.blogspot.com/-_mntQNcSgxM/XxhIjmX2-nI/AAAAAAAAAb0/Vx9Yx0YFXWMJvTvfS-BZkobR5ntHvzpHwCNcBGAsYHQ/s1600/post%2Burl.png"><br>

Sunucuya gönderilen değerler url'de gözükmez.Burp'e bağlayarak devam edelim.Değerlerimizi aynı şekilde kursad:kursad olarak yolladık.POST isteği aşağıdaki gibidir.<br>

<img src="https://1.bp.blogspot.com/-O6YJyTpU3GA/XxhJnBvj7mI/AAAAAAAAAcA/hnWWmncT9VE6tgYj0h-k5yYt7E27vwnUACNcBGAsYHQ/s1600/post%2Burl%2B2.png"><br>

<h1kursad</h1> şeklinde parametrelerimizi değiştirip yolladığımızda sonuç elde etmiş olacağız...<br>

<img src="https://1.bp.blogspot.com/-f-I1f9TvZ_I/XxhJnMehnyI/AAAAAAAAAcE/0BSB3xDbjzIAlzioPCV7LVbyPjl0bkMpgCNcBGAsYHQ/s1600/post%2Burl%2B3.png"> <br><br>


Diğer POST örneğimizde aynı GET örneği gibi bir tık önlem alınmış.Tekrardan URL encode ile denememizi yapalım ve busefer hackbar üzerinden görelim.Get ve Post arasında manipüle ederken pek bir fark yoktur.<br>

<img src="https://1.bp.blogspot.com/-wIFDMmGMvFw/XxhKpRe0aAI/AAAAAAAAAcQ/syqnpzOA-Ws9EFVHa8GTi7IHjHSpfJR_QCNcBGAsYHQ/s1600/post%2Bmedium%2Bencode.png"><br><br><br>


<p style="color:yellow;">C) HTML Injection Stored</p><br>

Stored HTML Injection durumunda payloadlar web serverda saklanır.Bu türde giriş ekranı oluşturulabilir, kullanıcıyı kandırmak amaçlı kod enjekte edilebilir.Bwapp örneğine baktığımız zaman bloğun kullanıcılar için yorum veya mesaj gönderebildiği bir ekran görüyoruz.Burda olay tamamen sizin hayal güvünüze kalmış nasıl ilerleyeceğiniz nasıl bir senaryo çizeceğiniz vs.Temel HTML Injection denemesi yapalım.<br><br>

<img src="https://1.bp.blogspot.com/-RDenAP8abBc/Xxk_JTF5hEI/AAAAAAAAAcc/82cwAgfDlJAY0R-FNks0qt1KRhPMdUHCgCNcBGAsYHQ/s1600/yeni%2Bstored%2B1.png"><br>

deneme yazarak yolladığımızda gözüktüğü üzere entry kaydedildi.Şimdi ise html taglarımızı kullanarak bir deneme yapalım.<br>

<img src="https://1.bp.blogspot.com/-hfkKi6x6btw/Xxk_qDT7hwI/AAAAAAAAAck/voLp2Rf0evAbduEa1BkdYd5OLt-4U09XQCNcBGAsYHQ/s1600/yeni%2Bstored%2B2.png"><br>

şeklinde sonuçaldık.Dediğim gibi seneryo size kalmış  mesela bir form oluşturup kullanıcı adı ve şifrede alabilirsiniz.Basitçe göstermek gerekirse ; <br>

<img src="https://1.bp.blogspot.com/-hqLaJktx-K8/Xxk_2Ffxc9I/AAAAAAAAAco/89Q3FEhblHgVgMDwUs31woYu9V7qwXZTACNcBGAsYHQ/s1600/yeni%2Bstored%2B4.png"><br>
<img src="https://1.bp.blogspot.com/-621aFRuYTlE/Xxk_3i4GJpI/AAAAAAAAAcs/WtKSMPVNlB0BhJFK9tQjg_1kmvV3SLMkgCNcBGAsYHQ/s1600/yeni%2Bstored%2B5.png"><br><br>

Basit şekilde HTML Injection nedir ne değildir ondan bahsettik.Özellikle bayadır popüler Bug bounty programlarında  oldukça  sık rastlanan ve basit olan bir zafiyettir.








