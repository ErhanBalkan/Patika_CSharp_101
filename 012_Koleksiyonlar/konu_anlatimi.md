# Koleksiyon(Collections) Nedir ?
---
Klasik programlama dillerinde array yani diziler çok önemli veri tipleridir. Birçok problemimizi diziler yardımıyla çözebiliriz ama bazı handikapları nedeniyle birçok sorun karşısında da yetersiz kalırlar.Bu sorunları şöyle sıralayabiliriz:

* Array'in elemanları aynı veri tipinde olmalıdır.
* Array'in boyutu önceden belirlenmelidir.

Oysa programlama dillerinde farklı türlerde verileri saklamaya ihtiyaç duyarız. Ve çoğu zaman ne kadar veri saklayacağımız program akışında belli olabilir. Koleksiyonlar tam da bu sorunları çözmek için dizilerin handikaplarından yaratılmıştır.

Dizilerin aksine koleksiyonların bazı tipleri; üzerinde çalıştıkları makinaın RAM'i yettiği sürece genişleyebilirler ve farklı türlerde veri tiplerini saklayabilirler.

Koleksiyonların elemanları object tipindedir. Hatırlayacak olursak öğrendiğimiz veri tipleri için object sınıfından türediklerini söylemiştik. Yani bu bir sorun değil, her türlü veriyi koleksiyonlar içerisinde saklayabiliriz.

Koleksiyonlar System.Collections namespace i yani isim uzayı altında bulunurlar. Yani bir koleksiyon tipini kullanmak istiyorsanız System.Collections'ı using direktifi ile programınıza import ediyor olmanız gerekiyor.

Peki bu Koleksiyonlar'ın hiç dezavantajı yok mu? Olmaz olur mu tabiki var. Gelin yakından bakalım.

## Dezavantajları

.NEt platformda kullanıdığımız veri tipleri 2'ye ayrılır. Değer ve referans veri tipleridir. Değer tipleri belliğin stack bölgesinde tutulurken, Referans tipleri belleğin heap bölgesinde tutulur.

`Değer Tipleri: int, long, float, double, decimal, char, bool, byte, short, struct, enum`
`Referans Tipleri: string, object, class, interface, array, delegate, pointer`

Bir değer tipinin referans tipine dönüştürülme boxing, tam tersine unboxing işlemi denir.

Koleksiyonlar verilerini object tipinde tutuyor demiştik. Object de bir referans tipi. Bu demek oluyor ki değer tipinde bir veriyi koleksiyona eklemek istediğimde bir boxing işlemi yapıyorum. Daha sonra elemanı okumak istediğimde de unboxing işlemi yapıyorum. Boxing ve unboxing işlemleri bilgisayar açısından maliyetli bir işlemdir. Koleksiyon içerisindeki eleman sayısının artışına bağlı olarak bu boxing ve unboxing işlemlerinin sayısı artacaktır. Buna bağlı olarakta uygulamanın performansı olumsuz yönde etkilenecektir.

# Generic Koleksiyonlar

Generic list System.Colections.Generic isim uzayı altında bulunan bit list sınıfı koleksiyonudur. Generic List bir list sınıfı tanımlarken T olarak tip değişkenini alır. Generic olmasını sağlayan da burdaki T veri tipidir. T listenin hangi türden veri tutacağını belirler. Bu tanımlama sonunda farklı türden bir veri tipini generic list ile saklayamazsınız.

Örnek söz dizimi şu şekildedir:

```
List<string> renkler = new List<string>();

renkler.Add("Mavi");
renkler.Add("Kırmızı");
```

# ArrayList Nedir ?

Standart dizilerde aynı tipte verileri verileri bir arada tutabileceğimizi ve dizinin boyutunun belirtilmesi gerektiğinden bahsetmiştik. Arraylist tam olarak bu noktada farklılaşıyor. Farklı veri tiplerini array list içerisinde saklayabilirsiniz. Ve eleman ekleyerek ve cıkararak boyutunu dinamik olarak değiştirebilirsiniz.
Varsayılan boyutu başlangıç olarak 4'tür. Aşıldığından otomatik olarak 2 katına çıkarılır. Yani bir array liste 5. elemanı eklemeye calıştıgınızda atka planda boyutunun 8'e çıkarır.

Örnek:
```
ArrayList dizi = new ArrayList();

dizi.Add("Kedi");
dizi.Add(99);
dizi.Add(true);
```

Yukarıdaki örnekte tanımladıgımız ArrayList içerisine string, integer ve bool veri tipindeki verileri aynı koyduk.
Değişken veri tipi kullanımı kulağa ilk etapta çok konforlu gelse de risk barındır. Listeden okudugunuz verinin tipinin ne olduğunu bilmemek güvenli bir yaklaşım değildir. Tip dönüşümleri sırasında hata ihtimalini arttırır.

# Dictionary Nedir ?

Dictionary koleksiyonunda key-value yani anahtar-deger denen 2 kavram ile karşılaşıyoruz. Dizilere eklediğimiz elemanları value, index lerini ise key olarak düşünebilirsiniz.

Dictionary lerin elemanlarının anahtarları birbirinden farklı olmalıdır. Aynı anahtar kullanılarak 2 değer saklanamaz.

Örnek söz dizimi şu şekildedir:

```
Dictionary<Key_Veri_Tipi, Value_Veri_Tipi> dictionary_adi = new Dictionary<Key_Veri_Tipi, Value_Veri_Tipi>();
```

Örnek:


```
Dictionary<int,string> renkler = new Dictionary<int, string>();

renkler.Add(3,"Kırmızı");
renkler.Add(5,"Sarı");
```

Yukarıdaki örnekte anatarı integer olan, değeri string olan renkler adında bir dictionary tanımladık. 3-"Kırmızı", 5-"Sarı" ikililerini dictionary'e ekledik.
