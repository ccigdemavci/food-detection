# 🍽️ Yemek Tanıma ve Garson Performansı Takip Sistemi

Bu proje, bir restoran ortamında gerçekleşen servis sürecini bilgisayarla görme teknikleri kullanarak analiz eden bir sistemdir. Amaç; yemeklerin tespit edilmesi, bu yemeklerin hangi masaya servis edildiğinin belirlenmesi, servisi gerçekleştiren garsonun kim olduğunun tanınması ve tüm bu bilgilerin otomatik olarak kaydedilmesidir. Sistem aynı zamanda her garsonun performansını da analiz etme potansiyeline sahiptir.

## 🎯 Projenin Amacı

- Restoran içi görüntülerden masa, yemek ve garsonu tespit ederek kayıt altına almak.
- Servis edilen yemeklerin türüne göre otomatik hesaplama yapmak.
- Garsonların görev yaptığı masaları ve servis ettiği yemekleri analiz ederek performans ölçümü yapılmasını sağlamak.
- Geliştirilen sistemin gerçek zamanlı çalışabilmesini ve ileride genişletilebilmesini sağlamak.

## ⚙️ Kullanılan Teknolojiler

- Python 3.9
- OpenCV
- face_recognition
- Ultralytics YOLOv8
- pyzbar (QR kod tanıma)
- Matplotlib (görselleştirme)
- CSV (kayıt işlemleri)
- Jupyter Notebook


## 🧠 Sistem Bileşenleri

### 1. **Yüz Tanıma (Garson Tespiti)**
Garsonların yüz fotoğrafları üzerinden `face_recognition` kütüphanesi ile encoding alınır. Video içerisinden alınan karedeki yüz ile kıyaslanarak hangi garson olduğu belirlenir.

### 2. **QR Kod Okuma (Masa Tespiti)**
Masaların üzerine yerleştirilen QR kodlar video görüntüsünde tespit edilerek her an hangi masanın ön planda olduğu belirlenir.

### 3. **Yemek Tanıma (YOLO)**
Eğitilmiş YOLOv8 modeli kullanılarak görüntüdeki yemekler sınıflandırılır:
- `soup`, `grilled`, `salad`, `stews`, `dessert` gibi sınıflar.

### 4. **Fiyat Hesaplama**
Her yemek türünün sabit bir fiyatı olup toplam hesap otomatik olarak belirlenir.

### 5. **Kayıt ve Raporlama**
Tespit edilen bilgiler (garson, masa, yemek, zaman) `loglar.csv` dosyasına yazılır. İleride performans raporu için kullanılabilir.

## 🚀 Kurulum

1. Ortam oluştur:
   ```bash
   conda create -n restoran_env python=3.9
   conda activate restoran_env
   ```

2. Gerekli kütüphaneleri yükle:
   ```bash
   pip install opencv-python face_recognition matplotlib pyzbar ultralytics
   ```

3. macOS kullanıcıları için `libzbar` yüklenmeli:
   ```bash
   brew install zbar
   ```

## 📊 Çıktılar

- Her 2 saniyede bir video karesi analiz edilir.
- Tespit edilen bilgiler:
  - Masa numarası
  - Garson adı
  - Yemek listesi
  - Toplam hesap
- Bu bilgiler hem videoya görsel olarak işlenir hem de `.csv` olarak kayıt altına alınır.

## 📝 Sonuç

Bu proje, bilgisayarla görme tekniklerini kullanarak restoran ortamında otomatik hizmet izleme ve kayıt sistemi oluşturmayı başarmıştır. Yüz tanıma ile garson tespiti, QR kod ile masa takibi ve nesne tespiti ile yemek sınıflandırma gibi birden fazla teknolojiyi bir arada kullanarak işlevsel ve genişletilebilir bir sistem ortaya konmuştur.

Gerçek zamanlı çalışabilen bu sistem, ileride;
- Garsonların servis sürelerinin analiz edilmesi,
- Müşteri memnuniyeti takibi için entegrasyon,
- Gerçek veritabanı bağlantısı ile POS sistemleriyle bütünleşme,
- Performans raporlarının otomatik oluşturulması gibi gelişmiş özelliklerle genişletilebilir.

Ayrıca sistemin modüler yapısı sayesinde, diğer hizmet sektörlerine de kolaylıkla uyarlanması mümkündür. Bu yönüyle proje, akademik olarak bilgisayarla görme alanına önemli bir uygulamalı katkı sunmaktadır.
