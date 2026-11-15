# Makine Öğrenmesi Nedir?

## 1. Yapay Zekâ Nedir?

**Artificial Intelligence (AI) / Yapay Zekâ**, bilgisayarların normalde insan zekâsı gerektiren görevleri gerçekleştirebilmesini amaçlayan geniş bir alandır.

Örneğin:

- Görüntü tanıma
- Ses tanıma
- Dil anlama
- Karar verme
- Tahmin yapma
- Problem çözme

Yapay zekâ oldukça geniş bir kavramdır.

Makine öğrenmesi ise yapay zekânın önemli bir alt alanıdır.

```text
Artificial Intelligence (AI)
│
└── Machine Learning (ML)
    │
    └── Deep Learning (DL)
```

Burada:

- **AI** → en geniş alan
- **ML** → makinelerin veriden öğrenmesini sağlayan yaklaşım
- **DL** → yapay sinir ağlarını ve çok katmanlı modelleri kullanan makine öğrenmesi yaklaşımı

---

## 2. Machine Learning Nedir?

**Machine Learning (ML) / Makine Öğrenmesi**, bilgisayarların açıkça her kural tek tek programlanmadan, verilerden örüntüler öğrenerek tahmin veya karar vermesini sağlayan bir yöntemdir.

Buradaki önemli nokta şudur:

> Makine öğrenmesinde bilgisayara her durumda ne yapacağını tek tek söylemek yerine, ona veriler gösterilir ve verilerden bir ilişki öğrenmesi sağlanır.

---

## 3. Klasik Programlama ile Makine Öğrenmesi Arasındaki Fark

Klasik programlamada genellikle elimizde:

```text
Kurallar + Veri
      ↓
   Program
      ↓
    Çıktı
```

bulunur.

Örneğin bir öğrencinin geçip geçmediğini belirleyen bir program yazabiliriz:

```text
Eğer not >= 50 ise
    geçti
Değilse
    kaldı
```

Burada kuralı insan belirler.

Makine öğrenmesinde ise yaklaşım farklıdır:

```text
Veri + Doğru Cevaplar
          ↓
        Model
          ↓
    Öğrenilen Kurallar
```

Model, örneklerden bir ilişki öğrenmeye çalışır.

---

## 4. Basit Bir Örnek

Bir öğrencinin sınavdan kaç puan alacağını tahmin etmek istediğimizi düşünelim.

Elimizde daha önceki öğrencilerden oluşan bir veri olsun:

| Çalışma Saati | Sınav Notu |
|---:|---:|
| 1 | 45 |
| 2 | 52 |
| 3 | 61 |
| 5 | 74 |
| 7 | 88 |
| 9 | 95 |

Burada:

- `Çalışma Saati` → Feature
- `Sınav Notu` → Target / Label

Model bu örnekleri inceleyerek çalışma süresi ile sınav notu arasında bir ilişki öğrenmeye çalışabilir.

Daha sonra:

```text
Çalışma Saati = 6
```

olan yeni bir öğrenci geldiğinde model bir tahminde bulunabilir.

Örneğin:

```text
Tahmin ≈ 82
```

Bu değer gerçek sonuç olmak zorunda değildir.

Modelin amacı, öğrendiği ilişkiyi kullanarak **makul bir tahmin** yapmaktır.

---

## 5. Model Nedir?

Makine öğrenmesinde **model**, verilerde bulunan ilişkileri ve örüntüleri kullanarak tahmin yapabilen öğrenilmiş yapıdır.

Basitçe:

```text
Girdi
  ↓
Model
  ↓
Tahmin
```

Örneğin:

```text
6 saat çalışma
      ↓
   Model
      ↓
   82 puan
```

Modelin kendisini bir "kural kitabı" gibi düşünebiliriz.

Ancak önemli bir fark vardır:

Bu kurallar çoğu durumda insan tarafından tek tek yazılmaz. Model, eğitim verilerini kullanarak uygun ilişkileri öğrenmeye çalışır.

---

## 6. Makine Gerçekte Ne Öğreniyor?

Burada önemli bir soru ortaya çıkar:

> "Makine öğreniyor" derken tam olarak ne öğreniyor?

Model, veriler içerisindeki **örüntüleri (patterns)** ve değişkenler arasındaki ilişkileri öğrenmeye çalışır.

Örneğin:

```text
Çalışma saati arttıkça
        ↓
Sınav notu genellikle artıyor
```

Model bu ilişkiyi kullanarak yeni veriler için tahmin üretir.

Fakat model yalnızca ezber yaparsa yeni verilerde başarısız olabilir.

Bu nedenle amaç yalnızca eğitim verisini hatırlamak değildir.

Amaç:

> Öğrendiği ilişkileri daha önce görmediği verilere de uygulayabilmesidir.

Buna **generalization (genelleme)** denir.

---

## 7. Machine Learning Neden Kullanılır?

Makine öğrenmesi özellikle kuralların elle yazılmasının zor olduğu problemlerde oldukça kullanışlıdır.

Örneğin:

### Görüntü sınıflandırma

```text
Görüntü
   ↓
Model
   ↓
Kedi / Köpek
```

### Spam tespiti

```text
E-posta
   ↓
Model
   ↓
Spam / Normal
```

### Hastalık tahmini

```text
Hasta verileri
      ↓
    Model
      ↓
Tahmin
```

### Dolandırıcılık tespiti

```text
İşlem verileri
      ↓
    Model
      ↓
Normal / Şüpheli
```

Bu problemlerde milyonlarca olası durum bulunabileceği için bütün kuralları elle yazmak oldukça zor olabilir.

---

## 8. Makine Öğrenmesinin Temel Mantığı

Makine öğrenmesinin temel sürecini çok basitleştirirsek:

```text
Veri
 ↓
Model
 ↓
Tahmin
 ↓
Hata
 ↓
Modeli güncelle
 ↓
Tekrar tahmin
 ↓
Tekrar hata
 ↓
...
```

Model, yaptığı tahmin ile gerçek sonuç arasındaki farkı kullanarak kendisini geliştirmeye çalışır.

Bu süreç ilerleyen bölümlerde daha ayrıntılı incelenecektir.

---

## 9. Kısaca

Makine öğrenmesi:

- Verilerden yararlanır.
- Veriler içerisindeki örüntüleri öğrenmeye çalışır.
- Öğrendiği ilişkileri kullanarak tahmin yapar.
- Tahmin hatalarını kullanarak modelini geliştirebilir.
- Amaç yalnızca eğitim verisini ezberlemek değil, yeni veriler üzerinde de başarılı olmaktır.

Bir sonraki bölümde makine öğrenmesinin temel yapı taşlarından olan **Data, Sample, Feature ve Label** kavramlarını inceleyeceğiz.
