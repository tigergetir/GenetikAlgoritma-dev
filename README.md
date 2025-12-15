# Genetik Algoritma ile Kısıtlı Optimizasyon: Öğrenci Etüt Planlaması

Bu proje, "Öğrenci Etüt Programı Planlaması" senaryosu (Senaryo 9) kapsamında, belirli kısıtlamalar altında bir amaç fonksiyonunu maksimize etmek için **Genetik Algoritma (GA)** kullanan bir Python uygulamasıdır.

Proje, bir öğrencinin Matematik ($x_1$) ve Fen ($x_2$) derslerine ayıracağı çalışma saatlerini optimize ederek, sınav başarısını (skorunu) en üst düzeye çıkarmayı hedefler.

## 📌 Proje Hakkında

Bu çalışma, klasik bir optimizasyon problemini evrimsel hesaplama yöntemlerinden biri olan Genetik Algoritma ile çözmektedir. Algoritma, rastgele oluşturulan bir çözüm popülasyonunu; **seçim (tournament selection)**, **çaprazlama (crossover)** ve **mutasyon (mutation)** operatörlerinden geçirerek en iyi sonucu bulmaya çalışır.

Problemin kısıtlarını ihlal eden çözümler (örneğin toplam çalışma saatini aşmak), **Ceza Fonksiyonu (Penalty Function)** yöntemi ile "cezalandırılarak" uygunluk (fitness) değerleri düşürülür ve popülasyondan elenmeleri sağlanır.

## 🔢 Matematiksel Model

Problem, verilen senaryoya uygun olarak aşağıdaki gibi modellenmiştir:

### 1. Amaç Fonksiyonu (Maximize)
Amaç, başarı skorunu maksimize etmektir:

$$f(x_1, x_2) = 4x_1 + 5x_2 - 0.5x_1^2 - 0.2x_2^2$$

Burada:
* **$x_1$**: Matematik çalışma saati.
* **$x_2$**: Fen çalışma saati.

### 2. Kısıtlar (Constraints)
Çözümün geçerli olabilmesi için aşağıdaki koşullar sağlanmalıdır:
1.  **Toplam Süre Kısıtı:** $x_1 + x_2 \le 12$ (Toplam çalışma saati 12'yi geçemez).
2.  **Minimum Fen Kısıtı:** $x_2 \ge 2$ (Fen dersine en az 2 saat ayrılmalıdır).
3.  **Sınır Değerler:** $0 \le x_1, x_2 \le 10$.

## ⚙️ Algoritma Parametreleri

Kod içerisinde kullanılan Genetik Algoritma konfigürasyonu şöyledir:

| Parametre | Değer | Açıklama |
| :--- | :--- | :--- |
| **Popülasyon Boyutu** | 60 | Her nesildeki birey (çözüm) sayısı. |
| **Nesil Sayısı** | 80 | Algoritmanın çalışacağı iterasyon sayısı. |
| **Seçim Yöntemi** | Turnuva (k=3) | Rastgele 3 bireyden en iyisi ebeveyn olarak seçilir. |
| **Çaprazlama** | Tek Noktalı | %50 ihtimalle ebeveyn genleri tek bir noktadan karıştırılır. |
| **Mutasyon Oranı** | 0.1 | Her genin %10 ihtimalle değişime uğrama olasılığı (Gauss gürültüsü ile). |
| **Elitizm** | 1 | En iyi birey bozulmadan doğrudan bir sonraki nesle aktarılır. |

## 🚀 Kurulum ve Çalıştırma

Bu projeyi çalıştırmak için bilgisayarınızda Python ve Jupyter Notebook (veya Google Colab) ortamı bulunmalıdır.

### 1. Gerekli Kütüphaneler
Projenin çalışması için `numpy` ve `matplotlib` kütüphanelerine ihtiyaç vardır. Yüklemek için:
```bash
pip install numpy matplotlib

2. Kodun Çalıştırılması
Terminal veya komut satırında proje dizinine gelerek aşağıdaki komutu çalıştırın:
jupyter notebook yapay_zeka_ilk_ödev.ipynb

Çıktılar ve Görselleştirme
Kod çalıştırıldığında optimizasyon sürecini analiz etmek için şu çıktılar üretilir:

Metin Çıktıları:

En iyi çözümün bulunduğu nesil numarası.

Optimize edilmiş x 
1
​
  ve x 
2
​
  değerleri.

Elde edilen maksimum skor (fitness değeri).

Kısıtların sağlanıp sağlanmadığına dair doğrulama (Feasibility Check).

Grafiksel Analizler:

Amaç Fonksiyonu ve Uygun Bölge: Fonksiyonun kontur haritası üzerinde kısıt sınırları (kırmızı çizgiler) ve bulunan en iyi çözüm (beyaz nokta) gösterilir.

Skor Evrimi: Nesiller boyunca popülasyonun en iyi skorunun nasıl arttığını gösteren çizgi grafiği. Bu grafik algoritmanın yakınsama başarısını gösterir.

📂 Dosya Yapısı
yapay_zeka_ilk_ödev.ipynb: Projenin kaynak kodlarını, açıklamalarını ve grafikleri içeren Jupyter Notebook dosyası.

README.md: Proje dokümantasyonu (Bu dosya).
