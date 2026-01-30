# wustl-ehms-2020

WUSTL-EHMS-2020 veri seti kullanılarak ağ trafiği üzerinde saldırı tespiti gerçekleştiren bir CNN modeli geliştirilmeye çalışılmıştır. Normal ve saldırı trafiğini doğrulukla ayırt edebilen bir derin öğrenme modeli oluşturmak ve model performansını çeşitli metriklerle değerlendirmek amaçlanmıştır. 

Kimlik bilgisi içeren ve modele katkı sağlamayacak sütunlar SrcAddr, DstAddr, SrcMac, DstMac ve Attack Category çıkartılmıştır. 

Kategorik özellikler içeren Dir, Flgs ve Sport Label Encoding yöntemiyle sayısal forma dönüştürülmüştür. 

Eğitim/Test oranı: %80 / %20 dir ve bölme işlemi stratify=y parametresi ile yapılmıştır. 

Ölçeklendirme için MinMaxScaler kullanılmıştır. 

Veri sızıntısını önlemek için ölçeklendirme yalnızca eğitim verisi üzerindedir. 

Saldırı sınıfının az olması nedeniyle class weight yöntemi uygulanmıştır. 

Model 64 ve 128 olmak üzere iki adet Conv1D katmanından oluşmaktadır ve evrişim katmanlarını özellik boyutunu azaltmak ve hesaplama maliyetini düşürmek amacıyla MaxPooling1D katmanları takip etmektedir. 

Overfitting önlenmesi için %30 oranında Dropout uygulanmış, ardından Dense katman ile sınıflandırma süreci gerçekleştirilmiştir.  

Modelin çıkış katmanında ikili sınıflandırma problemi için uygun olan sigmoid aktivasyon fonksiyonu kullanılmıştır.  

Model, Adam optimizasyon algoritması ile eğitilmiş olup learning rate değeri 0.001 olarak belirlenmiştir.  

Kayıp fonksiyonu olarak Binary Crossentropy kullanılmış, eğitim sürecinde batch size 64 ve epoch sayısı 50 olarak ayarlanmıştır. 

En yüksek val accuracy 40. epoch’ta %94,33 olarak elde edilmiştir. 

AUC değeri: 0.900 olarak hesaplanmıştır.
