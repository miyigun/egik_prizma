# 11. Materyal: Eğik Prizma
## Üretici Test ve Matematiksel Doğrulama Notu

**Materyal ID:** 11_materyal_egik_prizma_murat (MAT-011)  
**Sürüm:** 1.3.6  
**Tarih:** 2026-10-06  
**Hedef TYMM Çıktıları:** MAT.12.3.1, MAT.12.3.3  
**Beceriler & Süreç Bileşenleri:** MAB3 (Matematiksel Akıl Yürütme), KB2.6 (Bilgi Toplama / Ölçme)  

---

### 1. Amaç ve Kapsam
Bu belge, MEB/OGM Materyal Denetim Heyeti tarafından iletilen **MAT-006, MAT-007, MAT-008, MAT-009, MAT-010 ve MAT-011 (MEB Koordinat Sistemi ve Sağ El Kuralı Uyumu)** numaralı inceleme ve revizyon maddelerine istinaden hazırlanmıştır. 

Belgede; 3B dikdörtgen tabanlı eğik prizma üzerinde yanal ayrıt uzunluğu ile cisim/yüz yüksekliği arasındaki trigonometrik ayrım, yanal yüzeylerin analitik alan hesaplamaları, Cavalieri ilkesiyle hacim bağıntısı, açınım animasyonu, MEB müfredatına tam uyumlu Z-up sağ el Kartezyen koordinat sistemi ve teknik kapıların (çevrimdışı yerel çalışma, klavye erişilebilirliği, önizleme kipi, tema uyumu) eksiksiz karşılandığı teorik, algoritmik ve deneysel kanıtlarla belgelenmektedir.

---

### 2. Eğik Prizma Analitik Koordinat ve Geometrik Hesap Matematiği

#### 2.1. MEB Müfredatına Göre Eksen Yerleşimi ve Koordinat Sistemi
MEB Ortaöğretim Matematik (11-12. Sınıf Uzay Geometri/Vektörler) ve Fizik müfredatına tam uyum sağlamak üzere 3B uzay koordinat eksenleri standartlaştırılmıştır:
* **Düşey (Dikey) Eksen ($z$ ekseni - Yeşil):** Kot / yükseklik ekseni.
* **Yatay Genişlik Ekseni ($y$ ekseni - Kırmızı):** Sağa doğru uzanan yatay doğrultu.
* **Derinlik Ekseni ($x$ ekseni - Mavi):** Bize / öne doğru uzanan doğrultu.
* **Sağ El Kuralı Doğrulaması:** $\vec{x}_{\text{öne}} \times \vec{y}_{\text{sağa}} = \vec{z}_{\text{yukarı}}$ tam olarak sağlanmaktadır.
* **Zemin (Taban) Düzlemi:** $xy$ düzlemidir ($z = 0$). Prizmanın tabanındaki tüm köşelerin kotu $z = 0$, tavan köşelerinin kotu ise $z = h$ olarak tanımlıdır.

Model, tabanı kare ($PW = 6\text{ cm}, PD = 6\text{ cm}$) ve yanal ayrıt uzunluğu $AE_{\text{len}} = 9\text{ cm}$ olan eğik prizmadır. Merkez orijin $(0,0,0)$ kabul edildiğinde, eğilme $\theta = 78^\circ$ açıyla gerçekleşir:

* **Yanal Ayrıt Yatay Bileşeni ($y$ ötelemesi):**
  $$AE_{\text{yatay}} = AE_{\text{len}} \cdot \cos(78^\circ) = 9 \cdot 0.2079 \approx 1.871\text{ cm}$$

* **Yanal Ayrıt Dikey Bileşeni (Yüzey Dik Yüksekliği $h$ - $z$ kotu):**
  $$h = AE_z = AE_{\text{len}} \cdot \sin(78^\circ) = 9 \cdot 0.9781 \approx 8.803\text{ cm} \approx 8.8\text{ cm}$$

Three.js `BufferGeometry` üzerinde tüm tepe noktaları, yüzey normalleri ve kenar çizgileri bu analitik matris üzerinden hatasız oluşturulmaktadır.

---

### 3. Alt Uygulama Matematiksel Tutarlılık Kanıtları

