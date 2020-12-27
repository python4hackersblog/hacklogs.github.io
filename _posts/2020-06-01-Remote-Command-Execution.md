---
title: Remote Command Execution
description: Remote Command Execution
layout: Yazılar
permalink: remote-command-execution
---

**Command Execution** yani Komut Çalıştırma zaafiyetleri bir zaafiyeti barındıran script üzerinden saldırganın sistemde dilediği şekilde kod çalıştırmasına sebep olmaktadır. Bu zaafiyet script üzerinden işletim sistemine çağrı yapar yani **cmd-shell** komutlarını çalıştırır, bu yönüylede **RCE(Remote Code Execution)**'den farklıdır. Scriptte herhangi bir denetleme  olmadığından zafiyet kaynaklanmaktadır.

Öncesinde kısaca **Remote Code Execution** zafiyetinden bahsedeceğim.Sonrasında **Command Execution** ile devam edeceğiz.
Birçok zafiyetin sömürülmesindeki amaç hedef sistemlerde root düzeyinde yetkiye ulaşmaktır.Öncesinde düşük seviyeli bir erişim elde eden saldırgan root düzeyine ulaşmak için çeşitli teknikler denemeye devam eder.

**Remote Code Execution** zafiyeti script üzerinden kod çalıştırmamıza olanak sağlar.**Eval()** fonksiyonu ve bu fonksiyon gibi hareket eden fonksiyonlar zafiyetin oluşmasında önemli rol oynar.Herhangi bir kısıtlama görmemiş inputlar, dosya yükleme kısımları vs. zafiyete sebep olmaktadır.

<br>
**Rce** sürecini basitçe şöyle gösterebiliriz.

<p style="color:yellow;">Saldırgan---A----> Kod -----B----> Web Site ------C-----> Sunucu------D-------> Çıktı </p> 

**A)**  Saldırgan zararlı kodlar yazar.

**B)**  Saldırgan yazdığı zararlı kodları enjekte eder.

**C)**  Zararlı kodlar çalıştırılır.

**D)**  saldırganın ekranında çıktılar gözükür.

<br>

**Command Execution**, zafiyet barındıran script üzerinden direkt işletim sisteminde **cmd/Shell** komutları çalıştırmamızı sağlar.Bu yönüyle **Remote Code Execution** ile aynı değildir.**DVWA**,**BWAPP**,**Web For Pentesters** gibi lablar üzerinden bol örnek yaparak anlatımlarımıza devam edelim.


**DVWA Command Execution**
İlk örneğimizi inceleyelim.Kullanılan kod parçası kullanıcılar tarafından güvenli olmayan verileri direkt sisteme geçirdiğinden **command execution** saldırısı mümkün olmaktadır.

Kaynak koda bir göz attığımızda $target= kısmında  ip değerinin herhangi bir doğrulamaya tabi tutulmadığını görebiliyoruz buda bize ip adresinden başka şeylerde ekletebileceğimiz anlamına gelmektedir...


<img src="https://1.bp.blogspot.com/-eHJssIlXlQ8/XtVgNVlh-7I/AAAAAAAAAXg/ujB8KeF5rUEQNJktvzPd5qbq9v4I87QvwCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/0.png" width="500" height="400">


<img src="https://1.bp.blogspot.com/-azQaQ5fmfTU/XtVgNSoQ6gI/AAAAAAAAAXk/aw7pG0pFbJECwpc7-cyh8D4WubMbCpepACEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/1.png" >




