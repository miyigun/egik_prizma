# Materyal Seti: Tema ve Önizleme Eki

2 Ekim 2026 | Materyal sahipleri ve düzeltme yapan YZ için kısa teslim eki

**Toplantıda aktarılacak karar:** Her materyal sahibi, kendi bağımsız materyalini aşağıdaki tema ve önizleme koşullarını sağlayacak şekilde düzeltip çalışır paket olarak teslim eder. Siteye ekleme ve yayına alma, materyal sahibinin görevi değildir.

Bu belge mevcut üretim-denetim kural setinin yerine geçmez; materyalin tesliminde aranacak tema ve önizleme koşullarını netleştirir.

## 1. Tema: Sitede tek seçim, bağımsız kullanımda kendi düğmesi

- Kayıtlı kullanıcı tercihi yoksa **açık tema** ile başla. Gece teması kullanıcı seçimiyle açılır.
- Site içinde materyal, sitenin açık/koyu seçimini izlesin. Bağlantı doğrulandıktan sonra materyalin ikinci tema düğmesi gizlensin. Bağımsız açılışta veya bağlantı yoksa kendi düğmesi çalışmaya devam etsin.
- Tema değişince parametreler, çizim konumu, cevaplar ve ilerleme sıfırlanmasın. Bu davranış önizlemede de çalışsın.
- Zemin, panel, metin ve kontrol renkleri değiştirilebilir ortak renk değişkenlerine bağlansın. **Kesin renk kodları henüz zorunlu değil; önceki deneme paleti topluca uygulanmayacak.** Nesne renkleri çeşitli olabilir; her iki temada okunaklılık ve nesnelerin anlamı korunsun. Sayfaya topluca renk ters çevirme filtresi uygulanmasın.
- **Fon tutarlılığı:** `--ms-bg` ana fonu, `--ms-surface` panel/çizim zeminini, `--ms-surface-alt` ikincil alanları, `--ms-text` yazıyı yönetsin. Her değişkenin açık ve koyu tema karşılığı tanımlansın; açık temada açık nötr, koyu temada koyu nötr yüzeyler kullanılsın. Tam çalışma ve önizleme aynı paleti kullansın; koyu temada yanlışlıkla açık kalan panel veya çizim fonu olmasın. SVG/Canvas/WebGL zemini de bu seçime bağlansın; matematiksel anlam taşıyan renkli alanlar ve nesne renkleri fonla karıştırılmasın. Site şimdilik yalnız açık/koyu seçimini gönderir; renk kodlarını otomatik aktardığı varsayılmasın.

**YZ için bağlantı bilgisi:** Mevcut aynı-origin yerleştirmede materyal, dinleyicisini kurunca üst sayfaya `{"channel":"matbis-theme","type":"ready"}` gönderir. Üst sayfadan gelen `{"channel":"matbis-theme","type":"set-theme","theme":"light"}` veya `"dark"` mesajı mevcut tema fonksiyonuna bağlanır. Gönderen pencere `window.parent`, origin ise beklenen site origin'i olmalıdır; kanal, işlem ve değer doğrulanır. Hedef origin açıkça belirtilir, `*` kullanılmaz. Site tercihi bağımsız kullanım tercihinin üzerine kaydedilmez. Farklı alan adı kullanımı teknik ekiple ayrıca doğrulanır; güvenlik kontrolü kaldırılmaz.

## 2. Önizleme: Sade, doğru ve alana uyumlu

