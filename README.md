# Ubuntu Cyberpanel Kurulumu



![resim_2024-04-22_020757047-removebg-preview](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/5b86508d-691a-47bf-8592-413101f5e95d)


Merhaba, bu yazımızda Cyberpanel nasıl kurulur ve kullanılır onu anlatacağım. Cyberpaneli kurma sebebim aslında kolaylık açısından ziyade ücretsiz olmasıydı. Plesk ve Cpanel gibi yazılımlar tabi ki daha kaliteli ve güvenlikli sistemler fakat ücretleri biraz pahalı gelebiliyor. Cyberpanel kendi içerisinde bir Mail Server barındırıyor. IMAP ve POP servisi olarak Dovecot, SMTP olarak da postfix kullanılmıştır. Bu yazımızda bunlar nasıl kullanılır anlatacağız. 

## Kurulum

Aşağıdaki kodları sırasıyla yazıyoruz.

```
sudo apt update
sudo apt install curl wget
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
sudo su - -c "sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)"
```


Kurulum sağlanırken sizlere bazı sorular soracaktır. Bunları tercihlerinize göre seçebilirsiniz.  Kurulumu tamamen bitmesi biraz uzun sürebilir.


Kurulum tamamlandıktan sonra sizlere bir IP adresi verecektir. Örneğin; 192.168.1.15:8090 adresini tarayıcınıza yazarak giriş sağlayabilirsiniz. Eğer şifrenizi görmediyseniz veya unuttuysanız `adminPass` komutu ile sıfırlayabilirsiniz. Örnek kullanımı aşağıdaki gibidir:

```
adminPass A2e79!*
```

##  Web Sitesi Ayarları

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/d467a8c7-a88c-4d58-bf93-79cddd57c85e)

Sol tarafta bulunan Web siteler >> Web sitesi oluştur seçeneğinden basit bir şekilde yeni bir site oluşturabilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/884550a0-3a55-405c-b5a1-c2a26b2b1092)

Web siteleri >> Website listesi sekmesinden web sitelerinizi yönetebilirsiniz.


Tüm panelleri anlatmanız çok bir anlamı yok. Tek tek girip sizlerde kurcalayabilirsiniz :)




## E-posta Ayarları Ve Yaşanılabilecek Sorunlar 


Sol tarafta bulunan panelden E-posta kısmını görebilirsiniz

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/a38df94a-1d31-467f-9561-8984166415ab)


E-posta oluştur seçeneğine tıkladıktan sonra aşağıdaki gibi oluşturabilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/86b141f1-f202-4659-be92-8e6b788ab7e7)


Aynı başlık altında Webmaile giriş kısmını görebilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/851f8b93-2731-44dc-a161-f0c85f24b01d)


![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/8df144fe-3c98-45e9-a815-00665f338287)


Mail göndermeye çalışırken hata alırsanız sunucunuzda SMTP portlarınız açık olmayabilir. 

Ayrıca yaşanan sorunuz için SSL sekmesi altında mailserver ssl görebilirsiniz. Sekmeden alan adınıza SSL kurarak da bu sorunu çözebilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/f57f8837-e316-4758-a303-db4f4b587fdc)


![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/4e803ec4-40a6-4f58-b147-b6eabe6405e8)



### Mail Logu

Sol tarafta bulunan panelden Günlükler >> E-posta günlüğü sekmesinden log bakabilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/49139a0a-367a-4cfe-baeb-76442a930b12)

#### Örnek Mail Logları

Aşağıda iki farklı Mail logu görüyorsunuz. Birisi başarılı şekilde iletimiş, diğeri ise mail hesabını bulamadığı için bir hata dönmüş.


```
Apr 21 23:02:18 localhost postfix/pipe[19877]: 2352F182EE3: to=<test@ugurcomptech.com.tr>, relay=dovecot, delay=0.44, delays=0.24/0.04/0/0.16, dsn=2.0.0, status=sent (delivered via dovecot service)
```

```
Apr 21 23:04:08 localhost postfix/pipe[19903]: 9DD90182EE3: to=<aaa@ugurcomptech.com.tr>, relay=dovecot, delay=0.39, delays=0.21/0.04/0/0.14, dsn=5.1.1, status=bounced (user unknown)
```


