# Overfitting ve Underfitting

Bir makine öğrenmesi modelinin amacı yalnızca eğitim verisinde başarılı olmak değildir.

Asıl amaç:

> Daha önce görmediği yeni veriler üzerinde de doğru ve güvenilir tahminler yapabilmektir.

Bu noktada iki önemli problem ortaya çıkar:

- **Overfitting**
- **Underfitting**

---

# 1. Overfitting Nedir?

**Overfitting (Aşırı Öğrenme / Aşırı Uyum)**, modelin eğitim verisini gereğinden fazla öğrenerek adeta ezberlemesi ve yeni verilerde başarısının düşmesi durumudur.

Basitçe:

```text
Training Performance → Çok iyi
Test Performance     → Kötü
```

şeklinde bir durum oluşabilir.

---

# 2. Overfitting Nasıl Oluşur?

Bir modelin çok karmaşık olduğunu düşünelim.

Eğitim verisindeki gerçek örüntüleri öğrenmek yerine:

- Gürültüyü
- Tesadüfi ilişkileri
- Veriye özgü ayrıntıları

da öğrenmeye başlayabilir.

Örneğin:

```text
Gerçek örüntü:
Çalışma süresi arttıkça not genellikle artıyor.
```

Model bunu öğrenmek yerine eğitim verisindeki her küçük istisnayı da ezberlerse yeni öğrenciler geldiğinde başarısız olabilir.

---

# 3. Overfitting Örneği

Bir model eğitim verisinde:

```text
%99 doğruluk
```

elde ediyor olsun.

Ancak daha önce görmediği test verisinde:

```text
%65 doğruluk
```

elde ediyorsa modelin training verisine aşırı uyum sağlamış olma ihtimali vardır.

Burada tek başına bu sayılardan kesin bir teşhis koyamayız, ancak büyük bir performans farkı overfitting için önemli bir işarettir.

---

# 4. Underfitting Nedir?

**Underfitting (Yetersiz Öğrenme / Yetersiz Uyum)**, modelin verideki temel ilişkileri bile yeterince öğrenememesi durumudur.

Bu durumda model hem training hem de test verisinde düşük performans gösterebilir.

Örneğin:

```text
Training Performance → Kötü
Test Performance     → Kötü
```

olabilir.

---

# 5. Underfitting Neden Oluşabilir?

Model gereğinden fazla basit olabilir.

Örneğin problem oldukça karmaşıkken çok basit bir model kullanırsak verideki önemli ilişkileri yakalayamayabilir.

Ayrıca:

- Yetersiz eğitim
- Uygun olmayan özellikler
- Fazla kısıtlanmış model
- Yetersiz veri

gibi durumlar da etkili olabilir.

---

# 6. İkisini Karşılaştıralım

```text
Underfitting
     ↓
Model yeterince öğrenemiyor

Good Fit
     ↓
Model önemli örüntüleri öğreniyor

Overfitting
     ↓
Model eğitim verisini fazla öğreniyor
```

Basit bir tablo:

| Durum | Training | Test / Yeni Veri |
|---|---|---|
| Underfitting | Kötü | Kötü |
| İyi Uyum | İyi | İyi |
| Overfitting | Çok iyi | Kötü |

Buradaki amaç:

```text
Ne çok az öğrenmek
        ↓
Ne de veriyi ezberlemek
        ↓
Genelleme yapabilmek
```

---

# 7. Generalization Nedir?

**Generalization (Genelleme)**, modelin eğitim sırasında öğrendiği ilişkileri daha önce görmediği verilere uygulayabilme yeteneğidir.

Aslında makine öğrenmesindeki en önemli hedeflerden biri budur.

Örneğin model:

```text
Training Data
     ↓
Öğrenme
     ↓
Genel örüntüler
     ↓
Yeni Data
     ↓
Başarılı tahmin
```

yapabiliyorsa iyi bir genelleme yapıyor demektir.

---

# 8. Ezberlemek ve Öğrenmek Arasındaki Fark

Bu ayrımı anlamak çok önemlidir.

