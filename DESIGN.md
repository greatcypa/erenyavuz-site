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
  Varyantlar: `classic`, `crown`, `glasses`, `antenna`, `party`, `wave`, `sleepy` ve hareketliler:
  `burger`, `pizza`, `trumpet`, `guitar`, `camcorder`.
  Göz bebekleri imleci en fazla 6 birim izler. Rastgele aralıklarla göz kırpar.
- **Buton**: hap şekli (`border-radius: 999px`), 16×26px iç boşluk.
  Birincil siyah dolgu, ikincil 1.5px siyah kontur. Metin ne olacağını söyler ("E-posta yaz").
- **İş satırı**: başlık solda, tür sağda, üstte 1px ayırıcı. Masaüstünde imleci izleyen önizleme.
- **Zaman çizelgesi**: After Effects kompozisyonu gibi; katman adları solda (Oyun, Video ve Motion,
  Basılı ve dijital, Art direction, AI), barlar ve keyframe elmasları sağda. Cetvel 2011-2027 (1 yıl = 1/16).
  Beş keyframe: 2011, 2013, 2017, 2021, 2026. Kaydırma beş eşit parçaya bölünür; turkuaz playhead her
  keyframe'de biraz bekler, o yılın cümlesi altta yılıyla birlikte görünür, sonra bir sonrakine kayar.
- **Giriş kalabalığı**: Giriş ekranını boşluksuz dolduran, açık turkuaz (`#A9DCD2`), 1.5px çizgili canavarlar.
  Hiçbiri kenardan ya da menünün altından kesilmez; büyükten küçüğe boşlukları doldurarak yerleşir.
  Etkileşimsiz. Üstünde 8 (mobilde 6) tam görünen, etkileşimli canavar asimetrik dağılır.
- **Profil fotoğrafı**: Girişte sol tarafta, karakterlerin kafasıyla aynı boyda yuvarlak fotoğraf (`assets/eren.jpg`,
  480×480). Çevresinde karakterlerle aynı turkuaz, elle çizilmiş ve titreşen halka; kamera tutan karakter hemen altında.
- **Hareketli karakterler (GIF gibi)**: 2-5 karelik, adım adım değişen döngüler; ara geçiş yok.
  Hamburger yiyen ve pizza yiyen (ağız açar, ısırır, çiğner, kırıntı döker; 5 kare, 1.1 sn),
  trompetçi (gözler kapalı, yanaklar şişik, notalar yükselir; 3 kare, 0.75 sn),
  gitarist (sağ el tellere vurur; 4 kare, 0.56 sn), eski tip el kamerasıyla çeken
  (objektif imleci izler, REC ışığı yanıp söner; 2 kare, 1 sn).
  Yalnızca ekrandayken oynar; "hareketi azalt" ayarında ilk karede durur. Arka plandakiler hep ilk karede.
- **Canavar parçaları**: gövde (yuvarlak, şişman, zayıf, minik, fasulye), gözler (iki, kocaman, tek göz,
  göz kırpan, mutlu, üç göz, uykulu), ağız (sırıtma, gülümseme, dil, tavşan dişi, ıslık, çiğneme...),
  başlık (diken, anten, kep, bere, silindir, parti şapkası, taç, bandana, kulaklık, çiçek),
  gözlük (siyah, yuvarlak, kalp, yıldız, vizör, inek gözlüğü), elindekiler (pizza, hamburger, direksiyon,
  oyuncak araba, çay bardağı, simit, dondurma, kalem, klaket, patlamış mısır),
  ekstralar (bıyık, papyon, allık).
- **Carousel + galeri**: Her kutucuk bir iş; altında yalnızca kategorisi yazar (Product, Key Visual, Kampanya,
  Ambalaj, Motion, Sosyal Medya, Print, Etkinlik). Kapak görseli kendi oranında, 14px köşe. Sürükleme, oklar, klavye,
  "01 / 08" sayacı. Kutucuğa tıklayınca sayfa değişmeden altta o işin galerisi açılır (masaüstünde 2 kolon,
  mobilde 1). Görseller `assets/work/<klasör>/1.jpg, 2.jpg, 3.jpg...` düzeninden otomatik okunur; 1 kapaktır.
- **Sesler**: Dosya yok, hepsi Web Audio ile tarayıcıda üretilir. Çoğu karakter minik, tiz, sevimli bir
  "Hi!" der (minyon tarzı, formant sentezi; ses inceliği karaktere göre değişir). Kameralı aynı sesle "Action!" der,
  gitarist muzip bir akor çalar (Karplus-Strong tel sentezi), hamburgerci ve pizzacı ısırıp çıtır çıtır çiğner,
  trompetçi kısa bir "ta-ra-taa!" çalar. Fare karakterin üstüne gelince bir kez çalar, ayrılana kadar susar.
  Tıklayınca da çalar; footer'daki uykucular uyanınca daha kalın bir "Hi".
  Tarayıcı kuralı gereği ziyaretçi sayfaya bir kez tıklamadan ses çıkmaz. Menüde ses aç/kapa düğmesi var.

## Yapma

- Krem zemin, gradyan yıkamalar, her şeye aynı gölge.
- Her bölüme ayrı ayrı "aşağıdan kayarak gelme" animasyonu.
- Buton ve link metinlerine `→` eklemek.
- Canavarları başka renge boyamak ya da dolgulu çizmek.

## SEO

- Başlık, açıklama ve anahtar kelimelerde kategoriler geçer: product, key visual, kampanya, ambalaj, motion,
  sosyal medya, print, etkinlik (EN: campaign, packaging, social media, event).
- `schema.org` JSON-LD: Person (knowsAbout + makesOffer ile kategoriler), WebSite ve 8 işin listesi.
- Open Graph / Twitter paylaşım görseli: `assets/og.jpg` (1200×630, giriş ekranından).
- `robots.txt` ve görsel kapakları da içeren `sitemap.xml`. Görsellerin alt metni: "<Kategori> – Eren Yavuz".

## Ekran boyutları

- Masaüstü ve yatay tablet: karakterler ve fotoğraf bir "sahne" içinde; sahne metin sütunuyla aynı genişlikte
  (en fazla 1440px) ortalanır, konum ve boyutlar sahnenin yüzdesidir. Büyük ekranlarda da isimle hizalı kalır.
- Telefon ve dik tablet: sahne ismin ve unvanın altına iner, kalan ekranı doldurur (telefonda 7, tablette 7 öğe,
  farklı yerleşim). Hiçbir karakter yazının üstüne binmez.
- Yatay telefon gibi alçak ekranlarda zaman çizelgesi sıkışık düzene geçer ve tek ekrana sığar.
- Galeri 600px üstünde iki sütun, altında tek sütun. Süreç adımları 600-1100px arası iki sütun.
