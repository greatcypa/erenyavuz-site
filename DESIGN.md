# erenyavuz.com — Tasarım sistemi

Bu dosya sitenin görsel kurallarını tek yerde toplar. Siteye yeni bir bölüm eklerken
(kendin ya da bir yapay zekâ aracıyla) önce buraya bak. Değerler `index.html` içindeki
`:root` değişkenleriyle birebir aynıdır.

## Fikir

Beyaz bir sayfa, siyah ve net tipografi, ve sayfada yaşayan turkuaz çizgi canavarlar.
Canavarlar Eren'in Behance kapağındaki karakterlerden sadeleştirildi. Sitenin bütün
kişiliği onlarda. Geri kalan her şey sakin ve disiplinli kalır.

- Cesaret tek yerde: canavarlar. Tipografi, grid ve renk onların önüne geçmez.
- Hareket mesleği anlatır: titreşen çizgi (boil), trim path ile çizilme, squash & stretch,
  imleci izleyen gözler. Hepsi motion tasarımının kendi dilinden.
- Kendiliğinden oynayan hareket az: tek bir açılış anı (canavarların çizilmesi) ve
  kaydırmayla ilerleyen tek bir zaman çizelgesi. Gerisi ziyaretçinin hareketine cevap verir.
- `prefers-reduced-motion` açıksa boil, çizilme, makara ve el sallama durur.

## Renk

| Ad            | Hex       | Görev                                                   |
|---------------|-----------|---------------------------------------------------------|
| Paper         | `#FFFFFF` | Zemin. Krem ya da gri değil, düz beyaz.                 |
| Ink           | `#000000` | Metin, çizgiler, birincil buton.                        |
| Monster       | `#0E9F8E` | Canavar çizgileri, keyframe'ler, playhead, odak halkası. |
| Monster deep  | `#08766A` | Turkuaz metin ve hover (beyaz üstünde okunur kontrast).  |
| Mint          | `#E3F4F0` | Görsel yer tutucular, seçim rengi, zaman çizelgesi barı. |
| Fog           | `#6B7270` | İkincil metin, bölüm etiketleri.                        |
| Rule          | `#D9DDDC` | İnce ayırıcı çizgiler.                                  |

Kural: Sayfada tek renk vurgu var, o da turkuaz. Başlıkta tek bir kelimeyi renklendirmek yok.

## Tipografi

- Metin: **Bricolage Grotesque** (Google Fonts, değişken: `opsz 12–96`, `wght 300–800`).
  Türkçe karakterleri destekler. Yedek: Inter, system-ui.
