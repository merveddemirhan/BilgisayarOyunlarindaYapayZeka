# Gezgin Satıcı Problemi (TSP) - Ödev 1: En Yakın Komşu

Bu proje, Gezgin Satıcı Problemi (TSP) için temel bir sezgisel çözümü Python kullanarak uygular. `networkx` kütüphanesi ile rastgele 2 boyutlu noktalar (düğümler) oluşturur, "En Yakın Komşu" (Nearest Neighbor) algoritmasını kullanarak bir tur hesaplar ve `matplotlib` ile sonucu görselleştirir.

## Projenin Çalışma Prensibi

Proje 3 ana aşamadan oluşur:

### 1. Grafik Oluşturma
- **Sabitler:** Betik, `NOKTA_SAYISI = 11`, `AREA_SIZE = 100` ve `SEED = 42` sabit değerlerini kullanır. `SEED` değeri, her çalıştırmada aynı rastgele noktaların üretilmesini sağlar.
- **Nokta Üretimi:** `(0, 100)` aralığında 11 adet rastgele $(x, y)$ koordinatı oluşturulur.
- **Grafik Temsili:** `networkx.Graph()` kullanılarak boş bir grafik yaratılır. Oluşturulan her nokta, `pos` (pozisyon) özelliği ile birlikte bu grafiğe bir düğüm (node) olarak eklenir.
- **Kenar Ağırlıkları:** Grafiğe tam bağlı (complete graph) bir yapı kazandırmak için her düğüm çifti arasına bir kenar (edge) eklenir. Kenar ağırlığı (`weight`), iki nokta arasındaki Öklid mesafesidir ve `math.dist()` fonksiyonu ile hesaplanır.

### 2. Sezgisel Çözüm: En Yakın Komşu (Nearest Neighbor)
`nearest_neighbor(G, start=0)` fonksiyonu, TSP için açgözlü (greedy) bir yaklaşım uygular:
1.  **Başlangıç:** Tur, varsayılan olarak `0` numaralı düğümden başlar.
2.  **İterasyon:** Mevcut düğümdeyken, *henüz ziyaret edilmemiş* düğümler arasından en yakın olan (yani en düşük kenar ağırlığına sahip) komşu seçilir.
3.  **Tura Ekleme:** Seçilen bu en yakın komşuya gidilir, bu düğüm "ziyaret edildi" listesine eklenir ve aradaki mesafe toplam uzaklığa dahil edilir.
4.  **Tekrarlama:** Tüm düğümler ziyaret edilene kadar 2. ve 3. adımlar tekrarlanır.
5.  **Turun Tamamlanması:** Tüm düğümler ziyaret edildikten sonra, turu kapatmak için son ziyaret edilen düğümden başlangıç düğümüne (`0`) geri dönülür ve bu mesafe de toplam uzaklığa eklenir.
6.  **Dönüş:** Fonksiyon, hesaplanan tur rotasını (düğüm listesi) ve toplam tur mesafesini döndürür.

### 3. Görselleştirme
- `matplotlib` ve `networkx.draw` fonksiyonları kullanılarak sonuçlar görselleştirilir.
- Tüm düğümler (`node_color='purple'`) ve konumları grafiğe çizilir.
- `nearest_neighbor` fonksiyonundan dönen tur rotası (`initial_path`), `lightblue` (açık mavi) ve kesikli (`dashed`) çizgilerle vurgulanır.
- Grafiğin başlığında (`plt.title`) hesaplanan toplam mesafe `.2f` formatıyla gösterilir.
- Görsel, `SAVE_IMAGE = True` olduğu için `odev1.png` adıyla otomatik olarak kaydedilir ve aynı zamanda ekranda gösterilir.

## Gereksinimler

Projenin çalışması için aşağıdaki Python kütüphaneleri gereklidir:
- `networkx`
- `matplotlib`

(Not: `random` ve `math` Python standart kütüphanesinin parçasıdır.)

## Kurulum

Gerekli kütüphaneleri `pip` kullanarak kurabilirsiniz:
```bash
pip install networkx matplotlib