Bir öğrencinin sınavdaki bütün soruların cevaplarını ezberlediğini düşün.

Sınavda aynı sorular gelirse:

```text
Çok başarılı olabilir.
```

Ama sorular biraz değiştirilirse:

```text
Zorlanabilir.
```

Bu durumda öğrenci konuyu gerçekten anlamaktan çok soruları ezberlemiştir.

Overfitting de buna benzer bir durumdur.

Model:

```text
Eğitim verisini çok iyi tanıyor
```

ama:

```text
Yeni veriye uyum sağlayamıyor.
```

---

# 9. Overfitting Nasıl Azaltılabilir?

Overfitting'i azaltmak için farklı yöntemler kullanılabilir.

Örneğin:

- Daha fazla eğitim verisi kullanmak
- Modeli daha basit hale getirmek
- Regularization kullanmak
- Uygun feature seçimi yapmak
- Data augmentation kullanmak
- Early stopping kullanmak
- Cross-validation kullanmak

Kullanılacak yöntem probleme ve modele göre değişir.

---

# 10. Underfitting Nasıl Azaltılabilir?

Underfitting durumunda modelin öğrenme kapasitesi yetersiz olabilir.

Örneğin:

- Daha karmaşık bir model kullanmak
- Daha uzun eğitim yapmak
- Daha anlamlı feature'lar kullanmak
- Uygun hyperparameter ayarları yapmak

gibi yöntemler değerlendirilebilir.

---

# 11. Modelin İdeal Durumu

İdeal durumda model:

```text
Training Data
      ↓
Önemli örüntüleri öğrenir
      ↓
Gürültüyü ezberlemez
      ↓
Yeni veriye uygulanabilir
      ↓
İyi Generalization
```

elde eder.

Bu nedenle yalnızca:

> "Training accuracy kaç?"

sorusuna bakmak yeterli değildir.

Asıl önemli sorulardan biri:

> "Model daha önce görmediği veriler üzerinde nasıl performans gösteriyor?"

sorusudur.

---

# 12. Bias ve Variance ile İlişkisi

Overfitting ve underfitting konuları **Bias-Variance Tradeoff** kavramıyla da ilişkilidir.

Basitleştirilmiş şekilde:

```text
Underfitting
    ↓
High Bias

Overfitting
    ↓
High Variance
```

şeklinde düşünebiliriz.

Bu konu ilerleyen bölümlerde daha ayrıntılı olarak incelenebilir.

---

# 13. Büyük Resim

Şimdiye kadar öğrendiğimiz kavramları birleştirelim:

```text
DATA
 ↓
FEATURES + LABELS
 ↓
MODEL
 ↓
PREDICTION
 ↓
LOSS
 ↓
PARAMETER UPDATE
 ↓
TRAINING
 ↓
VALIDATION
 ↓
TEST
 ↓
GENERALIZATION
```

Ve modelin karşılaşabileceği iki temel problem:

```text
UNDERFITTING
     ↓
Yeterince öğrenememe

OVERFITTING
     ↓
Fazla öğrenip ezberleme
```

İdeal hedef ise:

```text
GOOD FIT
   ↓
İyi öğrenme
   ↓
İyi generalization
```

---

# 14. Özet

**Underfitting:**

Model verideki önemli ilişkileri yeterince öğrenemez.

**Overfitting:**

Model eğitim verisini gereğinden fazla öğrenir ve yeni verilerde başarısı düşer.

**Generalization:**

Modelin öğrendiği bilgiyi yeni verilere uygulayabilmesidir.

Makine öğrenmesinin temel hedeflerinden biri:

> Eğitim verisini ezberlemek değil, verideki anlamlı örüntüleri öğrenerek yeni veriler üzerinde başarılı olmaktır.

Bu bölümle birlikte makine öğrenmesinin temel mantığını oluşturan yapı taşlarını tamamlamış olduk.

Sonraki bölümde artık **Supervised Learning, Unsupervised Learning ve Reinforcement Learning** gibi makine öğrenmesi türlerine geçebiliriz.
