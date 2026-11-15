# Bir Makine Öğrenmesi Modeli Nasıl Öğrenir?

Makine öğrenmesindeki en önemli sorulardan biri şudur:

> Bir model gerçekten nasıl öğreniyor?

"Model verilerden öğrenir" demek tek başına yeterli değildir.

Modelin nasıl bir süreçten geçtiğini adım adım inceleyelim.

---

# 1. Temel Öğrenme Döngüsü

Bir makine öğrenmesi modelinin öğrenme sürecini basitleştirirsek:

```text
Veriyi al
   ↓
Tahmin yap
   ↓
Tahmini gerçek sonuçla karşılaştır
   ↓
Hata miktarını hesapla
   ↓
Modeli güncelle
   ↓
Tekrar tahmin yap
   ↓
...
```

Bu işlem birçok kez tekrar edilir.

Amaç, modelin yaptığı hataları zaman içerisinde azaltmaktır.

---

# 2. Modelin Elinde Ne Var?

Bir modelin eğitim sırasında temel olarak:

- Feature'lar
- Gerçek sonuçlar
- Öğrenilebilir parametreler

ile çalıştığını düşünebiliriz.

Örneğin ev fiyatı tahmin ediyoruz:

```text
Feature'lar:

Metrekare
Oda Sayısı
Bina Yaşı
```

Target:

```text
Ev Fiyatı
```

Model bu feature'ları kullanarak bir fiyat tahmin eder.

---

# 3. Prediction

Modelin ürettiği sonuca **Prediction (Tahmin)** denir.

Örneğin gerçek ev fiyatı:

```text
Gerçek fiyat = 3.000.000 TL
```

Modelin tahmini:

```text
Tahmin = 2.700.000 TL
```

olabilir.

Model burada henüz mükemmel değildir.

Çünkü tahmini ile gerçek değer arasında fark vardır.

---

# 4. Error / Loss

Tahmin ile gerçek sonuç arasındaki farkı değerlendirmek için bir **Loss Function (Kayıp Fonksiyonu)** kullanılır.

Basitçe:

```text
Gerçek Değer
      ↓
   Karşılaştır
      ↑
    Tahmin
```

ve:

```text
Tahmin ile gerçek sonuç arasındaki fark
                ↓
              Loss
```

şeklinde düşünebiliriz.

Loss bize modelin ne kadar kötü tahmin yaptığını ifade eden bir ölçü sağlar.

Örneğin:

```text
Gerçek = 3.000.000
Tahmin = 2.700.000
```

Modelin tahmini ile gerçek değer arasında fark vardır.

Model eğitim sırasında bu hatayı azaltmaya çalışır.

---

# 5. Modelin İçindeki Parametreler

Peki model tahminini nasıl değiştiriyor?

Modelin içerisinde öğrenilebilen bazı **parameters (parametreler)** bulunur.

Örneğin:

- Weight
- Bias

gibi parametreler modelin davranışını belirler.

Basit bir model düşünelim:

```text
Feature
   ↓
Weight
   ↓
Model
   ↓
Prediction
```

Model, eğitim sırasında bu parametrelerin değerlerini değiştirerek daha iyi tahminler üretmeye çalışır.

---

# 6. Weight Nedir?

**Weight (Ağırlık)**, bir feature'ın model üzerindeki etkisini belirleyen öğrenilebilir bir parametredir.

Örneğin:

```text
Ev fiyatı tahmini

Metrekare ──> Weight
Oda Sayısı ─> Weight
Bina Yaşı ──> Weight
```

Model eğitim sırasında bu ağırlıkları değiştirebilir.

Örneğin model şunu öğrenebilir:

```text
Metrekare çok önemli
Oda sayısı önemli
Bina yaşı da etkili
```

Buradaki "önem" doğrudan insan tarafından verilmez.

Model, eğitim verilerinden uygun parametreleri öğrenmeye çalışır.

---

# 7. Bias Nedir?

**Bias (Yanlılık / Sabit terim)**, modelin tahminini ayarlamasına yardımcı olan öğrenilebilir bir parametredir.

Basitleştirilmiş şekilde:

```text
Feature
   ↓
Weight ile etkilenir
   ↓
Bias eklenir
   ↓
Tahmin
```

Bias, modelin yalnızca feature'ların etkisine bağlı kalmadan tahminini ayarlayabilmesini sağlar.

Bu kavram özellikle yapay sinir ağlarında çok önemli hale gelir.

---

# 8. Model Nasıl Güncelleniyor?

Şimdi en önemli noktaya geldik.

Model:

```text
1. Tahmin yapar
2. Loss hesaplar
3. Hatanın ne kadar olduğunu görür
4. Parametrelerini günceller
5. Tekrar tahmin yapar
```

Örneğin:

```text
İlk tahmin
↓
Loss = yüksek
↓
Parametreleri güncelle
↓
İkinci tahmin
↓
Loss = daha düşük
↓
Parametreleri tekrar güncelle
```

Bu süreç tekrarlandıkça model uygun parametreleri bulmaya çalışır.

---

# 9. Öğrenme Ne Demektir?

Burada "model öğreniyor" ifadesinin ne anlama geldiğini netleştirebiliriz.

Modelin insan gibi bilinçli şekilde öğrendiğini söylemiyoruz.

Makine öğrenmesinde öğrenme:

> Eğitim verisine göre modelin parametrelerini değiştirerek tahmin hatasını azaltması sürecidir.

Yani:

```text
Veri
 ↓
Tahmin
 ↓
Loss
 ↓
Parametre güncelleme
 ↓
Daha iyi tahmin
```