Yukarıda bir metin kutusu görüyoruz bu metin kutusuna ip adresi yazdığımızda bu ip adresine (yukarıdaki kaynak koddan da anlaşıldığı üzere **("$cmd = shell_exec( 'ping  -c 3 ' . $target );")** 3 tane ping paketinin gittğini aynı zamanda ping istatisklerini **(3 paket iletildi, 3 paket alındı,% 0 paket kaybı, süre 1998 ms )** aşağıda görüyoruz…


**Shell_exec** içerisindeki ping komutu server tarafında çalışır ve **echo** ile ekrana bastırılır.**–c** parametresi iled e 3 paket gönderilir.**$target** değişkenide veriyi tutar.Kodları tek tek okumak her zafiyeti anlamak için güzel bir yöntemdir. Bu basit örneğimizde de herhangi bir kontrol mekanizmasının olmadığını rahat bir şekilde anlıyoruz.Hal böyle olunca ilgili metin kutusunda ekstra operatörler ile farklı komutlar çalıştırabilmemize imkan sağlanıyor.Özel karakterlere birazdan değineceğiz..
<br><br><br>

<img src="https://1.bp.blogspot.com/-Wq_V-esttT8/XtVgO57cx6I/AAAAAAAAAX4/b8UdS5l-Smk76W2OcwsNIcBhB3k9MZ-qQCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/2.png">

Buradan da anlıyoruz ki sunucu tarafında cmd/Shell komutları çalıştırılıyor.
<br><br><br>

Daha önceden de dediğimiz gibi bir denetleme mekanizması bu tarz sistemlerde oldukça önemlidir.Zafiyetin zor bulunmasının sebebide webmasterların bu tarz kod parçacıklarını çok nadir kullanmalarıdır. Yani siz kolaylaştırmadığınız sürece zordur bulmak :). 

Sistemde komut çalıştırma fonksiyonlarından kaçınmak, uygulamaları yaparken çok dikkatli olmak, fonksiyonları ve sistemleri iyi tanımak, dinamik verileri dikkatli olarak elden geçirmek, ekstra veri doğrulamaları eklemek vs. zafiyetten korunmak için söyleyebileceğimiz bazı önlemler. 
<br><br><br>
Örnek olarak PHP’ script dilinde de sistem shell çağrısı yapan fonksiyonlardan bazılarını inceleyebiliriz :
<br><br>

<h3 style="color:yellow;">exec() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.exec.php">exec() İncele</a>
<br><br>
<h3 style="color:yellow;">Shell_exec() Fonksyionu</h3>

<a href="https://www.php.net/manual/tr/function.shell-exec.php">shell_exec() İncele</a>
<br><br>
<h3 style="color:yellow;">proc_open() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.proc-open.php">proc_open() İncele</a>
<br><br>
<h3 style="color:yellow;">system() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.system.php">system() İncele</a>
<br><br>
<h3 style="color:yellow;">popen() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.popen.php">popen() İncele</a>
<br><br>
<h3 style="color:yellow;">passthru() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.passthru.php">passthru() İncele</a>
<br><br><br><br>

Bu fonksiyonları katılaştırmak için kullanılabilecek 2 fonksiyonu da inceleyebiliriz :
<h3 style="color:yellow;">escapeshellcmd() Fonsiyonu</h3>

<a href="https://www.php.net/manual/tr/function.escapeshellcmd.php">escapeshellcmd() İncele</a>
<br><br>
<h3 style="color:yellow;">escapeshellarg() Fonksiyonu</h3>

<a href="https://www.php.net/manual/tr/function.escapeshellarg.php">escapeshellarg() İncele</a>
<br><br><br><br><br>
Kaldığımız yerden devam edelim kodda herhangi bir karakter filtreleme özelliği olmadığından “;” ile komutları birbirinden ayırabiliriz:

<br>
<img src="https://1.bp.blogspot.com/-j6O9xA5PYN4/XtVgPN8BTII/AAAAAAAAAX8/hFYGG2IlZzsEtLk9khwKZ1gmDotICYlIACEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/3.png">
<br><br>
<img src="https://1.bp.blogspot.com/-DjOboR2rx2I/XtVgPuLBy7I/AAAAAAAAAYE/0VPwIS6pFaAVv1I2eYo3uSiBkMOJrx3bwCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/5.png" height="550" width="600">
<br><br><br><br><br><br>

Diğer örneğimizi incelemeye gecelim ve kaynak kodumuza bakalım :
<br>
<img src="https://1.bp.blogspot.com/-DSHKCwyRyTo/XtVgP_OR5DI/AAAAAAAAAYI/hKQ1rfB2aYUB5PpN1Ep4yAi6N0AOI_6hACEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/6.png">
<br><br>
Önceki kodumuza baktığımızda filtreleme yoktu istediğimiz şekilde at koşturuyorduk.Bu kodu incelediğimizde ise gözümüze 8. satırdaki oluşturulan dizi çarpıyor, basit blacklist muhabbeti : 

<br>
```
 // Remove any of the charactars in the array (blacklist).
    $substitutions = array(
        '&&' => '',
        ';' => '',
    );

```

