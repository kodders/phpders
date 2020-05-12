[//]: # "Title: MacOS"
# MacOS'a PHP geliştirme ortamı kurulumu

Mac'te PHP yazmaya başlayalı çok olmadı, o yüzden çok araştırma fırsatım da olmadı açıkçası, ancak reddit'te, forumlarda vs gördüğüm kadarıyla genelde kolay Laravel siteleri kurmak adına Laravel Homestead veya Laravel Valet kullanılıyordu, Laravel Homestead sanal makina tabanlı olduğu ve benim de PHP geliştirme için sanal makina kullanmaya pek niyetim olmadığı için Laravel Valet'i incelemeye başladım. Windows'ta kullandığım Laragon'a işlerimi kolaylaştırmak adına ve mantıkça en yakını bu geldiği için bunu kullanmaya başladım. Sizlere de o yüzden bunun kurulumunu anlatmak istiyorum.

Google'da yaptığım basit bir "macos php development" araması sonucu karşıma şunlar çıktı:

- **Homestead**: Sanal makina kurmak gerektiği için pek sıcak bakmadım. Tamam, bilgisayarınızı bu yöntemle temiz tutabilirsiniz, ancak aynı anda iki işletim sistemi kullanıyor gibi olmak ve sistem kaynaklarımın bölünmesini istemedim.
- **MAMP Server**: https://www.mamp.info/en/mamp/mac/ sitesine baktığımda en çok kullandığım klasörleri local domain'e çevirme olayını göremedim, ve paralı olduğuna göre bedavasında çoğu özelliği kısıtlanmıştır diye bir önyargıyla baktığım için kullanmadım.

Geriye kalan çözümler de hep aynı kurulum adımlarıyla Homebrew'i, PHP'yi, MySQL'i, NGINX'i, dnsmasq'ı kurup ortamı hazırlıyordu. Madem bunları zaten kuracağım, doğrudan Laravel Valet'le başlayayım dedim.

## Laravel Valet

Adından anlaşılacağı üzere kolayca kullanılabilecek bir Laravel ortamı hazırlamak  için tasarlanmış, ancak sadece Laravel ile kullanılacak diye bir kaide olmadığı için, Laravel'in de PHP ile yazılmış bir program olduğu düşüncesiyle bunu kurmaya karar verdim. 

Nasıl kurulduğunu öğrenmek adına, https://laravel.com/docs/6.x/valet sitesini ziyaret ettim, ve tanımını okudum: (Türkçe çevirisini ekliyorum)

> Valet, Mac minimalist'leri için bir Laravel geliştirme ortamıdır. Vagrant içermez, `/etc/hosts`dosyası içermez. Hatta local tunnel kullanarak sitelerinizi dışarısıyla paylaşabilirsiniz. Evet, bizim de hoşumuza gidiyor.
>
> Laravel Valet Mac'inizi her zaman [Nginx](https://www.nginx.com/)'i makinanızı başlattığınızda arkaplanda çalıştıracak şekilde ayarlar. Daha sonra Valet, [DnsMasq](https://en.wikipedia.org/wiki/Dnsmasq) kullanarak `*.test` domaininden gelen her isteği local makinanızda kurulu sitelerinize yönlendirir.
>
> Başka bir deyişle, aşağı yukarı 7 MB RAM kullanan çarpıcı şekilde hızlı bir Laravel geliştirme ortamı. Valet, Vagrant veya Homestead'in tüm özelliklerine sahip değildir, ancak, eğer esnek temellere sahip, aşırı derecede hızlı bir ortam arıyorsanız, veya düşük RAM'e sahip bir makinada çalışıyorsanız, size muhteşem bir alternatif sunar.

Ve windows'ta kullandığım Laragon'un sahip olduğu özelliklerin çoğuna sahip olduğunu gördüm (arayüz hariç, onun yerine komut satırı kullanıyor) ve kullanmaya karar verdim.

Dökümantasyonda yazdığı kurulum aşamalarına riayet edip aşağıdaki sırayla uygulamaları kurdum:

1. [Homebrew](#1-homebrew-kurulumu)
2. [PHP](#2-php-kurulumu)
3. [Composer](#3-composer-kurulumu)
4. [Laravel Valet](#4-laravel-valet-kurulumu)



### 1. Homebrew kurulumu

[Homebrew](https://brew.sh), ya da kısaca brew, MacOS için komut satırından program yüklemeye yarayan, MacOS'un en çok kullanılan paket yöneticilerinden biridir. Kurulumu ise oldukça basittir: 

Finder > Applications > Utilities > Terminal.app yoluyla, ya da Cmd+Space tuşuna basarak Spotlight açılarak Terminal.app çalıştırılır. Bu terminalde:

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)" 
```

komutu çalıştırılarak kurulum gerçekleştirilir. Kurulumun başarıyla gerçekleştirildiğini anlamak için terminal'e `brew -v` yazdığınızda:

```shell
Homebrew 2.2.10
Homebrew/homebrew-core (git revision c57ea; last commit 2020-03-18)
Homebrew/homebrew-cask (git revision 26cb8; last commit 2020-03-19)
```

şeklinde (ya da daha üst versiyonlara sahip) bir çıktı almalısınız.



### 2. PHP & MySQL kurulumu

Homebrew'i kurduktan sonra işimiz kolaylaştı, sadece 

```bash
brew install php
brew install mysql
```

yazarak PHP ve MySQL'in kurulumunu gerçekleştirebiliriz.



### 3. Composer kurulumu

[Composer](https://getcomposer.org), PHP için bir paket yönetim sistemidir. İleride *Symfony*, *Laravel*, *CakePHP* ya da *CodeIgniter 3* gibi frameworkler kullandığınızda çoğu kodun daha önceden yazılmış olduğu ve size paketler halinde sunulduğunu göreceksiniz. Örneğin, sitenize bir üyelik sistemi eklemek için, bir forum eklemek için sağda solda çok yıldız almış paketler arayacaksınız, ve muhtemelen bir çok kişinin katkı sağladığı, yılların birikimine sahip kod parçasını sitenize eklemek 15-30 dakikanızı alacak.

Kurulumu Windows'taki kadar kolay değil, ama yine de kolay. Tekrar bir terminal açıyoruz ve sırasıyla şu komutları çalıştırıyoruz: 

```shell
cd ~
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/
sudo chmod 755 /usr/local/bin/composer.phar
echo 'alias composer="php /usr/local/bin/composer.phar"' >> ~/.bash_profile
source ~/.bash_profile
```

Sırasıyla şu işleri yapıyor bu komutlar:

1. Kullanıcı ana dizinine geçiyoruz

2. `composer.phar` dosyasını indiriyoruz

3. Her yerde `composer` yazdığımızda bu programın çalışması için `composer.phar` dosyasını `usr/local/bin` klasörüne taşıyoruz.

4. Dosyanın izinlerini çalıştırılabilir şekilde olması için tekrar düzenliyoruz.

5. `composer` komutunu tanımlıyoruz, uzun uzadıya 

   ```shell
   php /usr/local/bin/composer.phar
   ```

   komutunu yazmaktansa bunu bir _alias_ olarak `composer` şeklinde kısaltıyoruz.

Bu adımları gerçekleştirdikten sonra terminal'e `composer` yazarak 

```shell
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.9.3 2020-02-04 12:58:49
...
```

şeklinde bir çıktı alıyorsak _Composer_ kurulumunu başarıyla tamamlamışızdır demektir.



### 4. Laravel Valet Kurulumu

Şu komutu kullanarak Laravel Valet'i kuruyoruz:

```bash
composer global require laravel/valet
```

Ve Valet'in sistemi konfigüre etmesini sağlamak adına 

```bash
valet install
```

komutunu çalıştırıyoruz. Hepsi bu kadar.



## Laravel Valet Kullanımı

Valet'i kurduk, tamam iyi güzel de, şimdi ne yapacağız? Dosyaları nereye koyacağız, hangi adrese gittiğimizde dosyalar çalıştırılıp çıktıları ekrana basılacak, başka bir ayar yapmamız gerekiyor mu? Bu sorulara cevap vermek için Valet'in komut satırına bir göz atalım. Bilmemiz gereken (ve muhtemelen bir daha kullanmadığınız için unutacağımız) önemli komutlar:

#### `valet help` 

Komutlar ile ilgili bilgi almak için kullanılır. Örneğin `valet help start`  komutuyla `valet start` komutu hakkında bilgi sahibi olabilirsiniz.

#### `valet link` ve `valet links` 

Bu komutla istediğiniz bir klasörü valet üstünde kaydettirip, o klasörün içeriğini de bir site gibi gösterebilirsiniz. Çoğul olan hali ise link ile kaydedilmiş klasörleri ve ilgili URL'leri listeler. 

Örneğin, masaüstünde *yeniwebsitem* isimli bir klasör oluşturduk, bu klasörün içine web sitemizde yayınlayacağımız dosyaları hazırladık. Ve bu websitesini http://yeniwebsitem.test adresinde göstermek istiyoruz. O zaman yapmamız gereken şey:

```shell
MacBook Pro:~ myuser$ cd ~/Desktop/yeniwebsitem
MacBook Pro:yeniwebsitem myuser$ valet link
```

komutlarını çalıştırmaktır. Gerisini Valet halledecektir. Daha önce bu yöntemle parkettiğiniz siteleri görmek içinse şöyle bir komut giriyoruz:

```bash
MacBook Pro:~ myuser$ valet links
+--------------+-----+--------------------------+-------------------------------------+
| Site         | SSL | URL                      | Path                                |
+--------------+-----+--------------------------+-------------------------------------+
| yeniwebsitem |     | http://yeniwebsitem.test | /Users/myuser/Desktop/yeniwebsitem  |
+--------------+-----+--------------------------+-------------------------------------+
```

#### `valet park` ve `valet parked`

Bu komutla da istediğiniz bir klasörün tüm alt klasörlerini birer siteymiş gibi davrandırabilirsiniz.  `valet parked` komutuyla da tüm park edilmiş klasörlerin altında sunumu yapılan sitelerin bir listesine ulaşabilirsiniz.

Örneğin, masaüstünde _Sitelerim_ adı altında bir klasörünüz var, ve _Site1_ ve _Site2_ isimli iki alt klasörünüz mevcut. Bu siteleri ve bu klasöre daha sonradan eklenecek klasörleri sunmak istiyorsunuz. O zaman yapmanız gereken şey:

```shell
MacBook Pro:~ myuser$ cd ~/Desktop/Sitelerim
MacBook Pro:Sitelerim myuser$ valet park
```

Bu komutla _Sitelerim_ klasörünü bir site yuvası haline getirdik. Buraya eklenen tüm klasörler, sunucuda bir site olarak otomatik kaydettirilecek. 

```shell
MacBook Pro:~ myuser$ valet parked
+------------+-----+----------------------+----------------------------------------+
| Site       | SSL | URL                  | Path                                   |
+------------+-----+----------------------+----------------------------------------+
| Site1      |     | http://site1.test    | /Users/myuser/Desktop/Sitelerim/Site1  |
+------------+-----+----------------------+----------------------------------------+
| Site2      |     | http://site2.test    | /Users/myuser/Desktop/Sitelerim/Site2  |
+------------+-----+----------------------+----------------------------------------+
```

####   `valet tld` komutu

http://yeniwebsitem.test şeklinde eriştiğimiz sitelerimize bundan sonra http://yeniwebsitem.ironman şeklinde erişmek istiyorsak, bu komutla Valet'in kullandığı TLD'yi (Top Level Domain) değiştirebiliriz. Bunu yapmak için `valet tld ironman` komutunu yazmak yeterli olacaktır. Ancak hali hazırda online olarak kullanılabilen TLD'lerden (com, net, org, info vs.) kullanamayabilirsiniz.

Şimdilik başlangıç adına bu bilgiler bize yetecektir. Daha fazla detay için [Laravel Valet](https://laravel.com/docs/6.x/valet) adresine bakabilirsiniz. 

Kendinize sonraki dersler için yukarıdaki komutlarla bir alan hazırlamayı unutmayın!

