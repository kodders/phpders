# Merhaba Dünya

Çoğu öğretici kişi, web sitesi, blog vs. genelde programlama dillerini öğretirken **hello world** isminde bir programcık yazdırır öğrencilerine, bu da öğrencilerin çalıştırdığı ve sonucunu canlı olarak gördüğü ilk program olur. Burada, bu konuyu biraz daha detaylandıracağız, ve nelerle karşılaşabileceğinizi de biraz göstermiş olacağız. 

<runnable>

```php
<?php

  $selamlanacak = "dünya";
  echo "Merhaba " . $selamlanacak . "! ";
	$dogum = 1985;
  echo "Yaşım " . (2020 - $dogum);
  
?>
```

</runnable>

Örnek bir PHP dosyası içeriği. Windows'ta Not defteri, Mac'te TextEdit, Linux'ta gEdit ile normal bir şekilde açtığınızda okunabilir şekilde olduğunu görürsünüz, aynı programlarla da kendiniz oluşturabilirsiniz. 

### Yapısal analiz

- PHP dosyaları, **.php** uzantısıyla biter, onu işleyecek program bu şekilde anlar o dosyanın bir PHP dosyası olduğunu. 
- `<?php` ile başlar ve `?>` ile biter. Ama eğer tüm dosyada sadece PHP yazacaksanız, kapatma tag'ini (< ile başlayıp > ile biten gruplar **tag** olarak adlandırılır) yazmasanız da olur. Buna sonra değineceğiz. Bu iki yazı arasında kalan her şey PHP kodu olarak işlenecektir.
- Her işlem satırı `;` ile bitirilir ki, programımızda işlem adımlarını oluşturabilelim.
- `$` (dolar işareti, <kbd>AltGr</kbd> + <kbd>4</kbd>) ile başlayan kelimeler değişken'lerimizdir. Değişken demek, programın herhangi bir yerinde temsil edilen, sonradan değiştirilebilecek değerleri tutan etiketlerdir. Bardak gibi düşünün. Boş, kahve dolu, çay dolu, şekerli çay dolu, sadece şeker dolu bardak olabilir. İçine ne koyduğunuza bağlı olarak sonraki adımda ne içeceğinizi belirler. Burada `$selamlanacak` ve `$dogum` programımızın değişkenleridir. 
- `=`, `.`, `-` ve `() ` işaretleri operatörler olarak adlandırılır, ve bir fiil'i tanımlar. 
  - `=` **atama** operatörüdür, ve solundaki değişkene sağındaki değeri atar. 
  - `.` ise **metin birleştirme** operatörüdür, solundaki ve sağındaki değerleri birleştirir, tek yapar. Mesela `Merhaba ` yazısı ile `$selamlanacak` değişkeni içerisindeki değer birleşince , `Merhaba dünya` yazısı oluşur, daha sonra bu yazı ile `! ` yazısı birleşince `Merhaba dünya! ` yazısı meydana çıkar. Boşluk karakterlerine dikkat edin. Onlar da birleştirilir.
  - `-` işareti ise **matematiksel çıkarma** operatörüdür, soldaki sayıdan sağdakini çıkartır.
  - `()` işaretleri gruplandırma işaretleridir, aynı matematikteki gibi, öncelikle parantezin içini hesaplatır, sonra o hesaplanan değer parantezin dışına aktarılır. Örneğin `5 * (3 - 1)`in sonucu 10 iken, `(5 * 3) - 1`in sonucu 14'tür. Parantezler, bu özelliğin kod yazılırken de kullanılmasını sağlar. Bir işlemin bir bölümünün önceliğini arttırmak isterseniz, o kısmı parantez içine alırsınız.
- `echo`  ekrana çıktı vermeye yarayan deyimdir. Sağında ne varsa ekrana basar.



### Fonksiyonel analiz

Kodu görmek için tekrar ekleyelim: 

<runnable>

```php
<?php

  $selamlanacak = "dünya";
  echo "Merhaba " . $selamlanacak . "! ";

	$dogum = 1985;
  echo "Yaşım " . (2020 - $dogum);

?>
```

</runnable>

Programımız 4 işlem satırı ve 2 ekrana basma deyiminden ibaret. İlk ekrana basma kısmına kadar inceleyelim öncelikle.  

İlk satır

```php
$selamlanacak = "dünya";
```