<br><br>
Sonrasında bu dizinin kullanıldığı kısıma bakıyoruz :

<br>

```
$target = str_replace( array_keys( $substitutions ), $substitutions, $target );

```
<br>

Burada **str_replace()** fonksiyonunun kullanıldığını görmekteyiz peki ne işe yarar bu **str_replace()** fonksiyonu ?
<br>
-Bu fonksiyon bir string içerisinde bizim istediğimiz karakterleri bularak değiştirmemizi sağlıyor. Detaylı örneklemeler ve anlatıma aşağıdan ulaşabilirsiniz...

<br>
<a href="https://www.php.net/manual/tr/function.str-replace.php">str_replace() İncele</a>
<br><br><br>
Yani burada yapılan işlem dizi içerisinde belirtilen  karakterleri **(“&&” , ”;”)**  silerek $target değişkenine atıyor.Biz önceki **“;”** karakterini kullanmıştık komutumuzu ayırmıştık tekrar kullandığımzda Shell_exec fonksiyonuna kodumuz ulaşmayacak ve ekranda hiçbir çıktı olmayacaktır.Bunun için **“|” PIPE** özel karakterini kullanarak sonuca ulaşabiliriz :
<br><br>
<h3 style="color:yellow;">"|" PIPE</h3>
<br>
Kullanımı şu şekildedir  **127.0.0.1| cat /etc/passwd**  örneğimizde deneyelim;
<br>
<img src="https://1.bp.blogspot.com/-QriY8bGH7Hw/XtVgQQJ9gnI/AAAAAAAAAYQ/Hj8IpxGOaUcSqrmzRYO3jbndNbJ3Z9rYwCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/8.png" height="500" width="600">
<br><br>
Başarılı bir şekilde komutumuz  çalıştı. Ayrıca **PIPE** karakterini şu  **“||”** şekilde de kullanılabiliriz.
Yukarıdaki basit blacklist muhabbetinden ötürü **“&&”** karakteri filtreli biz eğer şöyle bir şey yazarsak **127.0.0.1&cat etc/passwd** sonucumuz yine başarılı olacaktır. 

Yine aynı şekilde mantık basit bir mantık yürüterek şu şekilde bir kullanım ilede sonuç alabiliriz: **127.0.0.1&;& cat /etc/passwd**  basit bir filtrelemeyi basit bir şekilde bypass edebiliyoruz.

<img src="https://1.bp.blogspot.com/-TL8TW7mmYCw/XtVgQ-8AUmI/AAAAAAAAAYU/z8E1PiD05kMxnI9g9FnfUmKP5Y68mFpOgCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/9.png" height="500" width="600">
<br>
<img src="https://1.bp.blogspot.com/-oTsuDcBkuiw/XtVgNOeGh_I/AAAAAAAAAXc/EhHgGAol14w0cgktMgTPWAxtdHpjr0TfwCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/10.png" height="500" width="600">
<br><br><br>

<h3 style="color:yellow;">echo ">" Karakteri</h3>
echo nun ne işe ayradığını hepimizin biliyoruzdur. Bu bizim nasıl işimize yarar ona değinelim.**127.0.0.1&cat /etc/passwd > 0xkursad.php** diyerek çıktıyı **0xkursad.php** dosyası oluşutup kod çalıştırabiliriz.Görüldüğü üzere başarılı şekilde dosyamız oluşturuldu.

<br>
<img src="https://1.bp.blogspot.com/-WgeZFaSYB3w/XtVgON7GVbI/AAAAAAAAAXw/R4pySlcBankEdq7JJgicMUcra51A8XMFQCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/13.png">
<br>
<img src="https://1.bp.blogspot.com/-wyqFYtezvQ4/XtVgOoQ2PAI/AAAAAAAAAX0/i-A8SfYuTAopyyMPbINMj5KWm1tDhrdiQCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/14.png">
<br><br><br>

**High** level örneğimiz ile devam edelim  ve kaynak kodumuzu inceleyerek devam edelim:
<br>

<img src="https://1.bp.blogspot.com/-c0P65_NoGyE/XtVgN2Ry50I/AAAAAAAAAXo/nB2U8CLpV7giTQa4ajBzBN6NimBVynsmgCEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/11.png">
<br><br>

Burada gözümüze çarpan  fonksiyonları inceleyelim :
<br><br>

