# 🛍️ Müşteri Segmentasyonu ile Pazarlama Stratejileri

## Proje Özeti
Bu projede, bir perakende şirketinin müşteri verileri kullanılarak **K-Means kümeleme algoritması** ile müşteri segmentasyonu yapılmıştır. Amaç, farklı müşteri gruplarını belirleyerek her bir segment için özelleştirilmiş pazarlama stratejileri geliştirmektir.

# ** https://www.kaggle.com/code/aliolkac/customer-segmentation-with-k-means **

## Çalışmanın Tanımı ve Amacı

**Tanım:**
Bu çalışma, bir perakende şirketinin sahip olduğu müşteri veri setini kullanarak, müşterilerin satın alma davranışları, demografik özellikleri ve pazarlama kampanyalarına verdikleri tepkiler temelinde gruplandırılmasını (segmentasyonunu) içermektedir. Müşteri segmentasyonu, pazarlama kaynaklarının daha etkili kullanılması, müşteri memnuniyetinin artırılması ve sonuç olarak şirket karlılığının yükseltilmesi için kritik bir adımdır. Projede, denetimsiz öğrenme yöntemlerinden biri olan K-Means kümeleme algoritması kullanılarak anlamlı ve işlevsel müşteri segmentleri oluşturulmuştur.

**Amaç:**
Projenin temel amacı, aşağıdaki sorulara cevap bularak şirketin pazarlama stratejilerine yön vermektir:

1.  **Farklı Müşteri Grupları Var Mı?** Şirketin müşteri tabanında, benzer özellikler ve davranışlar sergileyen, birbirinden ayrışan belirgin müşteri grupları (segmentler) var mıdır?
2.  **Bu Grupların Özellikleri Nelerdir?** Oluşturulan her bir müşteri segmentinin demografik profili (yaş, gelir, eğitim, medeni durum), harcama alışkanlıkları (hangi ürün gruplarına ne kadar harcama yaptıkları), alışveriş kanalı tercihleri (mağaza, web, katalog) ve pazarlama kampanyalarına duyarlılıkları nelerdir?
3.  **Her Segment İçin Hangi Pazarlama Stratejileri Uygulanmalı?** Her bir segmentin kendine özgü ihtiyaçları, beklentileri ve davranışları göz önüne alındığında, hangi ürünler, kampanyalar ve iletişim kanalları kullanılarak bu segmentlere daha etkili bir şekilde ulaşılabilir?
4.  **Şirket Kaynakları Nasıl Optimize Edilebilir?** Segmentasyon sonuçları ışığında, pazarlama bütçesi ve çabaları, en yüksek geri dönüş potansiyeline sahip segmentlere nasıl odaklanabilir?

Bu amaçlar doğrultusunda, veri analizi, veri ön işleme, modelleme (K-Means), segment profilleme ve sonuçların iş stratejilerine dönüştürülmesi adımları izlenmiştir.

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

![Segmentlere Göre Ortalama Harcamalar](images/segmentlere_gore_ortalama_harcamalar.png)

*Yukarıdaki grafik, her müşteri segmentinin farklı ürün gruplarına yaptığı ortalama harcamaları göstermektedir. Özellikle Segment 0 ve 2'nin lüks ve çeşitli ürünlere yüksek harcama yaptığı, Segment 1'in ise tüm ürün gruplarında en düşük harcamaya sahip olduğu görülmektedir.*

### 2. Segmentlere Göre Kampanya Yanıt Oranları
- **Segment 0:** Kampanyalara en yüksek yanıt oranına sahip segment. Özellikle bazı kampanyalarda %100'e yakın yanıt oranı var.
- **Segment 2:** Kampanya yanıt oranları Segment 0'a göre daha düşük ama yine de diğer segmentlere göre yüksek.
- **Segment 3:** Kampanya yanıt oranları düşük-orta seviyede.
- **Segment 1:** Tüm kampanyalarda en düşük yanıt oranına sahip segment.