Bu döngü modelin öğrenme sürecinin temelini oluşturur.

---

# 10. Training Nedir?

Bu öğrenme sürecinin tamamına **Training (Eğitim)** denir.

Model eğitim verilerini kullanır.

```text
Training Data
      ↓
    Model
      ↓
 Prediction
      ↓
     Loss
      ↓
Parameter Update
      ↓
    Model
      ↓
   ...
```

Bu işlem birçok kez tekrarlanabilir.

---

# 11. Epoch Nedir?

Modelin eğitim verisinin tamamını bir kez görmesine genellikle **epoch** denir.

Örneğin elimizde:

```text
10.000 sample
```

olsun.

Model bu 10.000 örneği bir kez işlediğinde:

```text
1 epoch
```

tamamlanmış olur.

Eğer aynı eğitim verisi 10 kez işlenirse:

```text
10 epoch
```

olur.

Ancak daha fazla epoch her zaman daha iyi değildir.

Model eğitim verisini aşırı derecede ezberlemeye başlayabilir.

Bu durum **overfitting** ile ilişkilidir.

---

# 12. Batch Nedir?

Büyük veri setlerinde bütün veriyi aynı anda modele vermek her zaman uygun olmayabilir.

Bu nedenle veriler daha küçük gruplara ayrılabilir.

Bu gruplara **batch** denir.

Örneğin:

```text
Dataset = 10.000 sample
Batch size = 100
```

ise veri:

```text
100 sample
100 sample
100 sample
...
```

şeklinde küçük gruplar halinde işlenebilir.

---

# 13. Learning Rate Nedir?

Modelin parametrelerini güncellerken ne kadar büyük adımlar atacağını belirleyen önemli bir kavram da **Learning Rate (Öğrenme Oranı)**dır.

Basit bir benzetme:

Bir dağın tepesindesin ve en aşağıdaki noktayı bulmaya çalışıyorsun.

Çok büyük adımlar atarsan:

```text
Hedefi aşabilirsin.
```

Çok küçük adımlar atarsan:

```text
Hedefe ulaşman çok uzun sürebilir.
```

Learning rate de modelin parametrelerini güncellerken attığı adımın büyüklüğüyle ilişkilidir.

---

# 14. Gradient Descent

Modelin loss değerini azaltmak için kullanılan önemli yöntemlerden biri **Gradient Descent**'tir.

Basitleştirilmiş şekilde:

```text
Loss yüksek
   ↓
Hangi yönde azaltılabilir?
   ↓
Parametreleri uygun yönde değiştir
   ↓
Loss azalır
```

Gradient Descent'in ayrıntılı matematiğine ilerleyen bölümlerde ayrıca değinilecektir.

Şimdilik temel fikir şudur:

> Model, loss'u azaltacak yönde parametrelerini güncellemeye çalışır.

---

# 15. Küçük Bir Örnek

Bir modelin ilk tahmini:

```text
Gerçek değer = 100
Tahmin = 60
```

olsun.

Modelin hatası yüksektir.

Model parametrelerini günceller.

Sonraki tahmin:

```text
Tahmin = 80
```

Daha sonra:

```text
Tahmin = 92
```

Sonra:

```text
Tahmin = 98
```

gibi değerlere yaklaşabilir.

Bu yalnızca basitleştirilmiş bir örnektir. Gerçek modellerde öğrenme süreci bu kadar düz ve garantili ilerlemez.

Ancak temel mantık:

```text
Tahmin
  ↓
Hata
  ↓
Güncelleme
  ↓
Yeni tahmin
```

şeklindedir.

---

# 16. Büyük Resim

Artık makine öğrenmesinin temel öğrenme döngüsünü görebiliriz:

```text
                DATA
                  ↓
              FEATURES
                  ↓
                MODEL
                  ↓
              PREDICTION
                  ↓
         ┌────────┴────────┐
         ↓                 ↓
      TARGET          PREDICTION
         │                 │
         └───────┬─────────┘
                 ↓
               LOSS
                 ↓
        PARAMETER UPDATE
                 ↓
               MODEL
                 ↓
          tekrar tekrar...
```

Bu döngü sayesinde model eğitim verilerinden bir ilişki öğrenmeye çalışır.

---

# 17. Özet

Bir makine öğrenmesi modelinin öğrenme sürecini şu şekilde özetleyebiliriz:

```text
Data
 ↓
Feature'lar modele girer
 ↓
Model tahmin yapar
 ↓
Tahmin gerçek sonuçla karşılaştırılır
 ↓
Loss hesaplanır
 ↓
Model parametrelerini günceller
 ↓
Süreç tekrar edilir
```

Buradaki temel kavramlar:

- **Feature** → Modelin kullandığı girdi
- **Prediction** → Modelin tahmini
- **Target** → Gerçek hedef değer
- **Loss** → Tahminin ne kadar hatalı olduğunu ölçen değer
- **Parameter** → Modelin öğrenebildiği değerler
- **Weight** → Feature etkisini belirleyen parametre
- **Bias** → Modelin tahminini ayarlayan parametre
- **Training** → Modelin verilerden öğrenme süreci
- **Epoch** → Eğitim verisinin bir kez tamamen işlenmesi
- **Batch** → Eğitim sırasında kullanılan veri grubu
- **Learning Rate** → Parametre güncelleme adımının büyüklüğünü belirleyen değer

Bir sonraki bölümde modelin eğitim sırasında kullandığı verinin neden **Training, Validation ve Test** olarak ayrıldığını inceleyeceğiz.
