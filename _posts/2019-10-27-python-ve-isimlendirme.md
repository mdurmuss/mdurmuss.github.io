---
title: Python ve İsimlendirme
published: true
layout: post
date: '2019-10-27'
tag:
  - python
  - naming
  - zenofpython
star: true
category: blog
author: mustafadurmus
---
![Screenshot](/assets/images/readability_counts.jpg)

Yazıya [**The Zen of Python**]((https://zen-of-python.info/)) ile başlamak istiyorum. Bu 20 cümleye python dilinin manifestosu demek çok da yanlış olmaz.

- Beautiful is better than ugly.
- **Explicit is better than implicit.**
- Simple is better than complex.
- Complex is better than complicated.
- Flat is better than nested.
- Sparse is better than dense.
- **Readability counts.**
- Special cases aren't special enough to break the rules.
- Although practicality beats purity.
- Errors should never pass silently.
- Unless explicitly silenced.
- In the face of ambiguity, refuse the temptation to guess.
- There should be one-- and preferably only one --obvious way to do it.
- Although that way may not be obvious at first unless you're Dutch.
- Now is better than never.
- Although never is often better than *right* now.
- If the implementation is hard to explain, it's a bad idea.
- If the implementation is easy to explain, it may be a good idea.
- Namespaces are one honking great idea -- let's do more of those!

Python dilinin yazarı Guido ayrıca şöyle diyor.

> Kod yazıldığından daha çok okunur.

------

Günlerin kod yazmakla geçmesinin ardından geriye dönüp bakıldığında yazarın kendi yazdığı satırlar karşısında yarım saat geçirip anlamaya çalıştığı çok olmuştur benim de başıma birçok kez geldi. Her geliştiricinin böyle zamanları olur. 

Çözüm:

- Yorum satırları (python ve yorum ile alakalı ayrı bir yazı mutlaka gelecek)
- İsimlendirme

------

Kodlarken isimlendirme yapmak birçok kişi için geriye kalan işlerden daha fazla zaman alır. Mantıklı isimlendirme geriye döndüğünüzde size veya kodunuzu okuyana da zaman kazandırır. Her durumda olduğu gibi isimlendirmede de uyabileceğimiz bazı python standartları bulunur.

O zaman başlayalım!

- **Paketler**

  - Paket isimlerinin tamamı küçük harf olmalıdır.
  - Birden fazla kelimeye ihtiyacınız olduğunda alt çizgi kullanın.

- **Modüller**

  - Modül isimlerinin tamamı küçük harf olmalıdır.
  - Birden fazla kelimeye ihtiyacınız olduğunda alt çizgi kullanın.

- **Sınıflar**

  - Sınıf isimlerinin ilk harfi büyük diğerleri küçük olmalıdır.
  - Birden fazla kelimeye ihtiyacınız olduğunda bir sonraki kelimenin ilk harfi büyük yazılmalıdır. Bu yazıma **Camel Case** de denmektedir.


  ```python
  class HelloWorld ; class FirstPythonClass
  ```

- **Fonksiyonlar**

  - Fonksiyon isimlerinin tamamı küçük harf olmalıdır.

  - Birden fazla kelimeye ihtiyacınız olduğunda alt çizgi kullanın.

  - Bir sınıf içinde public olmayan sınıf isimlerine alt çizgi ile başlayın.

    ```python
    class FirstClass:
        def print()
	    pass
	
        def set_name(self, x)
	    pass
    
        def _get_name(self)
    
    ```

- **Sabit Değişkenler**

  - Sabit değişken isimlerinin tamamı büyük harf olmalıdır.
  - Birden fazla kelimeye ihtiyacınız olduğunda alt çizgi kullanın.

```python
PI = 3.14
GRAVITY = 9.8
MY_WORLD_NAME = "YOUR WORLD NAME"

print(PI)
print(GRAVITY)
print(MY_WORLD_NAME)
```

Görüldüğü üzere aslında öğrenilmesi gereken çok da fazla standart yok. Python dilinde isimlendirme yapmak için gereken her bilgi bir diğerini destekler niteliğindeydi. 

Son olarak bir senior ve bir junior geliştiricinin aralarında geçen bir konuşmada dikkatimi çeken bir cümleyi paylaşmak istiyorum.

> Senior Developer: "Junior'lar kodlama yaparken çalışsın da nasıl olursa olsun mantığıyla hareket ederken, bizler yazdığımız kodun çalışacağına eminiz ama nasıl daha güçlü daha sade ve daha geliştirilebilir yazmayı planlıyoruz."
