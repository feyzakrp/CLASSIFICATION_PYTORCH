# Derin Öğrenme ile Görüntü Sınıflandırma Projesi

Bu proje, derin öğrenme yöntemleri kullanılarak bir görüntü sınıflandırma modelinin oluşturulmasını ve test edilmesini amaçlamaktadır. Projede, önceden eğitilmiş bir model (örneğin ResNet18) kullanılarak transfer öğrenme uygulanmış ve başarı oranı arttırılmıştır.

## Projenin Amaçları

- Derin öğrenme teknikleri kullanarak verimli bir görüntü sınıflandırma modeli oluşturmak.
- GPU kullanarak eğitim süresini optimize etmek.
- Veri artırma (data augmentation) ve normalizasyon işlemleriyle model performansını iyileştirmek.
- Eğitim, doğrulama ve test aşamalarında model performansını değerlendirmek ve görsel olarak analiz etmek.

## Proje Aşamaları

### 1. Gerekli Kütüphanelerin Yüklenmesi
Proje, şu ana Python kütüphanelerini kullanmaktadır:
- **PyTorch** ve **torchvision**: Derin öğrenme modelleri ve veri işlemleri için.
- **NumPy**, **Pandas** ve **Matplotlib**: Veri analizi ve görselleştirme.
- **scikit-learn**: Model doğruluğu, hata metrikleri ve raporlamalar için.
- **Pillow** ve **OpenCV**: Görüntüler üzerinde işlem yapmak ve dönüştürüler yapmak için.

### 2. Donanım Kullanımını Doğrulama
Kod, mevcut donanımı tespit ederek GPU veya CPU kullanımını otomatik olarak seçer. GPU mevcutsa, CUDA destekli NVIDIA grafik kartı ile hızlı işlem yapar.

### 3. Veri Yükleme ve Ön İşleme
- **Veri Yükleme**: Görüntüler **ImageFolder** sınıfı kullanılarak yüklenmiştir.
- **Veri Artırma**: Aşağıdaki teknikler kullanılmıştır:
  - Rastgele döndürme.
  - Yeniden boyutlandırma.
  - Yatay çevirme.
  - Rastgele kesme.
- **Normalizasyon**: Renk kanalları (R, G, B) için ortalama ve standart sapma değerleri kullanılarak veri normalize edilmiştir.

### 4. Modelin Kurulumu
- **Model Seçimi**: ResNet18 modeli, transfer öğrenme kullanılarak uygulanmıştır.
- **Çıkış Katmanı**: Son katman, proje veri setindeki sınıf sayısına göre yeniden ayarlanır.
- **Kayıp Fonksiyonu**: CrossEntropyLoss kullanılmıştır.
- **Optimizasyon**: Adam optimizer ile eğitim yapılmıştır.

### 5. Model Eğitimi
- Model 10 epoch boyunca eğitilmiş ve her epoch sonunda aşağıdaki metrikler hesaplanmıştır:
  - **Loss Değeri**: Modelin yanılma oranını gösterir.
  - **Validation Accuracy**: Doğrulama setindeki başarı oranı.

### 6. Model Testi ve Performans Analizi
- **Test Accuracy**: Test veri setindeki başarı oranı hesaplanmıştır.
- **Görselleştirme**: Eğitim kaybı, doğrulama doğruluğu ve test tahminleri görselleştirilmiştir.
- **Yanılış Tahminler**: Modelin doğru ve yanlış tahminleri renklendirilerek gösterilmiştir.

### 7. Elde Edilen Sonuçlar
- **Test Accuracy**: Model, test setinde %86.8 başarı oranı elde etmiştir.
- **Eğitim ve Doğrulama Sonuçları**: Eğitim kaybı azalmış ve doğrulama doğruluğu artmıştır.

## Dosya Yapısı
- **dataset/**: Görüntülerin bulunduğu ana klasör.
  - **train/**: Eğitim veri seti.
  - **test/**: Test veri seti.
- **model.py**: Modelin eğitim ve test süreçlerini içeren Python dosyası.
- **README.md**: Proje hakkında detaylı bilgi.

## Nasıl Çalıştırılır?

1. **Gereksinimleri Yükleyin:**
   ```bash
   pip install torch torchvision scikit-learn matplotlib opencv-python pillow
   ```
2. **Veri Setini Yükleyin:**
   `dataset` klasörünü proje dizinine yerleştirin.
3. **Modeli Çalıştırın:**
   ```bash
   python model.py
   ```
4. **Sonuçları Görüntüleyin:** Eğitim kaybı, doğrulama doğruluğu ve test tahminleri görselleştirilecektir.

## Kullanılan Teknolojiler
- **PyTorch**: Derin öğrenme modeli oluşturmak ve eğitmek için.
- **ResNet18**: Transfer öğrenme ile daha hızlı ve doğru model oluşturmak için.
- **Matplotlib**: Görselleştirme.
- **scikit-learn**: Performans değerlendirmesi.


