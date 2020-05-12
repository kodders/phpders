[//]: # (Title: Linux)
# Linux'ta PHP geliştirme ortamı kurulumu

Linux'ta PHP kurulumu, Windows veya MacOS üzerine PHP kurmaktan biraz daha zor aslında. CentOS için farklı kurulum komutları var, Ubuntu için farklı komutlar var, Alpine Linux için farklı kurulum komutları var, bunların sebebi farklı paket yöneticisi programlarına ve kaynak depolarına sahip olmaları diyebiliriz. 

İlgilenen farklılıkları hakkında araştırmaya devam edebilir. 

Ortak özellikleri ise, hepsinin şu kurulumları içermesi:

- PHP kod çalıştırıcısı (mod_php, php-fpm, php-fcgi, hhvm vs.)
- Web sunucusu (Apache, NGINX vs.)
- Veritabanı sunucusu (MySQL)

Burada CentOS ve Ubuntu için PHP 7.2 versiyonu nasıl kurulur onu anlatacağız.