#### 3.1. Uygulama 1: Yüzeyleri Tanıma ve Açınım Matematiği (MAT.12.3.1)
* Eğik prizmanın 6 yüzeyi geometrik olarak şu sınıflara ayrılır:
  1. **2 Adet Kare Taban ($6 \times 6\text{ cm}$):** $A_{\text{taban}} = 6 \cdot 6 = 36\text{ cm}^2$ (Toplam $72\text{ cm}^2$)
  2. **2 Adet Dikdörtgen Yan Yüz ($6 \times 9\text{ cm}$):** $A_{\text{dikd}} = 6 \cdot 9 = 54\text{ cm}^2$ (Toplam $108\text{ cm}^2$)
  3. **2 Adet Paralelkenar Yan Yüz (Taban $6\text{ cm}$, Yanal Ayrıt $9\text{ cm}$, Eğim $78^\circ$):** 
     Tabana ait yükseklik $h = 9 \cdot \sin(78^\circ) \approx 8.8\text{ cm}$
* Açınım algoritması (`buildAnimatedNet`), bu 6 yüzeyi 2B düzlemde çakışmasız olarak açmakta ve 3D prizmaya dönüşüm animasyonunu trigonometrik katlanma açılarıyla canlı işletmektedir.

#### 3.2. Uygulama 2: Yüzey Alanı Hesabı ve Kenar-Yükseklik Ayrımı (MAT-006 / MAT.12.3.1)
* **Kritik Kavramsal Ayrım:** Paralelkenar yanal yüzde kenar uzunluğu ($9\text{ cm}$) doğrudan alan çarpanı olamaz. Dik yükseklik bileşeni ($h = 8.8\text{ cm}$) bulunmalıdır.
* **Adım Adım Bilişsel Hesaplama:**
  $$A_{\text{paralelkenar}} = \text{Taban} \times \text{Yükseklik} = 6 \times 8.8 = 52.8\text{ cm}^2$$
  $$A_{\text{toplam}} = 2 \cdot A_{\text{taban}} + 2 \cdot A_{\text{dikd}} + 2 \cdot A_{\text{paralelkenar}}$$
  $$A_{\text{toplam}} = (2 \times 36) + (2 \times 54) + (2 \times 52.8) = 72 + 108 + 105.6 = 285.6\text{ cm}^2$$
* Uygulama içi cetvel, açıölçer ve hesap makinesi araçları bu formülasyonla tam örtüşmektedir.

#### 3.3. Uygulama 3: Cavalieri İlkesi ve Hacim Bağıntısı (MAT-009 / MAT.12.3.3)
* **Teorem (Cavalieri İlkesi):** Taban alanları eşit ve yükseklikleri eşit olan iki prizmanın (biri dik, biri eğik olsa dahi) hacimleri birbirine eşittir.
* **Parametreler:**
  * Taban: Kare, $a = 4\text{ cm} \implies A_{\text{taban}} = 4 \times 4 = 16\text{ cm}^2$
  * Yanal Ayrıt: $L = 10\text{ cm}$, Eğim Açısı: $\alpha = 30^\circ$
  * Cisim Yüksekliği: $h = L \cdot \sin(30^\circ) = 10 \cdot 0.5 = 5\text{ cm}$
* **Hacim Hesabı:**
  $$V = A_{\text{taban}} \times h = 16 \times 5 = 80\text{ cm}^3$$
* Uygulamada dik prizma ile eğik prizmanın aynı taban ve aynı yükseklikteki kesit dilimleri karşılaştırmalı olarak gösterilmektedir.

---

### 4. Yönetim Kabul Koşulları Doğrulama Tablosu