**İş Açısından:** Segment 0, pazarlama kampanyalarına en duyarlı müşteri grubu. Bu segmentte kişiselleştirilmiş ve özel kampanyalar çok etkili olabilir. Segment 2 de kampanyalara duyarlı, ancak Segment 1 ve 3'te kampanya etkisi sınırlı.

![Segmentlere Göre Kampanya Yanıt Oranları](images/segmentlere_gore_kampanya_yanit_orani.png)

*Bu görsel, her segmentin pazarlama kampanyalarına verdiği yanıt oranlarını göstermektedir. Segment 0 kampanyalara en yüksek yanıtı verirken, Segment 1 en düşük yanıt oranına sahiptir. Segment 2 ise orta-üst seviyede kampanya duyarlılığı göstermektedir.*

### 3. Segmentlere Göre Alışveriş Kanalı Tercihleri
- **Segment 2:** Katalog ve mağaza alışverişlerinde en yüksek ortalamaya sahip. Geleneksel alışveriş kanallarını tercih ediyor.
- **Segment 0:** Mağaza ve katalog alışverişlerinde yüksek, web alışverişinde ise Segment 2'ye yakın.
- **Segment 3:** Mağaza alışverişinde yüksek, katalogda Segment 2 ve 0'ın gerisinde.
- **Segment 1:** Web ziyaretlerinde ve web alışverişinde öne çıkıyor, ancak katalog ve mağaza alışverişlerinde düşük.

**İş Açısından:** Segment 2 ve 0, fiziksel mağaza ve katalog kanallarında aktif. Segment 1 ise dijital kanallarda daha aktif, ancak genel alışveriş hacmi düşük. Segment 3 ise mağaza alışverişine yatkın, katalogda ise daha az aktif.

![Segmentlere Göre Alışveriş Kanalı Tercihleri](images/segmentlere_gore_alisveris_kanali_tercihleri.png)

*Bu grafik, müşteri segmentlerinin alışveriş kanalı tercihlerine göre (mağaza, web, katalog) dağılımını göstermektedir. Segment 2 ve 0 fiziksel mağaza ve katalogda aktifken, Segment 1 dijital kanallarda daha aktiftir.*

### 4. Segmentlerin Yaş ve Gelir Ekseni Üzerinde Dağılımı
- **Segment 0 ve 2:** Yüksek gelirli müşterilerden oluşuyor. Segment 2, yaş olarak daha geniş bir aralığa yayılmış.
- **Segment 1:** Düşük gelirli ve daha genç müşterilerden oluşuyor. Yaş ve gelir açısından kümelenmiş durumda.
- **Segment 3:** Orta gelirli ve yaşça daha olgun müşterilerden oluşuyor. Segment 0 ve 2'ye göre daha düşük gelirli.

**İş Açısından:** Segment 0 ve 2, yüksek gelirli ve yaşça olgun müşteri kitlesiyle lüks ve premium ürünler için hedeflenebilir. Segment 1, genç ve düşük gelirli müşteri kitlesiyle fiyat odaklı kampanyalar için uygun. Segment 3 ise orta gelirli, geleneksel müşteri profiliyle aile ve güven temalı kampanyalara uygun.

![Segmentlere Göre Gelir Dağılımı](images/segmentlere_gore_gelir_dagilimi.png)

*Her segmentin gelir dağılımını gösteren bu grafik, Segment 0 ve 2'nin yüksek gelirli müşterilerden oluştuğunu, Segment 1'in ise düşük gelirli müşteri kitlesine sahip olduğunu ortaya koymaktadır.*

![Segmentlere Göre Yaş Dağılımı](images/segmentlere_gore_yas_dagılımı.png)

*Bu görsel, müşteri segmentlerinin yaş dağılımını göstermektedir. Segment 2'nin yaş aralığı daha genişken, Segment 1 genç müşteri kitlesinden oluşmaktadır. Segment 0 ve 3 ise daha olgun yaş gruplarını temsil etmektedir.*

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