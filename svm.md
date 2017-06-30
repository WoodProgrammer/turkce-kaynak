## SVM Nedir ?
### (Support Vector Machine)

İki veya daha fazla grup arasında olan sonsuz adet doğrudan hangisinin optimum olduğunu bulmamıza yarar.Örneğin bir tarafta erkekler diğer tarafda kadınların çoğunlukta olduğu bir koordinat sistemi düşünelim.En optimum doğrumuzu bulmak için iki gruptan da diğer gruba en yakın olanı seçeriz.Bunların arasında olan doğru en optimum doğrumuzdur.

![image](https://www.svm-tutorial.com/wp-content/uploads/2014/11/01_svm-dataset1-separated-2.png)
<br>
Bu örnekte birden fazla doğru var ve bu doğruların hepsi doğru.Çünkü kadın ve erkekleri ikiye bölmüşler.Fakat doğru olmaları optime oldukları anlamına gelmiyor.İki gruba da yakın birbirine paralel iki çizgi çekilmesi gerekir.

[![image](https://i.hizliresim.com/7NvXGL.jpg)](https://hizliresim.com/7NvXGL)

Burada iki doğru arasında sonsuz adet doğru vardır.Bu doğruların en doğru şekilde kullanılması için iki noktaya en uzak olan doğru seçilir.
Kırmızı çizgi wx – b = 0 formulü ile hesaplanır.<br>
Sarı Çizgi wx – b = 1 formulü ile hesaplanır.<br>
Mavi Çizgi wx – b = -1 formulü ile hesaplanır.<br>
Sarı ve mavi çizgi arasında ki mesafe 2/||w|| ile hesaplanır.Bu aynı zamanda tolerans(offset) olarak isimlendirilir. <br>
Kırmızı çizgi Hyperlane olarakda geçer




[![image](https://i.hizliresim.com/aGEMYd.jpg)](https://hizliresim.com/aGEMYd)

Yukarıdaki şekilde iki farklı hiperdüzlem (aşırı düzlem) olasılığı bulunmasına karşılık SVM yönteminde bu olasılıklardan en büyük toleransa (offset) sahip olanı alınır.

### Örnek Kod

```python
import matplotlib.pyplot as plt
from sklearn import datasets
from sklearn import svm
import numpy as np
from matplotlib import style

style.use("ggplot")

x = np.array([
    [2,2],
    [2,3],
    [7,4],
    [7,5],
    [2,1],
    [7,7],
    [6,4],
    [4,3],
    [5,4]
])

y = [0,0,1,1,0,1,1,0,1]

clf = svm.SVC(kernel='linear', C = 1.0)
clf.fit(x,y)
w = clf.coef_[0]
a = -w[0]/w[1]
xx = np.linspace(0, 12) # 0-12 aras, hyperline cizmek
yy = a * xx - clf.intercept_[0] / w[1]
h0 = plt.plot(xx, yy, 'k-', label="non weighted div") #-1
plt.scatter(x[:, 0], x[:, 1], c= y)
plt.legend()
plt.show()

```