- İsim: **Happy Doodle** (Eren'in seçtiği font, `assets/fonts/happy-doodle.woff`, sadece Latin harfler).
  Sadece "Eren Yavuz" yazısında kullanılır (girişte ve footer'da). Türkçe ğ, ı, ş, İ harfleri yok,
  bu yüzden başka metinde kullanılmaz. Fare hareketiyle harfler çok hafif (±1.4°, ±2px) ve yumuşak kıpırdar.

| Rol                | Boyut                          | Ağırlık | Harf aralığı | Satır |
|--------------------|--------------------------------|---------|--------------|-------|
| İsim (hero)        | `clamp(84px, 19vw, 330px)`     | 400     | 0            | 0.9   |
| Büyük cümle (CTA)  | `clamp(44px, 7vw, 112px)`      | 600     | -0.035em     | 0.95  |
| Bölüm başlığı (h2) | `clamp(32px, 4.4vw, 60px)`     | 500     | -0.03em      | 1.02  |
| İş başlığı         | `clamp(26px, 3.2vw, 44px)`     | 500     | -0.02em      | 1.1   |
| Lead               | `clamp(21px, 2vw, 26px)`       | 400     | -0.01em      | 1.3   |
| Gövde              | `18px`                         | 400     | 0            | 1.5   |
| Küçük              | `14px`                         | 500     | 0.01em       | 1.4   |

- Büyük harfle etiket yok. Bölüm etiketleri cümle düzeninde, gri ve küçük.
- Satır uzunluğu en fazla ~65 karakter.

## Boşluk ve grid

- 8px tabanı: `8, 16, 24, 32, 48, 64, 96, 144`.
- Kenar boşluğu: `clamp(20px, 4vw, 56px)`. En geniş içerik: 1440px.
- Bölümler arası: 144px (mobilde 96px).
- Masaüstünde bölümler iki kolonlu: solda 3/12 etiket, sağda 9/12 içerik. Her şey sola hizalı.

## Bileşenler

- **Canavar**: `viewBox 0 0 200 200`, çizgi `3.4`, yuvarlak uç ve birleşim, gövde dolgusu beyaz.
  Varyantlar: `classic`, `crown`, `glasses`, `reel`, `antenna`, `wave`, `sleepy`.
  Göz bebekleri imleci en fazla 6 birim izler. Rastgele aralıklarla göz kırpar.
- **Buton**: hap şekli (`border-radius: 999px`), 16×26px iç boşluk.
  Birincil siyah dolgu, ikincil 1.5px siyah kontur. Metin ne olacağını söyler ("E-posta yaz").
- **İş satırı**: başlık solda, tür sağda, üstte 1px ayırıcı. Masaüstünde imleci izleyen önizleme.
- **Zaman çizelgesi**: After Effects kompozisyonu gibi; katman adları solda, barlar ve
  keyframe elmasları sağda, turkuaz playhead kaydırmayla ilerler.
- **Giriş kalabalığı**: Giriş ekranını boşluksuz dolduran, açık turkuaz (`#A9DCD2`), 1.5px çizgili canavarlar.
  Hiçbiri kenardan ya da menünün altından kesilmez; büyükten küçüğe boşlukları doldurarak yerleşir.
  Etkileşimsiz. Üstünde 6 tam görünen, etkileşimli canavar asimetrik dağılır.
- **Canavar parçaları**: gövde (yuvarlak, şişman, zayıf, minik, fasulye), gözler (iki, kocaman, tek göz,
  göz kırpan, mutlu, üç göz, uykulu), ağız (sırıtma, gülümseme, dil, tavşan dişi, ıslık, çiğneme...),
  başlık (diken, anten, kep, bere, silindir, parti şapkası, taç, bandana, kulaklık, çiçek),
  gözlük (siyah, yuvarlak, kalp, yıldız, vizör, inek gözlüğü), elindekiler (pizza, hamburger, direksiyon,
  oyuncak araba, çay bardağı, simit, dondurma, kalem, klaket, patlamış mısır, film makarası),
  ekstralar (bıyık, papyon, allık).
- **Carousel**: Sabit yükseklik, oran işe göre (`4/3`, `16/9`, `3/4`...). 14px köşe, mint zemin,
  boşken içinde canavar. Sürükleme, oklar, klavye, "01 / 08" sayacı. Altındaki liste içindekiler gibi çalışır.
- **Sesler (foley)**: Web Audio ile ağız/gırtlak benzeri filtrelerle üretilir (formant sentezi), dosya yok.
  Her karakterin kendi "sesi" var: taçlı "hey-ya!", gözlüklü "yeah~", makaralı "ba-di-ba-du",
  antenli "uu-ii?", hamburgerli "nom nom", parti şapkalı "yip!", klasik kıkırdama, el sallayan "hii!",
  uykucular esneme, tıklayınca "uf!". Fare karakterin üstüne gelince bir kez çalar, ayrılana kadar susar.
  Tarayıcı kuralı gereği ziyaretçi sayfaya bir kez tıklamadan ses çıkmaz. Menüde ses aç/kapa düğmesi var.

## Yapma

- Krem zemin, gradyan yıkamalar, her şeye aynı gölge.
- Her bölüme ayrı ayrı "aşağıdan kayarak gelme" animasyonu.
- Buton ve link metinlerine `→` eklemek.
- Canavarları başka renge boyamak ya da dolgulu çizmek.
