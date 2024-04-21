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



Cyberpanel üzerinde bir sürü özel ayar bulunmakta. Bu yazımızda sadece temel olarak anlatımıştır. Çok yakında daha detaylı anlatılmaya devam edecektir.

Okuduğunuz için teşekkürler.

