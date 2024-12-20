# LLM Tabanlı Model Eğitim ve Karşılaştırma Çalışması

Bu proje, çeşitli büyük dil modellerini (LLM) kullanarak Türkçe ve İngilizce veri setleri üzerinde model eğitimi, değerlendirme ve karşılaştırma yapmayı amaçlamaktadır. Kullanılan modeller, modern doğal dil işleme (NLP) teknikleriyle **soru-cevaplama** görevlerinde test edilmiştir. Amaç, modellerin farklı metrikler üzerindeki başarılarını analiz ederek en etkili modeli belirlemektir.

---

## Kullanılan Modeller

Projede yer alan modeller şunlardır:
- **BERT (Turkish-English)**: Hem Türkçe hem de İngilizce metinlerde etkili sonuçlar veren, çift dilli bir dil modeli.
- **RoBERTa (English)**: İngilizce dilinde geliştirilmiş güçlü bir model. Transformer mimarisinin optimize edilmiş bir versiyonudur.
- **T5 (English)**: İngilizce dilinde özelleştirilmiş bir generatif model. Metin özetleme ve soru-cevaplama gibi görevlerde kullanılmıştır.
- **DistilBERT (Turkish)**: Daha hafif ve hızlı bir Türkçe dil modeli. BERT'in sıkıştırılmış bir versiyonudur.
- **ELECTRA (Türkçe)**: Türkçe dilinde yüksek doğruluk oranı sağlayan bir model. Soru-cevaplama görevleri için optimize edilmiştir.

---

## Projenin Amacı

Projenin temel amacı, farklı dil modellerinin **soru-cevaplama** görevlerindeki performansını karşılaştırmaktır. Modellerin başarı düzeyleri, aşağıdaki metrikler üzerinden değerlendirilmiştir:
- **ROUGE (Recall-Oriented Understudy for Gisting Evaluation)**: Metin özetleme ve içerik benzerliği ölçümünde kullanılan bir metrik.
- **BLEU (Bilingual Evaluation Understudy)**: Çeviri ve metin oluşturma süreçlerinde kullanılan bir metrik.
- **F1 Skoru**: Modelin hassasiyet (precision) ve geri çağırma (recall) başarısını ölçer.
- **Exact Match (EM)**: Modelin verdiği cevabın tamamen doğru olma oranını ölçer.
- **Cosine Similarity**: Modelin semantik benzerliğini ölçen bir metrik.

---

## Proje İçeriği

### Kullanılan Veri Setleri

Eğitim ve değerlendirme süreçlerinde kullanılan veri setleri:
- **Eğitim Veri Seti**: 14.221 örnek içerir. Modelin eğitimi için kullanılmıştır.
- **Doğrulama Veri Seti**: 1.330 örnek içerir. Modelin değerlendirme metrikleri üzerinde test edilmesini sağlar.

Veri setleri JSON formatında düzenlenmiş olup `dataset/` dizininde bulunmaktadır. Her bir örnek şu alanları içerir:
- **context**: Soruların bağlamını oluşturan metin.
- **question**: Cevaplanması gereken soru.
- **answer**: Sorunun doğru cevabı.

---

### Modellerin Eğitimi

Projede modellerin eğitimi için şu adımlar takip edilmiştir:
1. **Veri Seti Hazırlama**: Ham veri, belirli bir formatta düzenlenmiş ve Hugging Face Dataset formatına dönüştürülmüştür.
2. **Model ve Tokenizer Seçimi**: NLP görevine uygun dil modeli ve ilgili tokenizer seçilmiştir.
3. **Tokenizasyon**: Veri token'lara (kelime parçacıklarına) ayrılarak modelin anlayabileceği hale getirilmiştir.
4. **Cevap Pozisyonlarının Belirlenmesi**: Sorulara ait doğru cevapların başlangıç ve bitiş pozisyonları belirlenmiştir.
5. **Eğitim Parametrelerinin Belirlenmesi**: Optimizasyon algoritması, öğrenme oranı ve epoch sayısı gibi parametreler ayarlanmıştır.
6. **Model Eğitimi**: Modeller, belirlenen parametrelerle eğitilmiştir.
7. **Sonuçların Değerlendirilmesi**: Eğitim ve doğrulama sonuçları detaylı bir şekilde analiz edilmiştir.

---

### Performans Karşılaştırması

Farklı modellerin sonuçları şu metriklerle değerlendirilmiştir:
- **ROUGE**: Metin özetleme performansını ölçmek için kullanılmıştır.
- **BLEU**: Modelin oluşturduğu metinlerin kalitesini analiz etmiştir.
- **F1 Skoru**: Modelin hassasiyet ve doğruluk başarısını ölçmek için kullanılmıştır.
- **Exact Match (EM)**: Cevapların doğru olup olmadığını doğrudan kontrol etmiştir.
- **Cosine Similarity**: Cevapların semantik olarak ne kadar benzer olduğunu ölçmüştür.

---

## Kurulum ve Çalıştırma

Projeyi çalıştırmak için aşağıdaki adımları izleyin.

### Gereksinimler
Proje, Python 3.8+ sürümü ile çalışır. Gerekli Python kütüphaneleri şunlardır:
- **Transformers**: Dil modellerini yüklemek ve eğitmek için.
- **Datasets**: Veri işleme ve düzenleme için.
- **Torch**: PyTorch tabanlı model eğitimi için.
- **Evaluate**: Modellerin performansını ölçmek için.

### Kurulum Adımları
1. **Gerekli Kütüphaneleri Yükleme**
   Aşağıdaki komutu kullanarak gerekli kütüphaneleri yükleyin:
   ```bash
   pip install transformers datasets torch evaluate
