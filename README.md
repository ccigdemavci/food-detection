# food-detection

Yemek Fiyatı ve Garson Performansı Ölçüm Sistemi
Bu proje, bir restoran ortamında kamera görüntülerinden otomatik olarak yemek türlerinin tanınması, garsonların kimliklerinin yüz tanıma ile belirlenmesi, masaların QR kodlarla tespiti ve bu bilgilerin birleştirilerek hem anlık hem de geçmişe dönük analizlerin yapılmasını amaçlamaktadır. Sistem, bilgisayarla görme ve makine öğrenmesi yöntemleri ile gerçekleştirilmiştir.

 Proje Amacı
Geliştirilen sistem ile:

Masalara gelen yemeklerin otomatik olarak tanınması

Hizmeti sağlayan garsonun kimliğinin yüz tanıma ile belirlenmesi

Her masanın kimliklendirilmesi için QR kod kullanımının sağlanması

Her işlem için hesaplanan fiyatın tahmini olarak belirlenmesi

Bu bilgilerin görsel olarak video üzerine işlenmesi

Tüm logların kaydedilmesiyle performans ve analiz yapılabilirliği sağlanması
amaçlanmaktadır.

Kullanılan Teknolojiler
Python 3.9

OpenCV – Görüntü işleme

face_recognition – Garson tanıma (yüz tanıma)

YOLOv8 (Ultralytics) – Yemek tespiti (object detection)

pyzbar – QR kod ile masa tanıma

Matplotlib – Görselleştirme

ZBar – QR kod çözümleyici kütüphane

NumPy, CSV, datetime – Yardımcı işlemler ve kayıt

 Sistem Bileşenleri
1.  Yemek Tanıma
YOLOv8 modeli, dessert, salad, grilled, soup, stews olmak üzere beş yemek kategorisini tanıyacak şekilde özel olarak eğitildi.

Tespit edilen yemeklerin her biri önceden belirlenmiş fiyatlarla eşleştirilerek toplam hesap tahmini yapılmaktadır.

2.  Garson Tanıma
face_recognition kütüphanesi kullanılarak, garsonların yüzlerinden alınan encoding’ler ile videodaki yüzler karşılaştırılır.

Yüz benzerlik toleransı (tolerance) %50 olarak ayarlanmıştır.

3.  Masa Tanıma
Masaların tanınması için her masada QR kodlar kullanılmıştır.

pyzbar modülü ile video içerisinden QR kodlar okunarak masa bilgisi alınmaktadır.

4.  Loglama ve Raporlama
Her tespitte: zaman, garson, masa, yemekler ve toplam ücret bilgileri CSV dosyasına kaydedilir.

Böylece geçmişe dönük performans analizi yapılabilir.

✅ Kullanım

# Ortam kurulum
conda create -n face_env python=3.9
conda activate face_env
pip install -r requirements.txt

# Gerekli ZBar kütüphanesini yükleyin (macOS için)
brew install zbar

# Ana betiği çalıştırın
python main.py
 Sonuç
Bu sistem, görüntü işleme ve derin öğrenme  uygulamalarından biri olarak restoran otomasyonu alanında yenilikçi bir örnek teşkil etmektedir. Proje kapsamında:

YOLO ile nesne tanıma,

yüz tanıma algoritmaları ile kimlik belirleme,

QR kod çözümleme,

ve tüm bu bileşenlerin bir araya getirilmesiyle otomatik hesaplama ve kayıt tutma başarıyla gerçekleştirilmiştir.

