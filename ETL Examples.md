# ETL ÖRNEKLERİ :
Önce projeyi clonelayalım.
```sh 
  $ git clone https://github.com/WoodProgrammer/etl-ruby.git 
  $ cd etl-ruby
  $ ruby etl.rb
```
# KOD BLOKLARI 

## EXTRACT 
```ruby

def Extract
  doc = Nokogiri::HTML(open("http://www.koeri.boun.edu.tr/scripts/lst4.asp"))
  x = doc.xpath("//pre")
  file = open('temp_data','w+')
  file.write(x)
  file.close()
end

```
* Kandilli Rasathanesi'nin son depremler adlı web sitesinden deprem verilerini çekiyorum.
Çektiğim verinin görüntüsü şu şekilde.
```
..................TÜRKİYE VE YAKIN ÇEVRESİNDEKİ SON DEPREMLER....................
.....BÖLGESEL DEPREM-TSUNAMİ İZLEME VE DEĞERLENDİRME MERKEZİ HIZLI ÇÖZÜMLERİ.....
......(YAPAY SARSINTI ANALİZİ YAPILMAMIŞTIR) Son 2000 deprem listelenmiştir......
                                                        Büyüklük
Tarih      Saat      Enlem(N)  Boylam(E) Derinlik(km)  MD   ML   Mw    Yer                                             Çözüm Niteliği
---------- --------  --------  -------   ----------    ------------    --------------                                  --------------
2017.06.15 23:28:55  37.8883   27.4035        7.2      -.-  2.4  -.-   HAVUTCULU-SELCUK (IZMIR)                          İlksel
2017.06.15 23:10:10  38.8733   26.2208        5.4      -.-  2.3  -.-   EGE DENIZI                                        İlksel
2017.06.15 22:43:16  39.4385   26.8503       12.8      -.-  1.8  -.-   KARAAGAC-GOMEC (BALIKESIR)                        İlksel
2017.06.15 22:42:06  38.9098   26.3980        4.8      -.-  1.5  -.-   EGE DENIZI                                        İlksel
2017.06.15 22:38:42  39.0217   26.2833        9.3      -.-  2.1  -.-   MIDILLI ADASI (EGE DENIZI)                        İlksel
2017.06.15 22:34:44  38.9293   26.3712       16.2      -.-  1.9  -.-   EGE DENIZI                                        İlksel
2017.06.15 22:15:40  38.9310   26.1752       11.1      -.-  1.8  -.-   MIDILLI ADASI (EGE DENIZI)                        İlksel
2017.06.15 21:30:37  38.9585   26.1977       10.2      -.-  1.9  -.-   MIDILLI ADASI (EGE DENIZI)                        İlksel
2017.06.15 21:11:33  40.5975   35.3480        0.0      -.-  1.5  -.-   SULUKLU-MECITOZU (CORUM)                          İlksel
2017.06.15 21:03:34  40.6640   27.8592        9.0      -.-  2.1  -.-   MARMARA DENIZI                                    İlksel
2017.06.15 20:45:28  38.7768   27.8023        5.2      -.-  1.8  -.-   SAZOBA-AKHISAR (MANISA)                           İlksel
```

* Görüldüğü üzere ne bir JSON ne bir XML ya da .csv formatında.Veri yapısal bir formda değil.Veriyi Crawle ettik.
## TRANSFORM  LOAD

```ruby

def TransformLoad
  temp_data = open('temp_data','r+')
  i = 0
  temp_data.each do |line|
    i += 1
    if i >=8
      x = line.force_encoding("iso-8859-1").split()
      puts x[0]##date
      begin
        coordinates = x[2]+" "+x[3]
      rescue
        break
      end
      
        puts x[3]##buyukluk
      Deprems.create(date: x[0],buyukluk: x[6],location: coordinates)
    end
  end
end
```
Koordinat datasını birleştirip veri tabanına veri girişi yapıyoruz.