# egik_prizma

Bu repo, **Eğik Prizma** konusu için hazırlanmış **tarayıcı tabanlı, etkileşimli bir eğitim materyalini** içerir.  
Uygulama **tek sayfalık bir HTML dosyası** olarak geliştirilmiştir ve **3B prizma görüntüleyici**, **açınım (net) görünümü** ve **adım adım etkinlikler** sunar.

---

## Özellikler

### 1. Etkileşimli 3B Eğik Prizma (Three.js)
- **Sürükle-bırak ile döndürme**, **scroll/pinch ile zoom**
- Köşe etiketleri ve kenar/vurgu yapıları ile daha iyi görselleştirme
- Görünümü sıfırlama (reset)

### 2. Açınım (Net) Görünümü
- **3B görünüm** ile **açınım görünümü** arasında geçiş
- Açınımın animasyonlu gösterimi
- Yüz ilişkilerini öğrenmeyi destekleyen yapı

### 3. Ölçüm Araçları
- **Ayrıt ölçme** (cetvel animasyonu ve sonuç paneli)
- **Açı ölçme** (3 köşe noktası seçerek açı hesaplama)

### 4. Yüz Boyama
- Renk paleti ile yüzleri boyama
- Boyaları sıfırlama
- Açınım üzerinde boyama ve tekrar prizmaya dönüştürme akışı

### 5. Yönlendirmeli Öğrenme Akışı (Uygulamalar)
- Sol panelde sekmeli etkinlik yapısı:
  - **Uygulama 1:** Yüzeyleri belirleme ve açınımı tanıma
  - **Uygulama 2:** Yüzey alanı odaklı çalışmalar / ölçme-değerlendirme sorusu
  - **Uygulama 3:** Hacim odaklı çalışmalar ve gerçek hayattan örnek diyalogları
  - **Serbest:** Serbest keşif ve etkileşim (akışa bağlı olarak)

### 6. Matematik & İçerik Desteği
- **MathJax** ile matematiksel gösterim
- Diyalog pencereleri ile soru-cevap ve kısa değerlendirmeler
- `images/` klasöründeki görsellerle desteklenen içerikler

---

## Proje Yapısı

- `index.html` — uygulamanın tamamı (HTML/CSS/JS tek dosya)
- `images/` — diyalog ve sorularda kullanılan görseller (örn. Kuril Adaları, sundurma, soru görseli)

---

## Başlangıç

Uygulamayı yerelde çalıştırmak için:

1. Repoyu klonlayın:
   ```bash
   git clone https://github.com/miyigun/egik_prizma.git
   ```

2. Klasöre girin:
   ```bash
   cd egik_prizma
   ```

3. Uygulamayı açın:
   - En kolay: `index.html` dosyasını tarayıcıda açın
   - Önerilen: local server ile çalıştırın (tarayıcı güvenlik kısıtlarını önler)

   Örnek (Python):
   ```bash
   python -m http.server 8000
   ```
   Sonra şurayı açın:
   - `http://localhost:8000`

---

## 🛠️ Kullanılan Teknolojiler
- HTML / CSS / JavaScript
- Three.js (3B modelleme/görüntüleme)
- MathJax (matematiksel ifadeler)
- jQuery (arayüz ve olay yönetimi)

---

## 📌 Notlar
- Uygulama **standalone** bir HTML dosyası olduğu için ayrıca build adımı yoktur.
- Diyaloglardaki görsellerin düzgün görünmesi için `images/` klasörünün konumu doğru olmalıdır.

---

## 📜 Lisans
Bu proje MIT lisansı altında sunulmaktadır. Ayrıntılar için LICENSE dosyasına bakınız.