## Benchmarking / Literatür Karşılaştırması

Bu çalışmanın sonuçları, Kaggle platformunda en yüksek etkileşimi alan iki popüler notebook (**Joshua Swords** ve **Niharika Pandit**) ile karşılaştırılmıştır:

* **Kullanılan Yöntem ve Teknikler:** Swords yalnızca betimsel EDA ve veri hikayeleştirmeye odaklanırken; Pandit, metin vektörleştirmede `TF-IDF` ve `CountVectorizer` ile `Cosine Similarity` kullanarak İçerik Tabanlı Öneri Modeli sunmuştur.
* **Görselleştirme Kalitesi:** Swords `Matplotlib`/`Seaborn` ile özel renk paletleri ve tipografi odaklı estetik görseller üretmiş; Pandit ise dinamik `Plotly` ve `WordCloud` grafiklerini tercih etmiştir. Topluluk genelindeki çoğu çalışmada ise görseller yüzeysel kalmıştır.
* **Veri Ön İşleme Stratejileri:** Kaggle'daki notebook'ların çoğunda yüksek eksiklik içeren sütunlar (`director`, `country`) silinmiş veya göz ardı edilmiştir. Bu projede ise eksik veriler kategorize edilerek korunmuş, tarih ve süre dönüştürmeleri detaylı olarak yapılmıştır.
* **Model Performansı ve Evaluation:** Literatürdeki çalışmaların %90'ından fazlasında (incelenen iki notebook dahil) öneri modellerinin başarısını ölçecek nicel metrikler (`Precision@K`, `Recall@K`, `MAP`) kullanılmamış; çıktılar yalnızca örnek başlıkların mantıksal kontrolü ile doğrulanmıştır.