İsterseniz de sunucu üzerinden log bakabilirsiniz.

İlk öncelikle sunucumuzda `cd /var/log/` konumuna gidiyoruz. Burada incelememiz gereken dosya `mail.log` dosyasıdır. Örneğin bir mailin gidip gitmediğini kontrol edeceksiniz. Aşağıdaki komutu yazarak kontrol sağlayabilirsiniz.

```
cat mail.log | grep test@test.com
```


## FTP 

FTP hesabı oluşturmak için sol tarafta bulunan panel üzerinden FTP >> FTP Hesabı Oluştur sekmesinden başarılı bir şekilde oluşturabilirsiniz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/28e53a9b-00a0-4d4c-8feb-80b3fbb274b0)


FileZilla üzerinden bağlanmak için üst tarafta bulunan File >> Site Manager sekmesinden yeni bir site ekleyip ayarları aşağıdaki gibi yapınız.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/8cf7af9d-db4e-45dc-bc04-72bc97a50b50)

Ayarları yaptıktan sonra `Connect` deyip bağlanabilirsiniz.


## User Ve Paket Ayarları


Sol tarafta bulunan Paketler >> Paket oluştur sekmesinden paket oluşturabilirsiniz. Bu sekmede kısıtlamalar koyabilir ve istediğiniz ayarı yapabilirsiniz.


![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/7b24d58a-68f7-4240-8d00-b3e21e81023a)


Sol tarafta bulunan Kullanıcılar >> Kulanıcı oluştur sekmesinden yeni bir kullanıcı oluşturabilirsiniz. Bu sekme üzerinde oluşturmuş olduğunuz kullanının bilgilerini giriyorsunuz. Select ACL kısmından kullanıcımıza vereceğimiz yetkileri seçiyoruz. Siz eğer önceden  ACL oluşturmadıysanız burası boş gelecektir. Sol tarafta bulunan Kullanıcılar >> Create New ACL sekmesidnen yeni bir ACL oluşturabilirsiniz.

Bu sekmeden istediğiniz yetkileri verebilirsiniz. Ben normal bir müşteride olması gereken yetkileri veriyorum. 

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/b1a4febe-b32a-432a-bc27-c9f27c8b7680)



Tekrardan Kullanıcı oluştur sekmesine gelip oluşturacağımız kullanıcımızı oluşturuyoruz.


![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/7cae19f8-6e7d-4841-8805-0c3aa9e927d0)


Şimdi bu kullanıcım için bir web sitesi oluşturacağız. Sol tarafta bulunan panelde Websiteler >> Websitesi oluştur sekmesinden yeni bir site oluşturacağız. 

Önceki adımlarda yapmış olduğumuz işlemleri burada kullandık. Sahip olarak oluşturmuş olduğumuz `catal` kullanıcısını ve paket olarak `admin_user` paketini seçtik. Web sitesini oluştur diyoruz.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/ff538e1a-5587-499f-a17c-a6f5f270441f)


Web sitemiz başarılı bir şekilde oluşturuldu.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/f0e27614-bfc4-4a17-8481-d4d77f16ab03)


Şimdi oluşturmuş olduğumuz Userın hesabına giriş yapıyoruz.


![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/aac75229-3e76-4e68-82c8-7e4bcd1256cc)



Görmüş olduğunuz gibi web sitemiz `catal` hesabında başarılı bir şekilde oluşturulmuştur. Sizlerin paketine vermiş olduğu limit kadar kullanabilmektedir. Örneğin ben bir tane FTP hesabı açma hakkı vermiştim eğer iki tane açarsa hata verecektir. Hadi bunu test edelim:

Başarılı bir şekilde oluşturabildim. Şimdi ikinci FTP hesabını açmayı deneyelim.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/462803e8-eb0d-452b-92b1-0b9eb24500f4)


Görmüş olduğunuz gibi 'Paket için izin verilen maksimum FTP hesabı miktarı aşıldı.' hatası verdi.

