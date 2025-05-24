# 🛍️ Müşteri Segmentasyonu ile Pazarlama Stratejileri

## Proje Özeti
Bu projede, bir perakende şirketinin müşteri verileri kullanılarak **K-Means kümeleme algoritması** ile müşteri segmentasyonu yapılmıştır. Amaç, farklı müşteri gruplarını belirleyerek her bir segment için özelleştirilmiş pazarlama stratejileri geliştirmektir.

## İçindekiler
- [Kullanılan Veri Seti](#kullanılan-veri-seti)
- [Adım Adım Çalışma](#adım-adım-çalışma)
- [Ekstra Analizler ve Segment Yorumları](#ekstra-analizler-ve-segment-yorumları)
- [Segment Profilleri ve Pazarlama Önerileri](#segment-profilleri-ve-pazarlama-önerileri)
- [Sonuç ve Stratejik Öneriler](#sonuç-ve-stratejik-öneriler)
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

## Ekstra Analizler ve Segment Yorumları

### 1. Segmentlere Göre Ortalama Harcamalar
- **Segment 0:** Şarap harcaması açık ara en yüksek. Lüks ve premium ürünlere yüksek harcama yapıyor. Et ve altın ürünlerinde de yüksek harcama var.
- **Segment 2:** Et ve balık harcamalarında öne çıkıyor. Şarap harcaması da yüksek, ancak Segment 0 kadar değil. Çeşitli ürün gruplarında dengeli ve yüksek harcama yapıyor.
- **Segment 3:** Şarap ve et harcamalarında orta seviyede, diğer ürünlerde ise Segment 0 ve 2'ye göre daha düşük.
- **Segment 1:** Tüm ürün gruplarında en düşük harcamaya sahip. Özellikle şarap ve altın ürünlerinde neredeyse hiç harcama yok.

**İş Açısından:** Segment 0 ve 2, yüksek harcama potansiyeline sahip, lüks ve çeşitli ürünlere ilgi gösteren müşteriler. Segment 1 ise fiyat hassasiyeti yüksek, düşük harcama yapan bir grup. Segment 3 ise orta düzeyde harcama yapan, daha geleneksel müşteri profili.

### 2. Segmentlere Göre Kampanya Yanıt Oranları
- **Segment 0:** Kampanyalara en yüksek yanıt oranına sahip segment. Özellikle bazı kampanyalarda %100'e yakın yanıt oranı var.
- **Segment 2:** Kampanya yanıt oranları Segment 0'a göre daha düşük ama yine de diğer segmentlere göre yüksek.
- **Segment 3:** Kampanya yanıt oranları düşük-orta seviyede.
- **Segment 1:** Tüm kampanyalarda en düşük yanıt oranına sahip segment.

**İş Açısından:** Segment 0, pazarlama kampanyalarına en duyarlı müşteri grubu. Bu segmentte kişiselleştirilmiş ve özel kampanyalar çok etkili olabilir. Segment 2 de kampanyalara duyarlı, ancak Segment 1 ve 3'te kampanya etkisi sınırlı.

### 3. Segmentlere Göre Alışveriş Kanalı Tercihleri
- **Segment 2:** Katalog ve mağaza alışverişlerinde en yüksek ortalamaya sahip. Geleneksel alışveriş kanallarını tercih ediyor.
- **Segment 0:** Mağaza ve katalog alışverişlerinde yüksek, web alışverişinde ise Segment 2'ye yakın.
- **Segment 3:** Mağaza alışverişinde yüksek, katalogda Segment 2 ve 0'ın gerisinde.
- **Segment 1:** Web ziyaretlerinde ve web alışverişinde öne çıkıyor, ancak katalog ve mağaza alışverişlerinde düşük.

**İş Açısından:** Segment 2 ve 0, fiziksel mağaza ve katalog kanallarında aktif. Segment 1 ise dijital kanallarda daha aktif, ancak genel alışveriş hacmi düşük. Segment 3 ise mağaza alışverişine yatkın, katalogda ise daha az aktif.

### 4. Segmentlerin Yaş ve Gelir Ekseni Üzerinde Dağılımı
- **Segment 0 ve 2:** Yüksek gelirli müşterilerden oluşuyor. Segment 2, yaş olarak daha geniş bir aralığa yayılmış.
- **Segment 1:** Düşük gelirli ve daha genç müşterilerden oluşuyor. Yaş ve gelir açısından kümelenmiş durumda.
- **Segment 3:** Orta gelirli ve yaşça daha olgun müşterilerden oluşuyor. Segment 0 ve 2'ye göre daha düşük gelirli.

**İş Açısından:** Segment 0 ve 2, yüksek gelirli ve yaşça olgun müşteri kitlesiyle lüks ve premium ürünler için hedeflenebilir. Segment 1, genç ve düşük gelirli müşteri kitlesiyle fiyat odaklı kampanyalar için uygun. Segment 3 ise orta gelirli, geleneksel müşteri profiliyle aile ve güven temalı kampanyalara uygun.

## Segment Profilleri ve Pazarlama Önerileri

| Segment | Yaş Profili         | Gelir Profili      | Pazarlama Stratejisi                        |
|---------|---------------------|--------------------|----------------------------------------------|
| 0       | Orta-üst yaş        | Yüksek gelir       | Lüks ürünler, kişiselleştirilmiş teklifler  |
| 1       | Genç-orta yaş       | Düşük gelir        | Fiyat odaklı kampanyalar, gençlere promosyon|
| 2       | Geniş yaş aralığı   | Yüksek gelir       | Sadakat programları, premium hizmetler       |
| 3       | Orta-üst yaş        | Orta gelir         | Aile paketleri, güven ve kalite vurgusu      |

## Sonuç ve Stratejik Öneriler

- **Segment 0 & 2:** Lüks ürünler, sadakat programları, kişiselleştirilmiş kampanyalar ile yüksek gelirli ve harcama potansiyeli yüksek müşteriler hedeflenmeli.
- **Segment 1:** Fiyat avantajı, gençlere özel dijital kampanyalar ile düşük gelirli ve genç müşteri kitlesi kazanılmalı.
- **Segment 3:** Aile paketleri, güven ve kalite vurgusu, mağaza içi promosyonlar ile geleneksel ve orta gelirli müşteri profili elde tutulmalı.

Bu segmentasyon sayesinde, her müşteri grubuna özel pazarlama stratejileri geliştirilebilir. Bu da müşteri memnuniyetini ve şirket gelirini artıracaktır.

## Kaynaklar
- [Kaggle - Customer Segmentation](https://www.kaggle.com/code/karnikakapoor/customer-segmentation-clustering/notebook)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- [Pandas Documentation](https://pandas.pydata.org/)
- [Seaborn Documentation](https://seaborn.pydata.org/)

---

**Proje sahibi:** Ali Olkac  
Her türlü soru ve öneriniz için iletişime geçebilirsiniz!