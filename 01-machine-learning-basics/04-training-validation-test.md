# Training, Validation ve Test

Bir makine öğrenmesi modelini eğitirken bütün veriyi doğrudan modele verip sonucu değerlendirmek doğru bir yaklaşım değildir.

Modelin gerçekten öğrenip öğrenmediğini anlayabilmek için veri farklı amaçlarla ayrılır.

Temel olarak:

```text
Dataset
│
├── Training Set
├── Validation Set
└── Test Set
```

şeklinde bir yapı kullanılır.

---

# 1. Training Set

**Training Set (Eğitim Seti)**, modelin öğrenmek için kullandığı veridir.

Model:

```text
Training Data
      ↓
    Model
      ↓
 Tahmin
      ↓
   Loss
      ↓
Güncelleme
```

döngüsünü bu veriler üzerinde gerçekleştirir.

Yani modelin parametrelerini öğrenmesi için temel veri training set'tir.

---

# 2. Validation Set

**Validation Set (Doğrulama Seti)**, modelin eğitim sırasında ne kadar iyi performans gösterdiğini kontrol etmek ve model ayarlarını seçmek için kullanılır.

Örneğin:

- Learning rate
- Modelin karmaşıklığı
- Epoch sayısı
- Tree depth
- Batch size

gibi ayarlar değiştirilebilir.

Bu ayarlara genellikle **Hyperparameter (Hiperparametre)** denir.

Validation set, farklı ayarların sonuçlarını karşılaştırmaya yardımcı olur.

---

# 3. Test Set

**Test Set**, model geliştirme süreci tamamlandıktan sonra modelin daha önce görmediği veriler üzerindeki performansını değerlendirmek için kullanılır.

Önemli nokta:

> Test verisi modelin eğitim sürecinde kullanılmamalıdır.

Çünkü test verisini sürekli kullanarak model üzerinde karar verirsek, test verisine de uyum sağlamaya başlayabiliriz.

Bu durumda test seti artık gerçek anlamda bağımsız bir değerlendirme sağlayamaz.

---

# 4. Basit Bir Benzetme

Bir sınava hazırlandığını düşün.

### Training

Ders çalışıyorsun ve soruları çözüyorsun.

```text
Çalışma
 ↓
Öğrenme
 ↓
Alıştırma
```

### Validation

Deneme sınavı çözüyorsun.

Sonuçlara bakarak:

```text
Nerede eksik var?
Hangi konuyu tekrar etmeliyim?
```

diye karar veriyorsun.

### Test

Gerçek sınava giriyorsun.

Artık sınav sorularını önceden görmemiş olman gerekiyor.

Bu nedenle:

```text
Training → Öğren
Validation → Ayarla / kontrol et
Test → Son değerlendirme
```

şeklinde düşünebiliriz.

---

# 5. Veri Nasıl Bölünür?

Örneğin elimizde:

```text
10.000 sample
```

olsun.

Basit bir bölme:

```text
Training   → %70
Validation → %15
Test       → %15
```

olabilir.

Bu oranlar sabit bir kural değildir.

Veri setinin büyüklüğüne, probleme ve kullanılan yönteme göre farklı oranlar tercih edilebilir.

---

# 6. Neden Aynı Veriyi Kullanamıyoruz?

Çünkü modelin gerçekten genelleme yapıp yapmadığını görmek istiyoruz.

Örneğin model training verisindeki örnekleri çok iyi biliyor olabilir.

Ama daha önce görmediği bir veri geldiğinde başarısız olabilir.

Bu nedenle:

```text
Training
    ↓
Öğren
    ↓
Validation
    ↓
Modeli geliştir
    ↓
Test
    ↓
Gerçek performansı değerlendir
```

şeklinde bir süreç kullanılır.

---

# 7. Data Leakage

Burada önemli bir problemden bahsetmek gerekir:

**Data Leakage (Veri Sızıntısı)**.

Data leakage, modelin normalde erişmemesi gereken bilgilerden eğitim sırasında yararlanması durumudur.

Örneğin test verisinden gelen bilgilerin eğitim sürecine yanlışlıkla karışması modelin performansını olduğundan daha iyi gösterebilir.

Bu nedenle veri bölme işlemi dikkatli yapılmalıdır.

---

# 8. Özet

| Veri | Görevi |
|---|---|
| Training | Modeli eğitmek |
| Validation | Modeli ve ayarları geliştirmek |
| Test | Son performansı değerlendirmek |

Kısaca:

```text
Training
   ↓
Öğren

Validation
   ↓
Kontrol et ve ayarla

Test
   ↓
Son kez değerlendir
```

Bu ayrımın temel amacı modelin yalnızca eğitim verisini ezberleyip ezberlemediğini değil, **yeni veriler üzerinde de başarılı olup olmadığını** görebilmektir.

Bir sonraki bölümde modelin eğitim verisini fazla öğrenmesi veya yeterince öğrenememesi durumlarını inceleyeceğiz:

**Overfitting ve Underfitting.**
