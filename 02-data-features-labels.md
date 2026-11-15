# Data, Sample, Feature ve Label

Makine öğrenmesinin temelinde **data (veri)** bulunur.

Bir modelin öğrenebilmesi için öncelikle öğrenebileceği verilere ihtiyacı vardır.

Bu nedenle:

```text
Data
 ↓
Features + Labels
 ↓
Model
```

ilişkisini anlamak oldukça önemlidir.

---

## 1. Dataset Nedir?

**Dataset (Veri Seti)**, makine öğrenmesi modelinin eğitiminde veya değerlendirilmesinde kullanılan verilerin tamamına verilen isimdir.

Örneğin öğrencilerin sınav sonuçlarını içeren bir veri setimiz olabilir:

| Öğrenci | Çalışma Saati | Devamsızlık | Sınav Notu |
|---|---:|---:|---:|
| A | 2 | 3 | 55 |
| B | 5 | 1 | 78 |
| C | 7 | 0 | 91 |
| D | 3 | 4 | 62 |

Bu tablonun tamamı bir **dataset** olabilir.

---

## 2. Sample / Instance Nedir?

Dataset içerisindeki her bir örneğe **Sample**, **Instance** veya bazı kaynaklarda **Observation** denir.

Örneğin:

| Öğrenci | Çalışma Saati | Devamsızlık | Sınav Notu |
|---|---:|---:|---:|
| A | 2 | 3 | 55 |

Bu tek satır bir sample'dır.

Yani:

```text
Dataset
│
├── Sample 1
├── Sample 2
├── Sample 3
└── Sample 4
```

Örneğin elimizde 1000 öğrenci varsa dataset içerisinde 1000 sample bulunabilir.

---

# 3. Feature Nedir?

**Feature (Özellik)**, modelin tahmin yaparken kullandığı girdidir.

Örneğin sınav notunu tahmin etmek istediğimizi düşünelim:

| Çalışma Saati | Devamsızlık | Sınav Notu |
|---:|---:|---:|
| 2 | 3 | 55 |
| 5 | 1 | 78 |
| 7 | 0 | 91 |

Burada:

- `Çalışma Saati` → Feature
- `Devamsızlık` → Feature
- `Sınav Notu` → Label / Target

Model, feature'ları kullanarak target'ı tahmin etmeye çalışır.

```text
Çalışma Saati ──┐
                ├──> Model ──> Sınav Notu
Devamsızlık ────┘
```

---

# 4. Feature Türleri

Feature'lar farklı veri tiplerinde olabilir.

Temel olarak:

```text
Feature
│
├── Numerical Feature
│
└── Categorical Feature
```

şeklinde düşünebiliriz.

---

## 4.1 Numerical Feature

**Numerical Feature**, sayısal değerlerden oluşan feature'dır.

Örneğin:

- Yaş
- Boy
- Kilo
- Sıcaklık
- Maaş
- Oda sayısı

### Continuous Feature

Sürekli değerler alabilen sayısal feature'lardır.

Örneğin:

```text
Boy = 158.2 cm
Boy = 158.25 cm
Boy = 158.253 cm
```

Teorik olarak iki değer arasında çok sayıda değer bulunabilir.

Bunlara **Continuous Feature** denir.

### Discrete Feature

Sayılabilir değerlerden oluşan feature'lardır.

Örneğin:

```text
Oda sayısı = 1
Oda sayısı = 2
Oda sayısı = 3
```

Genellikle ara değerler anlamlı değildir.

Örneğin:

```text
2.37 oda
```

gibi bir değer kullanmayız.

Bunlara **Discrete Feature** denir.

---

# 5. Categorical Feature

**Categorical Feature**, değerleri belirli kategorilerden oluşan feature'dır.

Örneğin:

```text
Şehir:
İstanbul
Ankara
Elazığ
İzmir
```

Buradaki şehir isimleri sayısal bir ölçüm değildir.

Başka örnekler:

- Cinsiyet
- Şehir
- Renk
- Marka
- Ürün türü

Categorical feature'ların iki önemli türü vardır:

```text
Categorical
│
├── Nominal
└── Ordinal
```

---

## 5.1 Nominal Feature

**Nominal Feature**, kategoriler arasında doğal bir sıralamanın olmadığı feature'dır.

Örneğin:

