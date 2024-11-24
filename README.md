# Breast-Cancer-Detection-Using-SVM-with-SMOTE-and-Model-Optimization

![bre](https://github.com/user-attachments/assets/611f7d3e-6ff1-4542-b4a2-699e797ee27f)

Bu proje, meme kanseri teşhisi için kullanılan bir veri seti üzerinde çalışır. Amaç, tümörlerin iyi huylu (Benign) veya kötü huylu (Malignant) olduğunu sınıflandırmaktır. Projede, Destek Vektör Makineleri (Support Vector Machines - SVM) algoritması kullanılarak bu sınıflandırma yapılır. Ayrıca, sınıf dengesizliği problemini çözmek için SMOTE (Synthetic Minority Oversampling Technique) uygulanır ve model performansı değerlendirilir.


# 1. Veri Setinin Hazırlanması

Proje, meme kanseri veri setini kullanır. Bu veri seti, bir hastanın çeşitli biyopsi özelliklerini içerir:
Örneğin: Tümör çapı (radius_mean), yüzey pürüzsüzlüğü (smoothness_mean) ve diğer biyopsi sonuçları.
Amaç, bu özelliklere bakarak tümörün iyi huylu (B) veya kötü huylu (M) olduğunu sınıflandırmaktır.


X ve id gibi sınıflandırmaya katkı sağlamayan sütunlar veri setinden çıkarılır. Diagnosis sütunu, 0 (Benign) ve 1 (Malignant) olarak yeniden kodlanır. Eksik veri olup olmadığı analiz edilir. Varsa uygun doldurma işlemleri yapılır.

# 2. Veri Görselleştirme

Verilerin genel dağılımını ve sınıf ayrımlarını görmek için görselleştirme yapılır:
Scatter Plot: Tümör çapı (radius_mean) ve yüzey dokusu (texture_mean) arasındaki ilişki, sınıflara göre ayrılarak görselleştirilir.
Pairplot: Seçilen birkaç özelliğin birbiriyle ilişkisi ve sınıflar arasındaki ayrım analiz edilir.
Bu görselleştirmeler, verilerin sınıflar arasında ayrılabilir olup olmadığını anlamaya yardımcı olur.

![scatter_plot](https://github.com/user-attachments/assets/ada6d1fa-ab24-4890-9689-84190016f157)
![pairplot](https://github.com/user-attachments/assets/94cb5615-9df0-4911-9011-4eca7cb35bb4)

# 3. Verilerin Standartlaştırılması

SVM algoritması, özelliklerin ölçeklerine duyarlıdır. Bu nedenle tüm sayısal özellikler, StandardScaler ile normalize edilir. Bu işlem, model performansını artırır.

![ROC Curve](https://github.com/user-attachments/assets/75c27bb0-a5e6-4d64-b4ac-bb4f44dda7b3)

# 4. Model Eğitimi ve Değerlendirilmesi

Farklı SVM Modelleri:
- **Linear: Doğrusal olarak ayrılabilir sınıflar için uygundur.**
- **Radial (RBF): Daha karmaşık sınıflar için esneklik sağlar.**
- **Polynomial: Çoklu doğrusal olmayan sınıflar için uygundur.**
- **Sigmoid: Özellikle probabilistik sınıflandırmalarda tercih edilir.**
  
![linear svm](https://github.com/user-attachments/assets/c39f2b17-66f2-4d44-a213-df0ea77d9d39)
![radial svm](https://github.com/user-attachments/assets/6d5c3784-9c94-46a2-8112-a34b18196e31)
![polynominal svm](https://github.com/user-attachments/assets/e8a45e69-8514-4d9e-ae8e-86947d8ef3c3)
![sigmoid svm](https://github.com/user-attachments/assets/73cf5887-e761-4a46-89eb-c1ca49cc26c0)

![model_accuracy_comparison](https://github.com/user-attachments/assets/54f05397-8d3f-4ecb-beb4-5f4eb505e183)

Her bir model, eğitim veri setinde eğitilir ve test setinde değerlendirilir.

Performans Değerlendirmesi:

- **Confusion Matrix: Gerçek ve tahmin edilen sınıflar arasındaki ilişki.**
_ **Classification Report: Doğruluk, hassasiyet, özgüllük ve F1 skoru gibi metriklerle performans ölçülür.**

# 5. Hiperparametre Optimizasyonu

Özellikle Radial SVM için GridSearchCV kullanılarak en iyi parametreler (C ve gamma) aranır. Optimize edilmiş model yeniden eğitilir ve performansı test edilir.

# 6. Sınıf Dengesizliğini Çözme (SMOTE)

Verilerde sınıf dengesizliği varsa, bu dengesizlik SMOTE yöntemi ile çözülür:Azınlık sınıfı için sentetik örnekler üretilir. Dengeli veri seti ile modeller yeniden eğitilir.
SMOTE sonrası, sınıfların dağılımı görselleştirilir ve modelin performansı iyileştirilir.

# 7. Model Performansının Görselleştirilmesi

Her modelin doğruluk skorları bir çubuk grafik ile karşılaştırılır. ROC Eğrisi ve AUC Skoru: Özellikle RBF çekirdekli SVM modelinin sınıflandırma performansı analiz edilir.




# Projenin Avantajları

- **Hassas Tespit: Meme kanseri gibi kritik bir alanda doğru sınıflandırma yapmak hayati önem taşır. Farklı modeller denenerek en iyi sonucu veren model seçilir.**
- **Sınıf Dengesizliği Çözümü: SMOTE, sınıf dengesizliğini giderir ve azınlık sınıfının (kötü huylu tümör) daha doğru sınıflandırılmasını sağlar.**
- **Farklı Çekirdeklerin Karşılaştırılması: Her çekirdek fonksiyonunun performansı karşılaştırılır, böylece hangi çekirdeğin hangi tür verilerde daha iyi çalıştığı anlaşılır.**
- **Optimizasyon: Hiperparametre optimizasyonu ile modellerin performansı en üst düzeye çıkarılır.**
- **Kapsamlı Değerlendirme: Confusion Matrix, ROC Eğrisi ve diğer metriklerle modeller detaylı olarak analiz edilir.**