| Kayıt No | Kategori / Öncelik | Yönetim Sorun ve Kabul Koşulu | Gerçekleştirilen Teknik Uygulama ve Kanıt | Sonuç |
| :--- | :--- | :--- | :--- | :--- |
| **MAT-006** | Pedagojik Akış (Orta) | Paralelkenar yanal yüzlerde kenar uzunluğu ile alan hesabını açık ayır. Bilişsel yük oluşturmamalı. | Uygulama 2 Adım 0-4'te $9\text{ cm}$ ayrıt ile $h=8.8\text{ cm}$ yükseklik adımlara ayrıldı. $\sin 78^\circ$ bağıntısı hesap makinesiyle hesaplatılarak toplam alan $285.6\text{ cm}^2$ olarak yapılandırıldı. | **BAŞARILI (100)** |
| **MAT-007** | Teknik / Kullanılabilirlik (Yüksek) | Harici jQuery/MathJax/Three bağımlılıklarını yerelleştir. Dış bağımlılık kalmamalı. | CDN fallback kodları tamamen kaldırıldı; kütüphaneler yerel `lib/` klasöründen çağrıldı. `materyal-denetim.py` statik taramasında 0 dış URL ile `VAR M1_yerel_paket` kanıtlandı. | **BAŞARILI (100)** |
| **MAT-008** | Varsayılan / Akış (Yüksek) | ? yönerge butonu, ?onizleme=1 ve reduced-motion ekle. Açılışta kısa yönerge/tema belirgin olmalı. | Floating alana `?` SVG butonu eklendi. `?onizleme=1` parametresi için `body.preview-mode` ile panellerden arındırılmış tam 3D vitrin katmanı entegre edildi. Varsayılan tema gündüz (`light`) yapıldı. `@media (prefers-reduced-motion: reduce)` eklendi. | **BAŞARILI (100)** |
| **MAT-009** | Pedagojik Akış (Orta) | Uzun akışı yüzey alanı ve hacim için iki ayrı değerlendirme düğümüne ayır. Kopuk geçiş kalmamalı. | Değerlendirme akışı ayrıldı: Uygulama 2 sonunda Yüzey Alanı Değerlendirmesi (`MAT.12.3.1`), Uygulama 3 sonunda Cavalieri ilkesi ve hacim değerlendirmesi (`MAT.12.3.3`) bağımsız pencereler olarak entegre edildi. | **BAŞARILI (100)** |
| **MAT-010** | Pedagojik Akış / Test (Orta) | Canlı testte boyama/ölçme butonlarının kilitlenme ve ilerleme koşullarını doğrula. | Boyama ve ölçme sayaçları tamamlanmadan ilerleme butonu açılmayacak şekilde koşullar bağlandı. Sıfırla butonunun boyaları silmesi engellendi. Sekmeler arası geçişte 3D tuvalin kararması/kapanması giderildi. | **BAŞARILI (100)** |

---

### 5. Kural Seti (v1.3.4) Kabul Kapıları Doğrulama Özeti

* **MS-01 & MS-02 (Manifest):** Kök dizinde geçerli ve 4 bloğu (`kimlik`, `matematik`, `teknik`, `program`) dolu `manifest.json` mevcuttur.
* **MS-03 & MS-04 (Öğrenme Dili):** TYMM-2026 `MAT.12.3.1` ve `MAT.12.3.3` kazanımları resmi manifest kaydına bağlanmıştır.
* **MS-05 (Önizleme Kipi):** `?onizleme=1` vitrin modu tam işlevli test edilmiştir.
* **MS-06 (Tema):** Gündüz varsayılan, gece kullanıcı seçimiyle çalışmaktadır.
* **MS-08 & MS-09 (Erişilebilirlik):** 3D prizma tuvali klavye ok tuşlarıyla (`ArrowUp/Down/Left/Right`), zoom tuşlarıyla (`+/-`) kontrol edilebilir durumdadır.

**Doğrulayan:** Murat İYİGÜN / MEB Materyal Ekibi  
**Denetim Tarihi:** 2026-09-10  

---

### 6. 2 Ekim 2026 Tema ve Önizleme Eki Test Doğrulaması (Kabul Kanıtları)

2 Ekim 2026 tarihli "Materyal Seti: Tema ve Önizleme Eki" yönergesi doğrultusunda yapılan revizyonlar ve yerel iframe test ortamında (`test_host.html`) gerçekleştirilen doğrulama sonuçları aşağıdadır:

#### 6.1. Paket Giriş Noktaları
* **Tam Materyal Çalışma Adresi:** `index.html`
* **Sade Önizleme Adresi:** `index.html?onizleme=1` (veya `&onizleme=1`)