- Tam materyal: `index.html`. Sade önizleme: **`index.html?onizleme=1`**. Parametre adı `önizleme` değil, `onizleme` olmalıdır. Adreste başka parametre varsa `&onizleme=1` eklenir.
- Önizleme aynı materyalin hesap/çizim mantığından üretilsin; bütün uygulama küçültülüp karta sıkıştırılmasın. Tek matematiksel fikir gösterilsin; uzun yönerge, araç panelleri ve cevaplar önizlemede açılmasın. Tam çalışmada gerekli yönerge erişilebilir kalsın.
- **Görünüm referansı:** Cisim Köşegenli Küp ve dört parçalı Üçgen Prizma örneklerindeki gibi, nesnenin/parçaların öne çıktığı sade ve ortalanmış bir sahne sunulsun. Bunların matematiksel içeriği kopyalanmaz; her materyalin kendi ilişkisi bu sadelikte gösterilir.
- **Önizleme fonu:** Saman sarısı, bej veya materyale göre değişen dekoratif alt zemin kullanılmasın. `--ms-preview-bg` ile tema başına tek, düz ve ortak fon tanımlansın: açık temada açık nötr, koyu temada koyu nötr. Fon; sürgü, animasyon veya sahne adımıyla renk değiştirmesin; yalnız tema değişiminde karşılığına geçsin. Doku ve gradient eklenmesin. Bu kural nesne/parça renklerini tekleştirmez; mevcut örneklerin fon renklerinin aynen kopyalanması istenmez.
- **1:1 ve responsive birbirinin alternatifi değildir.** 1:1 görsel alanının kare olmasıdır; responsive, görünümün içine yerleştiği alana uyum sağlamasıdır. Kare ve yatay alanlarda şekiller oranları bozulmadan sığsın ve ortalansın; etiketler kesilmesin, kontroller taşmasın. Dış kartın tamamının kare olması gerekmez.
- Asgari deneme alanları: **240×240 ve 333×333 kare; 320×200 yatay**. Tam materyal ayrıca **390×844 telefon ve 1440×900 masaüstü** görünümünde denensin. Bunlar test ölçüleridir; sabit piksel boyutu dayatması değildir.
- Animasyon veya SVG zorunlu değildir. Materyalin ürettiği sabit temsil ya da anlamlı sınırlı etkileşim yeterlidir. Hareket varsa durdurulabilsin; görünmezken/arka plandayken ve hareket azaltma tercihinde otomatik çalışmasın. Önizleme öğrenci cevaplarını veya ilerlemesini değiştirmesin.
- Kart kapağı ayrı, hafif bir görsel olabilir; **kapak, çalışan `?onizleme=1` kipinin yerine geçmez.** Kapağın veya animasyonun gösterdiği ilişki tam materyalde gerçekten bulunmalıdır.
- Teslim edilen tam çalışma adresi doğru materyali eksiksiz açsın. Materyalin kendi içinde “Çalışmayı aç” bağlantısı varsa bu adrese gitsin. Önizlemedeki anlık durum aktarılmıyorsa tanımlı başlangıç durumu kullanılsın; kaldığı yerden devam ettiği izlenimi verilmesin.

## 3. Teslimden Önce Düzeltilecek Kritik Hatalar

Yerel denemelerde görülen sorun türleri aşağıdadır; **her materyalde hepsinin bulunduğu iddia edilmez.** Her üretici kendi materyalinde kontrol etmelidir.

| Hata | Kabul için beklenen |
|---|---|
| Kapat-aç sonrasında boş kart, kaymış veya kesilmiş şekil | Her açılışta görünür, orantılı ve ortalanmış temsil |
| Önizlemede yarım yönerge veya tüm uygulamanın sıkıştırılması | Yalnız sade matematiksel temsil; tam çalışmada eksiksiz yönerge |
| Site ve materyalde çelişen tema; ancak düğmeye tekrar basınca düzelme | İlk açılışta ve tema değişiminde doğru görünüm, tek etkin tema yönetimi |
| Önizlemeyle ilgisiz/boş çalışma açılması veya çalışmayan kontrol | Doğru materyal, çalışan etkileşim ve matematiksel karşılık |
| Materyalin kendi açılışında bozuk ara resim veya belirgin takılma | Gereksiz yük olmadan açılış; yükleme bekleniyorsa sabit alanda “Çalışma yükleniyor…” ve hata halinde yeniden deneme |

**Teslim kapsamı:** Materyal sahibi yalnız kendi paketinin tema alıcısını, sade önizlemesini, yerleşimini ve etkileşimlerini düzeltip kontrol eder. Ana sitenin kartları, bağlantı yönetimi, yükleme sistemi ve yayın işlemleri bu teslim görevinin dışındadır.

## 4. YZ'ye Verilecek Düzeltme Talimatı

> Mevcut kural seti ve bu eki kullanarak yalnız verdiğim bağımsız materyali düzelt. Önce mevcut kodu ve bildirdiğim hataları incele. Matematiksel hesapları, pedagojik akışı ve çalışan özellikleri koru; yeniden yazma veya gereksiz animasyon ekleme. Tema bağlantısını mevcut tema yapısına uyarla; önizlemeyi aynı hesap/çizim mantığıyla sadeleştir ve belirtilen alanlara sığdır. Normal/önizleme açılışını, açık/koyu temayı, dar/geniş alanı ve üç kez aç-kapatmayı tarayıcıda dene. Tema mesajı alımını ve küçük alana yerleşmeyi yerel bir test sayfasında iframe içinde kontrol et; ana siteye erişim gerekmez. Değişen dosyaları, gerçekten yapılan testleri ve kalan sorunları kısaca bildir; test etmediğine “denetlenmedi” yaz. Sonuç olarak koşullara uygun, bağımsız çalışır materyal paketini teslim et.

**Teslim:** Güncel `index.html`, `manifest.json` ve gerekli yerel varlıkları içeren materyal paketi; yanında kısa değişiklik/test notu. Notta paket içindeki tam çalışma ve önizleme girişleri yer alsın; yayımlanmış bir web adresi gerekmez. Raporlar uygulamanın kullanıcıya sunulan ekranlarına eklenmesin. YZ'nin “düzeltildi” demesi tek başına yeterli değildir; materyal sahibi çalışır çıktıyı kontrol ederek teslim eder.
