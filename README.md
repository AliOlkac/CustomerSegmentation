# 🛍️ Müşteri Segmentasyonu ile Pazarlama Stratejileri

## Proje Özeti
Bu projede, bir perakende şirketinin müşteri verileri kullanılarak **K-Means kümeleme algoritması** ile müşteri segmentasyonu yapılmıştır. Amaç, farklı müşteri gruplarını belirleyerek her bir segment için özelleştirilmiş pazarlama stratejileri geliştirmektir.

## İçindekiler
- [Kullanılan Veri Seti](#kullanılan-veri-seti)
- [Adım Adım Çalışma](#adım-adım-çalışma)
- [Ekstra Analizler](#ekstra-analizler)
- [Segment Profilleri ve Pazarlama Önerileri](#segment-profilleri-ve-pazarlama-önerileri)
- [Sonuç](#sonuç)
- [Kaynaklar](#kaynaklar)

## Kullanılan Veri Seti
- **Dosya:** marketing_campaign.csv
- **Özellikler:** Demografik bilgiler (yaş, eğitim, medeni durum, gelir), alışveriş ve kampanya yanıtları, harcama alışkanlıkları.

## Adım Adım Çalışma

### 1. Veri Keşfi ve Temizliği
- Eksik gelir verisi olan 24 müşteri analiz dışı bırakıldı.
- Yaş ve gelirde uç değerler temizlendi.
- Medeni durum sütununda anlamsız kategoriler ("Alone", "Absurd", "YOLO") "Other" olarak gruplandı.
- Yeni bir "Yaş" sütunu oluşturuldu.

### 2. Kategorik Değişkenlerin Sayısallaştırılması
- Eğitim ve medeni durum sütunları one-hot encoding ile sayısallaştırıldı.

### 3. Sayısal Değişkenlerin Ölçeklendirilmesi
- Tüm sayısal değişkenler StandardScaler ile ölçeklendirildi.

### 4. Kümeleme (K-Means)
- Elbow ve Silhouette yöntemleriyle optimum küme sayısı belirlendi (örneğin 4).
- K-Means algoritması ile müşteriler segmentlere ayrıldı.

### 5. Segment Analizi
- Her segmentin yaş ve gelir dağılımı kutu grafikleriyle incelendi.
- Segmentlerin temel profilleri ve pazarlama önerileri çıkarıldı.

## Ekstra Analizler

### Segmentlere Göre Harcama Alışkanlıkları
Her segmentin şarap, et, tatlı, balık vb. ürünlere yaptığı ortalama harcamalar analiz edildi.

### Segmentlere Göre Kampanya Yanıt Oranları
Her segmentin pazarlama kampanyalarına verdiği yanıt oranları incelendi.

### Segmentlere Göre Alışveriş Kanalı Tercihleri
Web, mağaza ve katalog alışverişlerinin segmentlere göre dağılımı analiz edildi.

### Segmentlerin 2D Scatter Plot ile Görselleştirilmesi
Yaş ve gelir ekseninde segmentlerin dağılımı görselleştirildi.

> **Not:** Tüm görseller ve kodlar için notebook dosyasına göz atabilirsiniz.

## Segment Profilleri ve Pazarlama Önerileri

| Segment | Yaş Profili         | Gelir Profili      | Pazarlama Stratejisi                        |
|---------|---------------------|--------------------|----------------------------------------------|
| 0       | Orta-üst yaş        | Yüksek gelir       | Lüks ürünler, kişiselleştirilmiş teklifler  |
| 1       | Genç-orta yaş       | Düşük gelir        | Fiyat odaklı kampanyalar, gençlere promosyon|
| 2       | Geniş yaş aralığı   | Yüksek gelir       | Sadakat programları, premium hizmetler       |
| 3       | Orta-üst yaş        | Orta gelir         | Aile paketleri, güven ve kalite vurgusu      |

## Sonuç
Müşteri segmentasyonu sayesinde, her müşteri grubuna özel pazarlama stratejileri geliştirilebilir. Bu da müşteri memnuniyetini ve şirket gelirini artıracaktır.

## Kaynaklar
- [Kaggle - Customer Segmentation](https://www.kaggle.com/code/karnikakapoor/customer-segmentation-clustering/notebook)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- [Pandas Documentation](https://pandas.pydata.org/)
- [Seaborn Documentation](https://seaborn.pydata.org/)

---

**Proje sahibi:** Ali Olkac  
Her türlü soru ve öneriniz için iletişime geçebilirsiniz!