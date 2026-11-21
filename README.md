# Netflix İçerik ve Keşifsel Veri Analizi (EDA)

## Proje Amacı
Bu projenin amacı, Netflix platformundaki film ve dizilere ait verileri temizlemek, işlemek ve Keşifsel Veri Analizi (EDA) yöntemleriyle platformun içerik stratejisini, yıllık büyüme trendlerini ve kategori/ülke dağılımlarını ortaya koymaktır.

##  Veri Seti
Projede kullanılan `netflix_titles.csv` veri seti **8.807 satır** ve **12 sütun** içermektedir. Veri setinde yer alan temel değişkenler şunlardır:
* `show_id`, `type` (Movie / TV Show), `title`, `director`, `cast`
* `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, `description`

##  Yöntemler ve Veri Ön İşleme
1. **Eksik Veri Yönetimi**: `director`, `cast` ve `country` sütunlarındaki eksik değerler `'Unknown'` ile dolduruldu.
2. **Metin ve Tarih İşleme**:
   * `date_added` sütunundaki boşluklar temizlenerek `datetime` dönüştürmesi yapıldı; `yil` ve `ay` değişkenleri türetildi.
   * `duration` metinlerinden regex (`\d+`) ile sayısal süre değerleri çekildi.
   * `listed_in` alanındaki türler ayrılarak liste yapısına dönüştürüldü.
3. **Veri Kalitesi ve Temizlik**: `rating` sütununda yer alan hatalı süre verileri (`'74 min'`, vb.) tespit edilip ayıklandı.

##  Elde Edilen Temel Sonuçlar
* **İçerik Dağılımı**: Netflix kataloğunun **%69.6'sı Film**, **%30.4'ü Dizi** kategorisindedir.
* **Yıllık Trend**: 2015 yılı itibarıyla platforma eklenen içerik sayısında belirgin bir ivmelenme yaşanmış, en yüksek ekleme oranlarına **2019–2020** yıllarında ulaşılmıştır.
* **Bölgesel ve Tür Odakları**: 
  * En çok içerik sağlanan ilk iki ülke **ABD (2.818)** ve **Hindistan (972)**'dır.
  * En yaygın türler **"International Movies"** ve **"Dramas"** olarak öne çıkmaktadır.
* **Hedef Kitle**: Platformda en baskın kategoriler yetişkin içeriklerini temsil eden **TV-MA** ve 14 yaş üzeri için uygun olan **TV-14** seviyelerindedir.

---
## Benchmarking / Literatür Karşılaştırması

Bu çalışmanın sonuçları, Kaggle platformunda en yüksek etkileşimi alan iki popüler notebook (**Joshua Swords** ve **Niharika Pandit**) ile karşılaştırılmıştır:

* **Kullanılan Yöntem ve Teknikler:** Swords yalnızca betimsel EDA ve veri hikayeleştirmeye odaklanırken; Pandit, metin vektörleştirmede `TF-IDF` ve `CountVectorizer` ile `Cosine Similarity` kullanarak İçerik Tabanlı Öneri Modeli sunmuştur.
* **Görselleştirme Kalitesi:** Swords `Matplotlib`/`Seaborn` ile özel renk paletleri ve tipografi odaklı estetik görseller üretmiş; Pandit ise dinamik `Plotly` ve `WordCloud` grafiklerini tercih etmiştir.
* **Veri Ön İşleme Stratejileri:** Kaggle'daki notebook'ların çoğunda yüksek eksiklik içeren sütunlar (`director`, `country`) silinmiş veya göz ardı edilmiştir. Bu projede ise eksik veriler kategorize edilerek korunmuş, tarih ve süre dönüştürmeleri detaylı olarak yapılmıştır.
* **Model Performansı ve Evaluation:** Literatürdeki çalışmaların %90'ından fazlasında (incelenen iki notebook dahil) öneri modellerinin başarısını ölçecek nicel metrikler (`Precision@K`, `Recall@K`, `MAP`) kullanılmamış; çıktılar yalnızca örnek başlıkların mantıksal kontrolü ile doğrulanmıştır.