<h3 style="color:yellow;">Stripslashes(string) Fonksiyonu</h3> = ters “\” slaş karakterlerini kaldırır.
<br>
<h3 style="color:yellow;">explode(separator,string,limit) Fonksiyonu</h3> = değişken içerisindeki boşluk ve noktolama işaretlerine göre ayırma işlemi yapar ve bunu dizi olarak atar.
<br>
<h3 style="color:yellow;">is_numeric() Fonksiyonu</h3> =Dizenin sayısal bir dize olup olmadığını kontrol eder, sayısal ise true değil ise false değerini döndürür.
<br><br>

Buradaki kodumuz diğer kodlarımazla kıyaslanamayacak kadar güvenli , diğer örneklerimizde ip adresi doğrulaması yoktu mesela ilk kodumuzda şöyle bir kullanım yapsaydık :

<p style="color:yellow">1;  cat /etc/passwd</p>

Yine sonuca ulaşmış olacaktık çünkü herhangi bir kullanıcı girişi doğrulaması yoktu.
<br><br>
İkinci örneğimize bakacak olursak ve şöyle bir kullanım yaparsak :

<p style="color:yellow;">1&cat /etc/passwd</p>

Yine sonuca ulaşmış olacaktık çünkü yine herhangi bir kullanıcı girişi doğrulaması yoktu girdiğimiz değerin IP biçiminde olup olmaması kontrol edilmiyordu.İlla 1 rakamı değil bunun yerine karakterde girebiliriz.

<p style="color:yellow;">kursad&cat /etc/passwd</p>

Böyle bir kullanım ilede sonuca ulaşabilecektik.

En son ki örneğimize göz attığımızda bu bahsettiğimiz zayıflıklara karşı önlem alındığını görüyoruz :

<br>
<img src="https://1.bp.blogspot.com/-3DsV1veouhU/XtVgOP54NDI/AAAAAAAAAXs/4xdnMQXOr_oc8d15rwBKuy7sik4lNLusACEwYBhgLKs0DAL1OcqwVXeBohNIIs25TlO06GVcF4RvlTn20g4VEoj10qyjKiDUa2V9ezVoKIVwe5PBRp100eZgXgW5dmT3SNDneW8r8fZlKvWOdBh-4D-z2BkXUeMCaNxxk9DLgEp1DmLr9RQAls0Ygn10fPRcz2gW80f7Ka7-yydcrLWzf8k2kdwwadK-cH3lhcFeeYaFncoD85xJKnIWfL5Pw1fmNd0-pcQoLI-3sb_8H0Um_jfrSPB62b4B0GNHX9y2ahKoHCapyDYeWWebxg0lfpim2JcuwNrfarCXMqbZE_1eNob6pB0B6YWjNRw09uJrY0lu2OFHrBhtp-xlTIinHQzbl9nK3qGvG8hPK4cuKGm2tPinO-e5UPG7HVPswVeCxKdxWDylqJJMLECHihev5UhokaEzUWP5JA6SkS9OuZ61w-6NnFEY72SkGgHu6miphNbGkpGixEmCKOKBdjI7QeLuV4jJ0BOQyGSn4fYXmcX1J9uK_r0AkFRkoccMOdskG1Sw3MEAmZmHA3qLGqJ2Bh9QHlPxe3h73PsX5Z95N6vwd0fKX8EnmWKZ3PsniZcgCWBbZHc18S0iTRH3uY-j3BysOkRqNtzXK_nwlQsIZ7tUwq8XV9gU/s1600/12.png">
<br><br>
Kullanıcı giriş kontrolünün olduğunu görmekteyiz, ip adresi harici biçimdeki her şeyi algılayarak engelliyor.
Genel anlamda aklıma gelen belli başlı şeyler bunlar.Burada olduğu gibi her şey basit olmuyor gerçek hayatta her zaman böyle çıktı alamazsınız **Blind** olma durumlarını da göz önünde buldurmalısınız.Bunuda ilerleyen günlerde anlatmayı düşünüyorum.Mantık genelde hep aynı zafiyete hakim olmak, kodları güzel bir şekilde yorumlamak.Özel karakterlerden birini kullanı sonuç vermedi diyerek kestirip atmamalı ne varsa ne olabilirse akla gelen her teknik kullanılmalı.







