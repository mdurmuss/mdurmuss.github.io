---
title: "Python ve Test"
published: true
layout: post
date: '2019-06-19'
headerImage: true
tag:
  - python
  - test
  - unittest
star: true
category: blog
author: mustafadurmus
---

**Test**, kodun amacına ulaştığını göstermeye ve hataların önceden keşfedilmesine olanak sağlar.

Yazılımı bir sistem olarak adlandırırsak, sistemin beklenen veya beklenmeyen kullanımını yansıtacak bir test senaryosu hazırlanarak test oluşturmaya başlanır.

Test aşamaları genellikle 3 adımdan oluşur.

- Geliştirme Testi
- Dağıtım Testi
- Kullanıcı Testi

Geliştirme testi ise kendi içinde nesnelerin veya sınıfların test edilmesinden oluşan **birim testi**, birim testlerin birleşmesiyle oluşan **bileşen testi** ve bileşen testlerinin birleşmesiyle oluşan **sistem testi** ile oluşmaktadır.

------

Bu yazıda geliştirme testinin en küçük elemanı olan birim testi ele alınacaktır.

Önce fibonacci sayılarını bulan bir fonksiyon yazalım.

> **Fibonacci dizisi**, her sayının kendinden önceki iki sayıyla toplanması sonucu oluşan bir **sayı** **dizisidir.** 
>
> 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89 şeklinde ilerlemektedir.

```python
def fibo(number):
    if(number <=1):
        return number
    else
    	return fibo(number-1) + fibo(number-2)
```

- Fonksiyona dizideki hangi indis numarasına sahip sayının istendiğini gösteren bir sayı gönderilir.
- Sayı 1'den küçükse kendisi değilse rekürsif olarak kendisinden önceki 2 sayı toplanarak gönderilir ve değer elde edilir.

Fonksiyonumuz hazır olduğuna göre test edebileceğimiz birkaç değeri liste içinde gösterelim.

```python
values = [6,0,-1,3.3,True,"fibonacci"]
```

Ve fonksiyonun tüm bu değerlere karşılık ürettiği sonuçlara bakalım.

```python
8
0
-1
-0.5000000000000009
True
TypeError: '<=' not supported between instances of 'str' and 'int'
```

- 6 girdisine 8 cevabını verdi.
- 0 girdisine 0 cevabını verdi.
- -1 girdisine -1 cevabını verdi.
- 3.3 float değerine -0.5 cevabını verdi.
- True bool değerine True cevabını verdi.
- String ifadeye ise hata verdi.

Artık bu fonksiyon için birim testimizi yazabiliriz. Öncelikle test için ayrı bir dosya oluşturulur ve genellikle testi yapılacak dosyanın isminin başına "Test" yazılarak test dosyası isimlendirilir.

```python
import unittest
from function import fibo

class Test(unittest.TestCase):
    def test_numbers(self): # normal tests
        self.assertEqual(0,fibo(0))
        self.assertEqual(1,fibo(1))
        self.assertEqual(8,fibo(6))
        self.assertEqual(34,fibo(9))

    def test_values(self): # value tests
        self.assertRaises(ValueError,fibo,-2)

    def test_type(self): # type tests
        self.assertRaises(TypeError,fibo,3.3)
        self.assertRaises(TypeError,fibo,True)
        self.assertRaises(TypeError,fibo,"Fibonacci")

if __name__ == '__main__':
    unittest.main()
```

Önce test kütüphanesinden sınıf import edilir. Ardından test sınıfı adım adım oluşturulur.

- Test sınıfının alt sınıfı olarak kendi sınıfımızı yazdık.

- Test sınıfına ait tüm metotlar kesinlikle **test** anahtar kelime ile başlamalıdır. Import ettiğimiz test sınıfı bu şekilde test adımlarını fark etmektedir.

- ```python
  self.assertEqual(expected,value)
  ```

  assertEqual ile önce beklenen değer sonra fonksiyondan gelen değerler karşılaştırılır. Değerlere göre test hatalı veya doğrulandı şeklinde çıktı üretecektir.

- Birinci kısımda çeşitli değerler test edildi. İkinci ve üçüncü kısımda ise hata vermesi gereken değerler test edilir.

- ```python
  self.assertRaises(Error,function,value)
  ```

  Raise ile programın normal çalışmada hata vermeyeceği durumlarda hata vermesi sağlanır. Bu durumda ise

  - Negatif Değerler
  - String İfadeler
  - Float Değerler
  - Bool Değerler

  girdi olarak alındığında fonksiyonun hata döndürmesi sağlanır. Fonksiyonun son durumda şu şekli alır.

```python
def fibonacci(i):
    if type(i) not in [int]: # for type errors
        raise TypeError("Type must be integer")
    if i<0: # for value errors
        raise ValueError("Cannot be negative number")
    if i<=1: # if number is (zero or one) then return itself
        return i
    else:
        return fibonacci(i-1)+fibonacci(i-2)

```

```shell
...
----------------------------------------------------------------------
Ran 3 tests in 0.001s

OK

```

Test dosyası çalıştırıldığında ise çıktı yukarıdaki gibi olur. 3 ayrı test metodu ile test işlemleri gerçekleşti ve tüm testler başarıyla geçildi ve birim testi gerçekleştirilmiş oldu.

Test konusunun en önemli noktası ise, tüm yazılımın hatasız olduğunu değil testin tabii tutulduğu bölümünün yalnızca o kriterler için hatasız çalışabildiği gösterir.