![image](https://github.com/ugurcomptech/Ubuntu-Cyberpanel/assets/133202238/9b8faca7-0528-4485-8174-c31c98b32c8f)



## Custom FQDN Ayarları

CyberPanelin Login ekranı <IP_Adresi:8090> veya Snappy Mailin login ekranı bildiğiniz gibi <IP_Adresi:8090/snappymail> adresi ile gelir. Bunları domain ile yayınlamak isteyebilirsiniz. Bunun için ilk öncelikle bir domain veya subdomain oluşturmanız gerekmektedir.
İlgili domaini/subdomaini oluşturduktan sonra Yönet >>  Rewrite Rules seçeneğini seçip aşağıdaki kuralı girmeniz gerekmektedir.

**NOT:** DNS bölgenize gerekli kayıtları girmeyi unutmayınız!

```
webmail  IN A  1.1.1.1 # sunucu ıp adresi

panel  IN  A  1.1.1.1 # sunucu ıp adresi
```


```
RewriteEngine On
RewriteCond %{HTTPS}  !=on
RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R,L]


RewriteEngine on
RewriteCond %{QUERY_STRING} ^$
RewriteRule ^$ https://webmail.serverdomain.com:8090/snappymail? [R=301,L,NC]
```

Buradaki kural Webmail adresinize yönlendirecektir. Bunun aynısını CyberPanel için de uygulayabilirsiniz. Onun kuralı da aşağıdaki gibidir.

```
RewriteEngine On
RewriteCond %{HTTPS}  !=on
RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R,L]


RewriteEngine on
RewriteCond %{QUERY_STRING} ^$
RewriteRule ^$ https://serverdomain.com:8090/ [R=301,L,NC]
```

## Mail Kurulumu Yaparken Yaşanan Sorunlar

Selamlar, öncelikle sunucunuzdaki mail hesaplarınızdan birisini outlook veya başka bir benzeri uygulamaya kurmaya çalıştığınızda hatalar alacaksınızdır. Örnek hata aşağıdaki gibidir.

```
27 22:49:24 localhost dovecot: imap-login: Disconnected: Connection closed (no auth attempts in 0 secs): user=<>, rip=78.190.164.48, lip=193.106.196.59, session=<QFLy1BsXvUFOvqQw>
Apr 27 22:49:24 localhost postfix/submission/smtpd[192196]: warning: hostname 78.190.164.48.static.ttnet.com.tr does not resolve to address 78.190.164.48: Name or service not known
Apr 27 22:49:24 localhost postfix/submission/smtpd[192196]: connect from unknown[78.190.164.48]
Apr 27 22:49:24 localhost postfix/submission/smtpd[192196]: lost connection after EHLO from unknown[78.190.164.48]
Apr 27 22:49:24 localhost postfix/submission/smtpd[192196]: disconnect from unknown[78.190.164.48] ehlo=1 mail=0/1 commands=1/2
```

E-posta sunucusu yöneticileri, zaman zaman e-posta sunucularına gelen bağlantıları izlerken "hostname does not resolve" (alan adı çözünemiyor) hatası ile karşılaşabilirler. Bu hata, gelen bağlantının IP adresi ile ilişkilendirilmiş bir alan adının olmamasından kaynaklanır. Bu durum, e-posta sunucusunun güvenlik politikaları nedeniyle bağlantıyı reddetmesine neden olabilir.

Bu hatanın çözümü, PTR (Reverse DNS) kaydının oluşturulması veya doğru şekilde yapılandırılmasıyla mümkündür. PTR kaydı, bir IP adresinin alan adı ile eşleşmesini sağlar. E-posta sunucuları, gelen bağlantıların güvenilirliğini doğrulamak için PTR kaydını kontrol eder. Sunucunuz için erişmiş olduğunuz IP adresinin sahibi hangi ISP firması ise orayla iletişime geçmeniz gerekmektedir. https://search.arin.net/rdap/ Web sitesinden IP adreslerin sahiplerini görebilirsiniz.















Cyberpanel üzerinde bir sürü özel ayar bulunmakta. Bu yazımızda sadece temel olarak anlatımıştır. Çok yakında daha detaylı anlatılmaya devam edecektir.

Okuduğunuz için teşekkürler.

