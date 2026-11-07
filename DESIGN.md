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

- Aile: **Bricolage Grotesque** (Google Fonts, değişken: `opsz 12–96`, `wght 200–800`).
  Türkçe karakterleri destekler. Yedek: Inter, system-ui.
- Tek aile kullanılır. Kişilik ağırlık, boyut ve sıkı harf aralığıyla kurulur.

| Rol                | Boyut                          | Ağırlık | Harf aralığı | Satır |
|--------------------|--------------------------------|---------|--------------|-------|
| İsim (hero)        | `clamp(64px, 15.2vw, 250px)`   | 600     | -0.045em     | 0.86  |
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
- **3D ikon**: hizmetler bölümünde, 112px. Kaynak 3dicons (CC0), `assets/3d/` klasörüne PNG.
  Dosya yoksa turkuaz kil görünümlü yer tutucu çizilir.
- **Zaman çizelgesi**: After Effects kompozisyonu gibi; katman adları solda, barlar ve
  keyframe elmasları sağda, turkuaz playhead kaydırmayla ilerler.

## Yapma

- Krem zemin, gradyan yıkamalar, her şeye aynı gölge.
- Her bölüme ayrı ayrı "aşağıdan kayarak gelme" animasyonu.
- Buton ve link metinlerine `→` eklemek.
- Canavarları başka renge boyamak ya da dolgulu çizmek.
