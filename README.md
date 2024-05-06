# Akbank_APRM

Bu makine öğrenmesi modeli, başta serum kreatinin ve ejeksiyon fraksiyonu değerleri olmak üzere; yaş, diyabet, sigara içme durumu gibi kriterler üzerinden kalp krizi geçiren kişilerin hayatta kalıp kalmayacaklarını tahmin etmektedir.

Modelde kullanılan veri seti: 10.24432/C5Z89R DOI numaralı 2/4/2020 tarihli "Heart Failure Clinical Records" adlı csv dosyasıdır. Dosya UCI Machine Learning Repository platformunun public olarak yayınladığı veri setleri arşivinden alınmıştır. bknz:(https://archive.ics.uci.edu/dataset/519/heart+failure+clinical+records)

Makalede, Serum Creatinine ve Ejection Fraction değerlerinin bir kişinin kalp krizi geçirdikten sonra hayatta kalma olasılıklarını etkileyen birincil faktör olduğu iddia edilmektedir.

Hasta kayıt verileri ilgili Pandas fonksiyonları ile incelendikten sonra uygun bir şekilde işlenip yaş verileri kategorize edilerek feature engineering gerçekleştirilmiştir.

İlgili veriler feature engineering işleminin aradından Serum Creatinin, Ejection Fraction gibi numerik değerler StandardScaler ile model trainingi için uygun formata getirilmiştir. Kategorize edien yaş verisi dışında geri kalan non-numerical veriler hali hazırda verisetinde 1 ve 0 olarak kodlandığı için LabelEncoder veya OneHotEncoder gibi işlemlerden geçirilmemişlerdir.

 Ardından kayıtlardaki parametrelerin korelasyon ve bar grafikleri çizilerek makalenin iddiası nicel olarak incelenmiştir. (Detaylı notlar kod dosyasındaki comment satırlarında görülebilir)

Logistic Regression modeli işlenmiş veri ile train edildikten sonra ilgili model skorları incelenmiş ve ardından modelin performansının arttırılması ve overfitting'ten kaçınmak için RandomizedSearchCV aracılığı ile Hyperparameter Tuning yapılmış, ilgili sonuçlar yeni parametre ve model ile tekrar incelenmiştir.

Kod dosyasında da bulunan ilgili model sonuç raporu aşağıdadır:

```
Accuracy: 0.8
Confusion Matrix:
 [[34  1]
 [11 14]]
Classification Report:
               precision    recall  f1-score   support

           0       0.76      0.97      0.85        35
           1       0.93      0.56      0.70        25

    accuracy                           0.80        60
   macro avg       0.84      0.77      0.78        60
weighted avg       0.83      0.80      0.79        60

Cross-Validation Scores: [0.8        0.8        0.83333333 0.86666667 0.8        0.96666667
 0.86666667 0.76666667 0.6        0.86206897]
Average Cross-Validation Score: 0.8162068965517241
En İyi Parametreler: {'C': 1.9894240408880515, 'solver': 'lbfgs'}
En İyi Skor: 0.7931656754386582
Accuracy (En İyi Hiperparametre):
 0.7833333333333333
Confusion Matrix (En İyi Hiperparametre):
 [[34  1]
 [12 13]]
Classification Report (En iyi Hiperparametre):
               precision    recall  f1-score   support

           0       0.74      0.97      0.84        35
           1       0.93      0.52      0.67        25

    accuracy                           0.78        60
   macro avg       0.83      0.75      0.75        60
weighted avg       0.82      0.78      0.77        60

```
