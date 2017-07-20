## SVM Nedir ?
### (Support Vector Machine)

İki veya daha fazla grup arasında olan sonsuz adet doğrudan hangisinin optimum olduğunu bulmamıza yarar.Örneğin düzlemimizde elma ve armutlar var.Bunlar iki boyutlu düzlemde elmalar bir tarafta armutlar bir tarafta olacak şekilde ayrıldığını düşünelim.Bu elma ve armutları birbirinden ayıran sonsuz adet vektör çizebiliriz.SVM bize bu vektörlerden hangisinin daha optimum olduğunu bulmamızı sağlar.Bu vektöre de 'hyperplane' denir.Bu hyperplane'ın vektörü henüz bilinmez durumdadır.Bu durumda Lagrange yöntemi ile hyperplane'ınımızın denklemini bulabiliriz.

[![image](https://www.svm-tutorial.com/wp-content/uploads/2014/11/01_svm-dataset1-separated-2.png)
<br>
Bu örnekte birden fazla vektör var ve bu vektörlerin hepsi doğru.Çünkü kadın ve erkekleri ikiye bölmüşler.Fakat doğru olmaları optime oldukları anlamına gelmiyor.İki gruba da yakın birbirine paralel iki çizgi çekilmesi gerekir.

[![image](https://i.hizliresim.com/aGEMYd.jpg)](https://hizliresim.com/aGEMYd)

Yukarıdaki şekilde iki farklı hiperdüzlem (aşırı düzlem) olasılığı bulunmasına karşılık SVM yönteminde bu olasılıklardan en büyük toleransa (offset) sahip olanı alınır.


### Bad
[![image](https://i.hizliresim.com/XX0A1o.png)](https://hizliresim.com/XX0A1o)
### GOOD 
[![image](https://i.hizliresim.com/zB3pjg.png)](https://hizliresim.com/zB3pjg)


### Eğer Data Çok Karışık İse ?

Data birbirine çok girmiş karışık bir şekilde duruyorsa , SVM kernel fonksiyonu sayesinde üçüncü bir özellik bulup üçüncü boyuta taşır.Yani siz bir kübe yukardan baktığınızı düşünün , hangi elma yukarda hangi elma aşağıda göremezsiniz . 3 boyutlu şekilde baktığınızı düşünün şimdi elmalar yukarda armutlar aşağıda kaldı . Bu sayede bizde vektörümüzü çizebiliyoruz.
K(x,y)
### Örnek Kernel Fonksiyonları

Linear
![image](http://latex.codecogs.com/gif.latex?k(x,%20y)%20=%20x%5ET%20y%20+%20c)<br><br>
X ve Y nin iç çarpımı ve isteğe bağlı bir c değişkeni
<br><br>Poly
![image](http://latex.codecogs.com/gif.latex?k(x,%20y)%20=%20(%5Calpha%20x%5ET%20y%20+%20c)%5Ed)

[![image](https://prateekvjoshi.files.wordpress.com/2012/08/2d-to-3d-projection.jpeg)

