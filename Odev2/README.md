# 🚗 TSP (Gezgin Satıcı Problemi) - Antalya Yol Ağı Üzerinde 2-Opt İyileştirmesi

Bu proje, **OSM verilerini (OpenStreetMap)** kullanarak **Muratpaşa, Antalya** bölgesinde rastgele seçilen noktalar arasında **Gezgin Satıcı Problemi (TSP)** çözümü gerçekleştirir.  
Çözümde **Nearest Neighbor (En Yakın Komşu)** sezgisel yöntemi ve ardından **2-Opt** algoritması ile rota iyileştirmesi uygulanır.  
Sonuç, **Folium** kütüphanesi kullanılarak interaktif bir **harita üzerinde görselleştirilir**.

---

## 📚 İçindekiler
- [Amaç](#-amaç)
- [Kullanılan Kütüphaneler](#-kullanılan-kütüphaneler)
- [Algoritmalar](#-algoritmalar)
  - [Nearest Neighbor (En Yakın Komşu)](#nearest-neighbor-en-yakın-komşu)
  - [2-Opt İyileştirmesi](#2-opt-iyileştirmesi)
- [Kurulum](#-kurulum)
- [Çalıştırma](#-çalıştırma)
- [Çıktılar](#-çıktılar)
- [Notlar](#-notlar)

---

## 🎯 Amaç
Bu projenin amacı:
- Gerçek bir şehir yol ağı üzerinde TSP problemi çözmek,  
- Rota optimizasyonu için 2-Opt gibi bir yerel arama algoritmasını uygulamak,  
- Sonuçları interaktif bir haritada görselleştirmektir.

---

## 🧩 Kullanılan Kütüphaneler
Aşağıdaki Python kütüphaneleri kullanılmaktadır:

| Kütüphane | Açıklama |
|------------|-----------|
| `osmnx` | OpenStreetMap verilerini indirip grafik (ağ) yapısına dönüştürür. |
| `networkx` | Yol ağı üzerinde grafik hesaplamaları yapar (kısa yol, mesafe, vb.). |
| `folium` | Sonuçları etkileşimli haritada görselleştirir. |
| `random` ve `math` | Rastgele nokta seçimi ve matematiksel işlemler için. |

Kütüphaneleri yüklemek için:
```bash
pip install osmnx networkx folium
```

---

## 🧠 Algoritmalar

### 🟩 Nearest Neighbor (En Yakın Komşu)
- Başlangıç noktasından en yakın komşu düğüme giderek rota oluşturur.  
- Hızlı ancak her zaman en iyi çözümü bulmaz.  
- Bu yöntem başlangıç çözümünü üretir.

### 🟦 2-Opt İyileştirmesi
- Nearest Neighbor sonucu üzerinden rota çiftlerini değiştirerek mesafeyi azaltır.  
- Her değişim sonrasında rota yeniden değerlendirilir.  
- Yerel minimumda durur.

---

## ⚙️ Kurulum

1. Python 3.8+ kurulu olduğundan emin olun.
2. Gerekli kütüphaneleri yükleyin:
   ```bash
   pip install osmnx networkx folium
   ```
3. Script dosyasını (`odev2.py`) indirin.
4. Aynı dizinde bir çalışma ortamı oluşturun.

---

## ▶️ Çalıştırma

Terminal veya VSCode üzerinden:
```bash
python odev2.py
```

Kod çalıştırıldığında:
- **Muratpaşa, Antalya** yol ağı indirilir.  
- 11 rastgele nokta seçilir.  
- **Nearest Neighbor** yöntemiyle rota oluşturulur.  
- **2-Opt** algoritması ile rota iyileştirilir.  
- Sonuçlar `odev2.html` dosyası olarak kaydedilir.

---

## 📍 Çıktılar

**Konsol Çıktısı Örneği:**
```
4. Adım: TSP çözülüyor (Nearest Neighbor Heuristic uygulanıyor)...
  Nearest Neighbor Sonucu: 12.45 km
  Nearest Neighbor Rotası: [0, 3, 7, 5, 10, 1, 8, 6, 2, 9, 4, 0]
  2-Opt 7 iterasyonda tamamlandı.
  2-Opt Sonrası Sonuç: 10.87 km
  2-Opt Rotası : [0, 7, 5, 10, 8, 1, 9, 6, 2, 4, 3, 0]
```

**Üretilen Harita:**
- `odev2.html` adlı dosya çalışma klasörüne kaydedilir.  
- Harita, her bir noktanın etiketini (`Nokta 0`, `Nokta 1`, …) ve rotayı mavi çizgilerle gösterir.  
- Başlangıç noktası yeşil, diğer noktalar kırmızı ikonlarla gösterilir.

---

## 🧾 Notlar
- Eğer bazı noktalar arasında yol bağlantısı yoksa (`inf` mesafe), 2-Opt algoritması çalıştırılmaz.
- Rastgele seçilen noktalar nedeniyle her çalıştırmada farklı rotalar oluşabilir.
- Daha doğru sonuçlar için **NOKTA_SAYISI** artırılabilir, ancak hesaplama süresi de artar.
- Harita verileri OSM’den indirildiği için **internet bağlantısı** gereklidir.

---

## 📁 Dosya Yapısı
```
├── odev2.py
├── odev2.html        
└── README.md         
```

---