`$selamlanacak` isimli bir değişken oluştur, içine "dünya" yazısını at. Bundan sonra `$selamlanacak` nerede geçerse yerine "dünya" yazısını koyduğumuzu varsayacağız. Çünkü değişkenimizin değeri artık "dünya".

İkinci satır:

```php
echo "Merhaba" . $selamlanacak . "! ";
```

Burada 3 nesne arasında bir birleştirme işlemi yapılıyor, bu birleştirme tamamlanınca ortaya çıkan değer ekrana basılıyor. Peki echo deyimi, en önce olmasına rağmen neden en sona işlendi? Cevap, **echo deyimi en önce gelmiş ama, sonrakilerin işlemi bitmeden ekrana neyi basacağını bilmiyor.** Bunu göz önünde bulundurarak, adım adım kod işlenirken şu şekilleri alacak:

```php
echo "Merhaba " . $selamlanacak . "! ";

echo "Merhaba " . "dünya" . "! "; // $selamlanacak değişkeninin değeri yerleştirildi

echo "Merhaba dünya" . "! "; // "Merhaba " ve "dünya" birleşti, "Merhaba dünya" oldu

echo "Merhaba dünya! "; // "Merhaba dünya" ve "! " birleşti, "Merhaba dünya! " oldu
```

En son satırda artık `echo` ekrana neyi basacağını biliyor, ve ekrana onu yerleştiriyor.



Şimdi, farklı bir türdeki değişkenin nasıl işlendiğini gösteren ikinci örneğe geçiyoruz:

<runnable>

```php
<?php 
  $dogum = 1985;
	echo "Yaşım " . (2020 - $dogum);  
?>
```

</runnable>

Burada `$dogum` değişkenine sayısal bir değer atanmış (1985). Sayısal olduğu için üzerinde matematiksel operatörlerin işlem yapmasına izin veren bir değişken oluşturmuş. 

İkinci satırda ise bu değişkendeki sayı, 2020 sayısından çıkartılarak, 2020 yılında bu vatandaşın yaşı hesaplanmak istenmiş. 

Önceki örnekteki gibi işlem adımlarını görselleştirelim:

```php
echo "Yaşım " . (2020 - $dogum);

echo "Yaşım " . (2020 - 1985); // $dogum değişkeninin değeri yerine yazılır

echo "Yaşım " . 35; // matematik işlemi yapılır, parantez dışına çıkartılır

echo "Yaşım " . "35"; // birleştirebilmek için PHP sayısal değeri metin eşdeğerine dönüştürür

echo "Yaşım 35"; // birleştirme işlemi yapılır, "Yaşım 35" elde edilir, ekrana basılır
```



4üncü adımda dikkatinizi çekmiştir, sayısal değer bir metin birleştirme işleminin parçası olacağı zaman, PHP yorumlayıcısı, o değeri önce metin eşdeğerine çevirir, sonra birleştirir. Tam tersi de doğrudur, bir metin değeri bir sayıyla toplanmak istendiğinde önce o metin değerinin soldan başlanarak sayısal değerine dönüştürülmeye çalışılır. 

Örnekler:

```php
"Ahmet" + 12 = 12			// soldan ilk karakter sayısal değil, metne dönüşünce 0 olur
"6yeşil" + 10 = 16		// soldan ilk karakter sayısal, sonraki değil, sadece 6 alınır
"023" + 12 = 35;			// üç karakter de sayısal, 23 olarak dönüşür
"ayşe5" + 2 = 2;			// ilk karakter sayısal değil, 0 olarak dönüşür, sondaki 6 görülmez
```



Temellere böylelikle giriş yaptık. Değişken nedir bir sonraki bölümde biraz daha açacağız. Bu konuda öğrendiklerimiz, PHP dosyası nedir, içinde başında sonunda ne olursa geçerli bir PHP dosyası olur, her satır neyi ifade eder, sıralaması neyi değiştirir, ekrana nasıl yazı yazılır, metin nedir, sayı nedir, değişken ne işe yarar, iki metni nasıl birleştiririz, metinle sayı toplanırsa ne olur, metinle sayı birleştirilirse ne olur bunları gördük. Siz de denemelerinizi ekrandaki çalıştırılabilir kod penceresinden yapabilirsiniz. Değerleri değiştirip, sağdan soldan silip ekleyip istediğiniz şeyi deneyebilirsiniz. 