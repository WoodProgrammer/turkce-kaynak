### Ad/Soyad: Emir Özbir (stajyer)
### Kurum: TRNET
 
# ETL NEDİR ?
 
Günümüzde veri toplanırken birden farklı formatta ve yapıda toplanırken işlenmesi için de belirli bir formatlar ya da o formata bağlı standartlar kümesi gerekmektedir.Bu standartlar oluşurken özellikle veri bilimcilerini uğraştıran bir konudur.
 
İşte burada devreye ETL girmekte.Herbir harfi farklı bir işlevi temsil eden 3 harf.
 
# E (Extract):
Extract verinin herhangi bir veri kaynağından elde edilmesidir.Bu dümdüz bir veri tabanından çektiğimiz veri,crawle ettiğimiz veri ya da sosyal ağlardan elde ettiğimiz veriler(Twitter API,FourSquare API) olabilir.
 ### Not: Extract edilen verinin belirli periyodlara göre çekilmesi gerekmektedir.Bunlar kendi aralarında Static ve    Incremental Extracting olarak ayrılmaktadır.
 

  
# T (Transform):
Transform ise şöyle bir örnekle açıklanabilir.Mesela ben FourSquare API’den belli başlı mekanların verisini çektim.JSON elimde ama bana sadece o mekanlara ait hareketlilik verisi lazım buna bağlı olarakta bana check-in saatleri yeterli olacaktır.Yani Transform’da ana kütleden cımbızla istediklerimizi ayıklama işlemi yapılmaktadır.
 ### Not: Transform süreçlerinde ise veri belki kolonlara bölünecek belki de eldeki veri kolonları birleştirilecektir.Bu işlemlere ise ya da belli başlı modüller kullanarak ana bir değer elde edilmesidir.

## Pre-Processing:(Transform süreci ile beraber işlemekte.)
 Extract’ten sonra ara bir bölüm olan kendi oluşturduğumuz işlememiz gereken verileri ya da sadece ihtiyacımız olan verileri filter edebildiğimiz ya da her şeyin dışında veriye olan güveni arttıran elde edilen datayı filtrelediğimiz alandır.Anladığım kadarıyla kirli olan raw datayı daha temiz hale getiriyoruz. 
  
# L (Load):
Artık Transform işlemi tamamladıktan sonra Load ile eldeki veri bir veritambarına( aslında o da bir veri tabanı parçası gibi çalışabiliyormuş.) eklenir.Bundan sonrası bizim analizlerimizi,eldeki veriden sonuçlar çıkartıcak algoritmalarımıza ve sorgularımıza kalmaktadır.
 ### Not: Refresh ile veri ambarı yekten yenilenir.Ama Update mod 'da ise sadece değişimler update edilir.