#### 6.2. Tema Yönetimi ve PostMessage Köprüsü Doğrulaması
* **Ortak Değişkenler:** `--ms-bg`, `--ms-surface`, `--ms-surface-alt`, `--ms-text` ve `--ms-preview-bg` ortak renk değişkenleri hem açık (varsayılan) hem koyu temada eksiksiz tanımlanmıştır. Sayfaya toplu filtre/invert uygulanmamış, nesne ve matematiksel renklerin okunaklılığı korunmuştur.
* **matbis-theme El Sıkışması (Handshake):** Materyal iframe içine gömüldüğünde üst sayfaya `{"channel":"matbis-theme","type":"ready"}` mesajı iletilmiştir.
* **Dinamik Tema Geçişi:** Üst sayfadan gelen `{"channel":"matbis-theme","type":"set-theme","theme":"dark"}` ve `theme:"light"` mesajları anında işlenerek arayüz ve 3B sahne zemin ızgarası başarıyla güncellenmiştir.
* **İkinci Düğmenin Gizlenmesi:** Siteden tema sinyali alındığında materyalin kendi `#themeToggle` butonu otomatik gizlenmiştir.
* **Bağımsız Kullanım:** Bağımsız çalıştırmada kullanıcının tema tercihi `localStorage` üzerinden korunmakta; siteden gelen tercihler yerel tercihi ezmemektedir.
* **Durum Korunumu:** Tema geçişi sırasında 3B kamera açısı/uzaklığı, çizim adımı, ölçümler ve kullanıcı cevapları sıfırlanmamaktadır.
* **Güvenlik & Origin:** `document.referrer`, ana pencere kökeni ve MEB/EBA alan adları (`*.eba.gov.tr`, `*.meb.gov.tr`) haricindeki kökenlerden gelen yetkisiz mesajlar engellenmiştir.

#### 6.3. Sade Önizleme Kipi (`index.html?onizleme=1`)
* **Sade Matematiksel Temsil:** Önizleme modunda uzun yönergeler, araç panelleri, bilgi diyaloğu (`#infoDialog`), hesap makinesi, cetvel/açıölçer ve arka plan dekoratif SVG animasyonları tamamen gizlenerek ortalanmış tek 3B eğik prizma sunulmuştur.
* **Düz Nötr Fon:** Saman sarısı, bej veya gradyan yerine temaya uygun düz nötr zemin (`--ms-preview-bg`) kullanılmıştır.
* **Çalışmayı Aç Bağlantısı:** Sağ üst köşede göze batmayan, `_top` hedefli ve tam çalışmaya yönlendiren "Çalışmayı Aç ↗" bağlantısı konumlandırılmıştır.
* **İlerleme/Cevap İzolasyonu:** Önizleme kipi öğrenci ilerlemesini veya cevaplarını değiştirmemektedir.

#### 6.4. Ekran Boyutları ve Duyarlılık (Responsive) Test Matrisi

| Test Boyutu | Kapsam / Ortam | Beklenen Davranış | Gerçekleşen Sonuç | Durum |
| :--- | :--- | :--- | :--- | :--- |
| **240 × 240** (Kare) | Önizleme (`?onizleme=1`) | Prizma ortalanmalı, kesilmemeli, kaydırma çubuğu olmamalı | Model tam ortalandı, fov dinamik uyarlandı, taşma yok | **BAŞARILI** |
| **333 × 333** (Kare) | Önizleme (`?onizleme=1`) | Kart içine tam sığmalı, net ve orantılı görünmeli | Tam uyumlu, fov 42-44°, 0 kesilme | **BAŞARILI** |
| **320 × 200** (Yatay) | Önizleme (`?onizleme=1`) | Yatay kartta dikey/yanal taşma olmamalı | Yükseklik sığması tam, kamera açısı optimize | **BAŞARILI** |
| **390 × 844** (Mobil) | Tam Materyal (`index.html`) | Dikey mobil ekranda tüm butonlar ve 3D tuval erişilebilir olmalı | Duyarlı düzen korundu, araçlar ve paneller tam işlevsel | **BAŞARILI** |
| **1440 × 900** (Masaüstü)| Tam Materyal (`index.html`) | Geniş ekranda iki panelli dikey mimari bozulmamalı | Masaüstü çalışma alanı tam yerleşimli | **BAŞARILI** |

#### 6.5. Kararlılık ve Kapat-Aç Doğrulaması
* **3 Kez Aç-Kapat / Yenileme:** Iframe ve tarayıcı ortamında 3 ardışık kapatıp açma ve sayfa yenileme testinde boş kart, kaymış veya kesilmiş şekil oluşmamıştır.
* **Çalışma Zamanı (Runtime) Hatası:** Konsolda 0 JS / WebGL hatası tespit edilmiştir (TDZ ReferenceError ve eahGroup uyuşmazlığı giderilmiştir).
* **Değişen Dosyalar:** `index.html`, `manifest.json`, `test_host.html`, `URETICI_TEST_NOTU.md`.

**Nihai Karar:** 2 Ekim 2026 Tema ve Önizleme Eki şartları eksiksiz karşılanmış olup materyal paketi teslim edilmeye hazırdır.

