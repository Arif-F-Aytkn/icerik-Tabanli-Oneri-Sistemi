## Benchmarking / Literatür Karşılaştırması

Bu projede geliştirilen yaklaşım ve elde edilen bulgular, Kaggle platformunda **Netflix Movies and TV Shows Dataset** üzerinde en yüksek etkileşimi (upvote) almış öne çıkan topluluk çalışmalarıyla (örn. *Joshua Swords - Netflix Data Visualization*, *Niharika Pandit - Netflix Visualizations & Recommendation*) kıyaslanmış ve aşağıdaki boyutlarda değerlendirilmiştir.

---

### 1. Görselleştirme Teknikleri ve Sunum
* **Topluluk Çalışmaları:** Kaggle üzerindeki popüler defterler ağırlıklı olarak görsel anlatıma odaklanmıştır. Görselleştirmelerde `Matplotlib`, `Seaborne`, interaktif grafikler için `Plotly` ve metin madenciliği görselleştirmesi için `WordCloud` yaygın olarak kullanılmıştır.
* **Değerlendirme:** Görsel çeşitlilik ve estetik seviyesi oldukça yüksektir. Ancak grafiklerin büyük bir kısmı sadece betimsel kalmış, grafiklerden çıkarılan içgörüler istatistiksel anlamlılık testleri ile desteklenmemiştir.

---

### 2. Öneri Algoritmaları ve Yöntem Seçimi
* **Topluluk Çalışmaları:** Öneri sistemlerinde genelde metin sütunlarının (`title`, `director`, `cast`, `listed_in`, `description`) birleştirilmesiyle elde edilen "soup" metinleri üzerinde **Content-Based Filtering (İçerik Tabanlı Filtreleme)** uygulanmıştır. Vektörleştirme adımında `TF-IDF` veya `CountVectorizer` tercih edilmiş; benzerlik skoru olarak **Kosinüs Benzerliği (Cosine Similarity)** veya graf tabanlı `NetworkX` yaklaşımları kullanılmıştır.
* **Değerlendirme:** Yaklaşımlar pratik ve işlevsel olmakla birlikte, metin matrislerinin yüksek boyutlu (d -dimensional) ve seyrek (*sparse*) yapısının matematiksel arka planı genellikle detaylandırılmamıştır.

---

### 3. Değerlendirme Metrikleri ve Performans Ölçümü
* **Topluluk Çalışmaları:** Çalışmaların çoğunda öneri sistemlerinin başarısını nicel olarak ölçecek metrikler yer almamaktadır. Az sayıda gelişmiş notebook'ta `Precision@K` veya çizge tabanlı benzerlik ölçütleri (`Adamic-Adar Index`) kullanılmıştır.
* **Değerlendirme:** Metrik kullanımı topluluk genelinde belirgin bir eksikliktir. Öneri sonuçları çoğunlukla sezgisel örnekler üzerinden doğrulanmıştır.

---

### 4. Veri Ön İşleme ve İstatistiksel Yaklaşım (Farkımız)
* **Tespit Edilen Literatür Eksikliği:** Kaggle'daki mevcut çalışmaların neredeyse tamamı, eksik değerleri sildikten veya doldurduktan hemen sonra doğrudan makine öğrenmesi modellerine ve görselleştirmeye geçmektedir. Eksik verilerin mekanizması (MCAR, MAR, MNAR) veya değişkenler arası istatistiksel bağımlılıklar analiz edilmemiştir.
* **Bizim Özgün Yaklaşımımız:** Bu projede klasik veri bilimi adımlarına ek olarak **İstatistiksel Hipotez Testi ve Dağılım Analizi** katmanı eklenmiştir:
  1. **Eksik Veri Analizi:** Eksikliğin rastgeleliğini sınamak adına kategorik değişkenler arası Ki-Kare χ² bağımsızlık testleri uygulanmıştır.
  2. **Dağılım Testleri:** Film süreleri ve dizi sezon sayılarının dağılım parametreleri (çarpıklık, basıklık) ve normallik testleri ile incelenmiştir.
  3. **Kategorik İlişki Analizi:** Yaş grupları (`rating`) ile içerik türü (`type`) arasındaki ilişkinin istatistiksel anlamlılığı test edilmiştir.
  4. **Vektör Uzayı Matematiği:** Öneri sistemindeki TF-IDF ve kosinüs benzerliğinin geometrik ve olasılıksal temelleri açıklanarak model kurulmuştur.
