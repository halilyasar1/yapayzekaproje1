#  Yapay Zeka Sistemleri - Genetik Algoritma Projesi



## 📌 Proje Özeti
**Senaryo 6: Kargo Kutusu Tasarımı**

Bir e-ticaret firması için kargo kutularının hacim (kazanç) ve malzeme maliyeti (kayıp) arasındaki dengeyi kurarak, en verimli kutu ölçülerini (**x1: Genişlik**, **x2: Yükseklik**) bulmak hedeflenmiştir. Problem, belirli kısıtlar altında (Constraints) bir **Maksimizasyon** problemidir.

---

## 📐 Matematiksel Model ve Kısıtlar

Projede kullanılan amaç fonksiyonu ve fiziksel kısıtlar aşağıdadır:

### 1. Amaç Fonksiyonu (Fitness Function)
Kutunun verimliliği şu formülle hesaplanmaktadır:
$$y = (x_1 \cdot x_2) - 0.1 \cdot x_1^2 - 0.1 \cdot x_2^2$$

### 2. Kısıtlar (Constraints)
Algoritmanın uyması zorunlu olan kurallar:
* **Raf Sınırı:** $x_1 \cdot x_2 \le 600$ (Kutunun taban alanı 600 cm²'yi geçemez).
* **Genişlik Sınırı:** $x_1 \ge 15$ (Genişlik en az 15 cm olmalı).
* **Değişken Aralıkları:**
    * $x_1 \in [15, 40]$
    * $x_2 \in [5, 20]$

---

## ⚙️ Kullanılan Algoritma ve Yöntemler

Bu çözümde hazır bir kütüphane (PyGAD vb.) **kullanılmamış**, Genetik Algoritma mantığı Python ile **sıfırdan (from scratch)** kodlanmıştır.

### Teknik Detaylar:
* **Kodlama Dili:** Python
* **Kütüphaneler:** NumPy, Matplotlib, Random
* **Seçim Yöntemi (Selection):** *Kesme Seçimi (Truncation Selection)* kullanılarak popülasyonun en iyi %50'si ebeveyn olarak seçilmiştir.
* **Çaprazlama (Crossover):** Ebeveynlerin genleri (genişlik ve yükseklik) karıştırılarak yeni bireyler üretilmiştir.
* **Mutasyon (Mutation):** %10 ihtimalle genlerde rastgele değişimler yapılmış ve sınır dışına taşmalar **Clamping** yöntemiyle engellenmiştir.
* **Elitizm (Elitism):** Her neslin en iyi 2 bireyi bozulmadan doğrudan bir sonraki nesle aktarılmıştır.
* **Ceza Yöntemi (Penalty Method):** $x_1 \cdot x_2 > 600$ olan, yani rafa sığmayan kutulara çok yüksek ceza puanı (-5000) verilerek elenmeleri sağlanmıştır.

---

## 📊 Sonuçlar

Yapılan optimizasyon sonucunda, algoritma kısıtlara tam uyum sağlayarak sınır değerlerine yakınsamıştır.

| Parametre | Bulunan Değer | Açıklama |
| :--- | :--- | :--- |
| **Genişlik ($x_1$)** | **34.54 cm** | 15-40 aralığında optimize edildi. |
| **Yükseklik ($x_2$)** | **17.37 cm** | 5-20 aralığında optimize edildi. |
| **Alan ($x_1 \cdot x_2$)** | **599.86 cm²** | 600 sınırına %99.9 oranında yaklaşıldı. |
| **Amaç Fonksiyonu ($y$)** | **450.41** | Maksimum verimlilik skoru. |


---

## 👨‍💻 Hazırlayan

* **Ad Soyad:** Halil Yaşar
* **Okul Numarası:** 2212721026
* **Ders:**  Yapay Zeka Sistemleri
