[//]: # "Title: Giriş"

# PHP'ye giriş

Öncelikle PHP nedir diye konuya başlamak istiyorum ancak bunu anlatırken PHP'ye neden ihtiyaç duyulduğundan başlamak daha mantıklı olacak. Bunun için de öncelikle backend - frontend ayrımını yapabilmeniz gerekiyor. 

Backend, yani server (sunucu) tarafı, web sitelerinin her kullanıcının ortak olarak kullandığı ancak çalışırken browser (tarayıcı) üzerinde görmediği kısımları barındırır. Frontend ise kullanıcı tarafında görünen kısımdır. 

Mesela programlamaya başlarken genelde örnek olarak verilen ziyaretçi defteri uygulamasında, frontend şu  kısımlardan oluşur:

1. Kullanıcıların yaptığı yorumların listelendiği _sayfa_
2. Kullanıcının yorumunu ve kendi bilgilerini doldurduğu _form_
3. Formu doldurduktan sonra kullanıcıya gösterilen _onay kutusu, sayfası, bildirimi_ vs
4. Kullanıcının onay kutusunun sol üst köşesindeki çarpıya tıklandığında o kutunun gizlenmesini sağlayan _javascript_ kodu
5. Onay kutusunun yeşil, hata kutusunun kırmızı arkaplana sahip olmasının tanımlandığı _stil dosyaları_

Backend ise şu işleri yapar:

1. Kullanıcıların yaptığı yorumların kaydedildiği ve okunduğu _veritabanını_ yönetir
2. Yorumları veritabanından okuyup kullanıcıya gösteren sayfayı oluşturan bir _programı_ barındırır
3. Formdan gelen bilgileri veritabanına kaydeden, kaydetmeden önce doğrulayan, hatalı bilgi varsa, ya da zararlı bir içerik varsa bunu kullanıcıya bildiren _programı_ barındırır.
4. Başarılı kayıttan sonra kullanıcıya gösterilecek onay içeren sayfayı oluşturan _programı_ barındırır.

Buradan anladığımız kadarıyla, bir sistemin kullanıcılara açıkça gösterilmek istenen kısma frontend, kullanıcının pek ilgisinin olmadığını düşündüğümüz, kullanıcılarca ortak kullanılması gereken ya da kullanıcılara açılması pek güvenli olmayacak kısımları sakladığımız yer de backend denilir. 

Ya da şöyle bir ayrım yapmak da yanlış olmaz: Kullanıcının bilgisayarında görülebilecek her türlü uygulama kodu _HTML_, _CSS_, _Javascript_ (ve genişletmeleri) frontend'i oluşturur. Örneğin; bir siteyi açtığınızda o sitede sağ tuşa tıklayıp **Kaynağı görüntüle** ya da **Öğeyi incele** dediğinizde sayfada çalışan kodların sadece kullanıcı ile paylaşılan kısmını, yani frontend kodlarını görebilirsiniz. Server'da çalışan, size hangi sayfanın gösterileceği, hangi işlemlerin yapılacağı, veritabanına nelerin kaydedileceği vs komutları içeren kodları göremezsiniz.  İşte bu sunucu üzerinde çalışıp size sonuç olarak sayfaları oluşturan kısma ise backend denilir.

PHP bir backend dilidir, ve kullanıcının bilgisayarında server (sunucu) programları kullanılmadan çalıştırılamaz. Genelde kullanılan sunucular Apache ve NGINX sunucularıdır. Bunların nasıl kurulacağını basitçe sonraki bölümlerde anlatacağım, detaylı ayarları ve optimizasyonları, bu dili öğrenmede biraz ilerledikten sonra belki ilginizi çekebilir, ancak hızlı bir giriş yapmak için hazır programlar kullanacağız. 

