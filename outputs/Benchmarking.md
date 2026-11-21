## Benchmarking / Literatür Karşılaştırması

Bu çalışmada, Kaggle platformunda **Netflix Movies and TV Shows Dataset** üzerinde en yüksek etkileşimi almış 2 temel çalışma incelenmiş ve karşılaştırmalı analize tabi tutulmuştur:

* **Çalışma 1:** *Netflix Data Visualization* (Joshua Swords)
* **Çalışma 2:** *Netflix Visualizations, Recommendation & EDA* (Niharika Pandit)

---

### 1. Görselleştirme Teknikleri ve Sunum
* **Joshua Swords:** Ağırlıklı olarak `Matplotlib` ve `Seaborn` kütüphanelerini kullanarak özel renk paletleri ve tipografi ile betimsel görseller oluşturmuştur. Veri hikayeleştirme ve estetik düzen ön plandadır.
* **Niharika Pandit:** Dinamik ve kullanıcı etkileşimli grafikler sunan `Plotly` kütüphanesini ve metin madenciliği için `WordCloud` görsellerini tercih etmiştir.
* **Genel Topluluk Çalışmaları:** Çoğunlukla standart pasta, bar ve çizgi grafikleri kullanılmış; grafik çeşitliliği yüksek tutulsa da analizler yüzeysel seviyede kalmıştır.

---

### 2. Öneri Algoritmaları ve Yöntem Farklılıkları
* **Joshua Swords:** Çalışmasını temel olarak Keşifsel Veri Analizi (EDA) ve görselleştirme üzerine kurgulamış, makine öğrenmesi tabanlı bir öneri algoritmasına yer vermemiştir.
* **Niharika Pandit:** `title`, `director`, `cast`, `listed_in` ve `description` metinlerinin birleştirilmesiyle oluşturulan metin "soup" yapısı üzerinde **İçerik Tabanlı Filtreleme (Content-Based Filtering)** uygulamıştır. Metinlerin vektörleştirilmesinde `TF-IDF` ve `CountVectorizer` tercih edilerek **Kosinüs Benzerliği (Cosine Similarity)** hesaplanmıştır.
* **Diğer Çalışmalar:** İçerik tabanlı önerilere ek olarak bazı gelişmiş çalışmalarda oyuncu/yönetmen ilişkilerini haritalayan graf tabanlı (`NetworkX`) yaklaşımlar veya düz Python eşleşme algoritmaları kullanılmıştır. İş Birlikçi Filtreleme (Collaborative Filtering) kullanımı kullanıcı etkileşim verisinin (rating/user ID) olmaması nedeniyle tercih edilmemiştir.

---

### 3. Değerlendirme Metrikleri ve Performans Ölçümü
* **Joshua Swords & Niharika Pandit:** Öneri çıktılarının başarısını nicel olarak ölçecek herhangi bir matematiksel değerlendirme metriğine (`Precision@K`, `Recall@K`, `MAP` vb.) yer vermemişlerdir. Doğrulama, çıktı olarak üretilen örnek başlıkların mantıksal kontrolü ile sınırlı kalmıştır.
* **Diğer Çalışmalar:** Kaggle genelindeki notebook'ların %90'ından fazlasında metrik kullanımı eksiktir. Yalnızca kısıtlı sayıda nitelikli çalışmada çizge tabanlı `Adamic-Adar Index` veya benzerlik skorları eşik değer analizi kullanılmıştır.

---

### 4. Veri Ön İşleme Stratejileri ve Tespit Edilen Eksiklikler
* **Eksik Değer İşleme:** İnceleyen çalışmaların büyük çoğunluğu `director`, `cast` ve `country` sütunlarındaki yüksek oranlı eksik verileri silmek veya doldurmadan analiz dışı bırakmak yoluna gitmiştir.
* **Tip Dönüşümleri ve Ayrıştırma:** `duration` (film dakikası ve dizi sezon sayısı) sütununun sayısal olarak ayrıştırılması çoğu çalışmada yapılmış, ancak `date_added` sütunundan yıl ve ay türetme adımları bazı notebook'larda yüzeysel kalmıştır.
* **Genel Eksiklik:** İncelenen 2 ana kaynakta da eksik verilerin veya değişkenlerin matematiksel/istatistiksel dağılım yapıları derinlemesine incelenmemiş, ön işleme adımlarından sonra doğrudan görselleştirme ve model kurma aşamasına geçilmiştir.
