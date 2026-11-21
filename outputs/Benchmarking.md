### Projemize Kazandıracağımız İstatistiksel Dokunuşlar

1.  **Eksik Veri Mekanizması Analizi (Missing Data Mechanism):**
    
    *   Eksik verileri rastgele silmek veya 'Unknown' yazıp geçmek yerine, eksikliğin mekanizmasını (MCAR, MAR, MNAR) değerlendireceğiz.
        
    *   Örneğin; country veya director sütunundaki eksikliklerin içerik türüne (type) veya eklenme yılına bağlı olup olmadığını ki-kare χ² bağımsızlık testi ile inceleyebiliriz.
        
2.  **Betimsel İstatistik ve Hipotez Testleri:**
    
    *   **Tip ve Süre Analizi:** Film sürelerinin (dakika) ve dizi sürelerinin (sezon) dağılım uygunluğu. Normal dağılım gösterip göstermediğini çarpıklık (_skewness_), basıklık (_kurtosis_) ve normallik testleri ile sınayacağız.
        
    *   **Kategorik Değişken İlişkileri:** İçerik türü (Film vs. Dizi) ile yaş kategorileri (rating) arasında anlamlı bir ilişki var mı? Ki-Kare χ² testi ile kontrol edeceğiz.
        
    *   **Mevsimsellik ve Trend:** Yıllara göre eklenen içerik sayılarındaki artışın trend bileşenlerini ve mevsimsellik etkisini inceleyeceğiz.
        
3.  **Öneri Sistemi ve Vektör Uzayı Matematiği:**
    
    *   Öneri sistemindeki TF-IDF yaklaşımını sadece hazır kütüphane fonksiyonu olarak kullanmayıp, kelime frekanslarının logaritmik ölçeklenmesini, yüksek boyutlu metin matrislerinin sparse (seyrek) yapısını ve kosinüs benzerliğinin geometrik/istatistiksel anlamını (iki vektör arasındaki açının kosinüsü) açıklayacağız.
