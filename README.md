
### python ile makine öğrenimi projesi
### Proje Özeti
Bu çalışmanın temel amacı, anonimleştirilmiş hasta verilerini kullanarak Astım ve KOAH (Kronik Obstrüktif Akciğer Hastalığı) tanısını sınıflandırmak ve test veri kümesi üzerinde tahminlerde bulunmaktır. Bağımlı değişken TANI değişkenidir. Proje kapsamında veri ön işleme, keşifçi veri analizi (EDA), özellik mühendisliği ve çeşitli makine öğrenmesi modellerinin karşılaştırılması adımları uygulanmıştır.


#### Veri Seti ve Ön İşleme
Veri seti üzerinde kapsamlı bir ön hazırlık süreci yürütülmüştür:


Veri Tipi Düzenlemesi: Kategorik ve numerik değişkenlerin tipleri (object, float/int) düzeltilmiştir.

#### Eksik Değer Analizi ve Doldurma:

Sigara kullanım alışkanlıklarına (içmemiş, bırakmış, halen içiyor) dayalı mantıksal çıkarımlar yapılarak ilgili sayısal değişkenlerdeki eksiklikler giderilmiştir.

Ailedeki hastalık öyküsüne (Anne, Baba, Kardeş vb.) göre tutarsızlıklar giderilmiş ve eksik bilgiler "bilgiyok" sınıfı ile veya mantıksal çıkarımlarla doldurulmuştur.


Aykırı Değer Analizi: Değişkenlerdeki aykırı değerler tespit edilmiş (örn: sigara bırakma süresindeki ekstrem değerler), ancak baskılama yapılmadan bırakılması tercih edilmiştir.


Özellik Mühendisliği (Feature Engineering): Seçili değişkenler için One-Hot Encoding uygulanmış ve çarpık dağılıma sahip veriler için Z-Score Standartlaştırması (StandardScaler) kullanılmıştır.

#### Keşifçi Veri Analizi (EDA)
Veri setini anlamak adına yapılan analizlerden bazı çıkarımlar şunlardır:


Hedef Değişken: Tanı değişkeninin dengeli bir dağılıma sahip olduğu görülmüştür.

İlişkiler:

Yaş arttıkça FEV1 değerinin düştüğü (negatif korelasyon) gözlemlenmiştir.

Erkeklerde KOAH tanısı daha yaygınken, kadınlarda Astım tanısı daha baskındır.

KOAH hastalarının yaş ortalaması Astım hastalarına göre daha yüksektir.


Solunum Fonksiyonları: FEV1% ve PEF% arasında güçlü pozitif korelasyon tespit edilmiştir.

#### Kullanılan Modeller ve Yöntemler
Model başarısını ölçmek için Accuracy, Precision, Recall, F1-Score ve ROC-AUC metrikleri kullanılmıştır. Aşağıdaki algoritmalar test edilmiştir:


KNN (K-Nearest Neighbors): En iyi k değeri 11 olarak belirlenmiştir (Accuracy: 0.86).


Naive Bayes: Accuracy: 0.83, AUC: 0.8986.



Logistic Regression: Accuracy: 0.87, AUC: 0.94.



Decision Tree (Karar Ağaçları): Accuracy: 0.85.


Random Forest: Accuracy: 0.88, AUC: 0.9516.



Bagging Classifier: Accuracy: 0.90, AUC: 0.956.



Gradient Boosting: Accuracy: 0.86, AUC: 0.9490.



AdaBoost: Accuracy: 0.87, AUC: 0.94.



CatBoost: En iyi performansı gösteren model olarak seçilmiştir.

#### Sonuç
Yapılan karşılaştırmalar sonucunda CatBoost modeli seçilmiştir.


Model Performansı: %97 


Hata Oranı: 0.272 (En düşük hata) 

CatBoost, hem en yüksek doğruluk skoruna hem de en düşük hataya sahip olması nedeniyle final modeli olarak belirlenmiştir.

Bu proje, makine öğrenmesi algoritmalarının sağlık verileri üzerindeki sınıflandırma başarısını göstermek amacıyla akademik bir ödev kapsamında hazırlanmıştır.
