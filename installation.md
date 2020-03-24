# PHP'yi bilgisayarımda nasıl çalıştırabilirim?

PHP yazmak için MAMP, LEMP, LAMP, WAMP vs ileride sağda solda duyacağınız ve işlerinizi aşırı derecede hızlandıracak toplama programlar halinde geliştirilmiş stack'ler mevcuttur ve bütün ihtiyacınız olan programları ayrı ayrı kurmak yerine bunlarla başlamanız, neyi ne zaman öğrenmeniz gerektiği açısından çok önemli bir olay. 

Örneğin, tutup PHP öğrenecek bir insan, bence, NGINX'in ya da MySQL'in tüm özelliklerini önceden öğrenmez. İhtiyacı olduğu zaman sadece neyin ne iş yaptığını bilse, neyi yapabileceğini o doğrultuda araştırmaya girer ve çözüm için nereye bakması, hangi keywordleri kullanması gerektiğini bilir. Bu, programlama konusunda çok önemli bir meziyettir. Neyi nasıl nerede ve neleri kullanarak arayacağını bilmek. En hızlı çözüm, en hızlı aradığını bulan, en doğru çözüm ise en çok yol yordam bilen (tecrübe) tarafından sağlanır. Bu ikisini bir arada bulunduran kişiye ise "iyi programcı" denir.

Benim kullandığım işletim sistemlerine göre en hızlı başlangıçları sağlayan stack'lar şunlar:

1. Windows için **Laragon**
2. MacOS için **Laravel Valet**
3. Linux için **LEMP stack**



## Windows kurulumu

Windows'ta PHP kodlamaya ilk başladığım zamanlarda [**EasyPHP**](https://www.easyphp.org/), daha sonraları ApacheFriends'in [**XAMPP**](https://www.apachefriends.org/tr/index.html)'ı, ve en son karar kıldığım [**Laragon**](https://laragon.org/) hazır PHP stack'lerini kullandım. Hepsinin kurulumu oldukça basit, istediğiniz konfigürasyonu ayarlayabiliyorsunuz, örneğin ben Apache değil de NGINX kullanmak istiyorum diyorsanız ona göre dosya indiriyorsunuz ya da programın arayüzünden birini kapatıp diğerini açıyorsunuz vs, ancak ilk **Laragon**'u keşfettiğimde çok hoşuma giden bir özelliği vardı, ki hala o yüzden kullanıyorum, server kök klasörünün (bu konuya ileride tekrar değineceğim) içine örneğin _yenisitem_ isminde yeni bir klasör açtığınızda, otomatik olarak _yenisitem.dev_ adlı bir sanal websitesi oluşturuyor ve bu URL'ü kullanarak geliştirme yapabiliyorsunuz.

https://laragon.org/download/ adresinde Laragon size seçmeniz için 3 seçenek sunacak:

- **Laragon Full**: Apache 2.4, Nginx, MySQL 5.7, PHP 7.2, Redis, Memcached, `Node.js 11, npm, yarn, git`,… bütün sunabildiği paketleri içine dahil etmiş ve toplam boyut 130MB olmuş.

- **Laragon Lite**: Full paketten `Node.js 11, npm, yarn, git` özelliklerini çıkartmış ve kurulum boyutunu 85MB'a indirmiş. Çıkartılan özelliklerle bizim bir işimiz yok, ayrıca bunların her birinin ayrı sitelerinde setup dosyaları mevcut. Daha sonra ihtiyacınız olduğunda da indirebilirsiniz.

- **Laragon Portable**:  İndir ve kullanmaya başla şeklinde paketlenmiş, sağa sola kolayca taşıyabileceğiniz PHP 5.4 ve MySQL 5.1 kurulumlarını içerir. Sitesinde PHP'ye başlamak için güzel bir paket olarak tanımlanmış, daha sonrasında PHP versiyonuna ihtiyacınız olduğunda kendiniz ekleyebilirsiniz şeklinde de açıklama yapılmış. 18MB'a düşürmüşler paketi. 

İstediğiniz herhangi birini indirebilirsiniz. Bu dili öğrenmek adına başlangıçta bir sorun oluşturmayacaktır, ancak güncel kalmak adına PHP7 ve üzeri herhangi bir versiyonu seçmeniz, ileride anlatılacaklarda sorun yaşamamanız için önemli olabilir.

