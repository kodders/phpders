# CentOS üzerinde PHP geliştirme ortamı kurulumu

Ubuntu işletim sisteminde kurduğumuz programların aynısını burada da kurmamız gerekiyor:

* Web Sunucusu
* PHP kod çalıştırıcısı
* MySQL veritabanı

> **Not:** Bu komutları yetkisiz bir kullanıcı ile çalıştıramazsınız, eğer root erişiminiz ya da sudo yetkili bir kullanıcınız yoksa, öncelikle bunu elde etmeye çalışın.

Öncelikle sistemimize epel-release adlı kaynak depoları eklememiz gerekiyor:

**Centos 6**

```bash
sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
sudo yum install http://rpms.remirepo.net/enterprise/remi-release-6.rpm
```

**Centos 7**

```bash
sudo yum -y install epel-release
sudo yum-config-manager --enable remi-php72
```

Sistemimizdeki depo içerik listesini güncelleştiriyoruz

**Centos 6 & 7**

```bash
sudo yum update
```



## Otomatik Kurulum



## Manuel Kurulum