```text
Renk:
Kırmızı
Mavi
Yeşil
Sarı
```

Bu renkleri:

```text
Mavi < Yeşil < Sarı
```

şeklinde anlamlı biçimde sıralayamayız.

Bu nedenle nominal kategorik feature'dır.

---

## 5.2 Ordinal Feature

**Ordinal Feature**, kategoriler arasında anlamlı bir sıralamanın bulunduğu feature'dır.

Örneğin:

```text
Memnuniyet:
Düşük
Orta
Yüksek
```

Burada:

```text
Düşük < Orta < Yüksek
```

şeklinde anlamlı bir sıralama vardır.

Başka bir örnek:

```text
Eğitim Seviyesi:

Lise
Lisans
Yüksek Lisans
Doktora
```

Burada da bir sıralama vardır.

---

# 6. Neden Feature Türünü Bilmemiz Gerekiyor?

Çünkü makine öğrenmesi modelleri verileri doğrudan insan gibi yorumlamaz.

Örneğin:

```text
Şehir:

İstanbul
Ankara
Elazığ
```

değerlerini model doğrudan matematiksel olarak kullanamaz.

Bu nedenle kategorik veriler çoğu zaman uygun bir biçime dönüştürülür.

Bu işleme **Encoding** denir.

Örneğin:

```text
İstanbul
Ankara
Elazığ
```

verisi uygun bir yöntemle sayısal temsile dönüştürülebilir.

Ancak burada dikkat edilmesi gereken önemli bir nokta vardır.

Eğer:

```text
İstanbul = 1
Ankara = 2
Elazığ = 3
```

şeklinde kodlama yaparsak model bu sayıları gerçek bir sıralama gibi yorumlayabilir.

Oysa:

```text
İstanbul < Ankara < Elazığ
```

gibi bir anlam yoktur.

Bu nedenle kategorik verinin türüne uygun encoding yöntemi seçilmelidir.

---

# 7. Label / Target Nedir?

**Label** veya **Target**, modelin tahmin etmeye çalıştığı değerdir.

Örneğin:

| Çalışma Saati | Devamsızlık | Sınav Notu |
|---:|---:|---:|
| 2 | 3 | 55 |
| 5 | 1 | 78 |
| 7 | 0 | 91 |

Burada:

```text
Features:
- Çalışma Saati
- Devamsızlık

Target:
- Sınav Notu
```

Modelin görevi:

```text
Features
   ↓
Model
   ↓
Target tahmini
```

yapmaktır.

---

# 8. Feature ve Label Arasındaki Fark

En kolay şekilde şöyle düşünebiliriz:

> **Feature = Modelin baktığı şey**

> **Label / Target = Modelin bulmaya çalıştığı şey**

Örneğin ev fiyatı tahmini:

```text
Metrekare ───────┐
Oda Sayısı ──────┤
Bina Yaşı ───────┼──> Model ──> Ev Fiyatı
Kat ─────────────┘
```

Burada:

- Metrekare → Feature
- Oda Sayısı → Feature
- Bina Yaşı → Feature
- Kat → Feature
- Ev Fiyatı → Target

---

# 9. X ve y Nedir?

Makine öğrenmesinde sık sık:

```text
X
y
```

ifadelerini göreceğiz.

Genellikle:

```text
X = Features
y = Target / Label
```

şeklinde kullanılır.

Örneğin:

```text
X:
Çalışma Saati
Devamsızlık

y:
Sınav Notu
```

Yani:

```text
X ──> Model ──> y tahmini
```

şeklinde düşünebiliriz.

---

# 10. Özet

Makine öğrenmesindeki temel veri kavramları:

| Kavram | Anlamı |
|---|---|
| Dataset | Veri setinin tamamı |
| Sample / Instance | Veri setindeki tek örnek |
| Feature | Modelin kullandığı girdi/özellik |
| Label / Target | Modelin tahmin etmeye çalıştığı çıktı |
| X | Genellikle feature'lar |
| y | Genellikle target/label |

Feature'lar ise temel olarak:

```text
Feature
│
├── Numerical
│   ├── Continuous
│   └── Discrete
│
└── Categorical
    ├── Nominal
    └── Ordinal
```

şeklinde sınıflandırılabilir.

Bir sonraki bölümde modelin bu feature'ları kullanarak **nasıl öğrendiğini** inceleyeceğiz.
