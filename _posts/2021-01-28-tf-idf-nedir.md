---
title: "TF-IDF Nedir?"
published: true
layout: post
date: '2021-01-28'
tag:
  - statistic
  - nlp
  - text-analysis
  - semantic
star: true
category: blog
author: mustafadurmus
---

![Screenshot](../assets/images/tf-idf.png)

TF-IDF (term frequency–inverse document frequency), sözcüğün bulunduğu dökümanı ne kadar temsil ettiğini gösteren bir istatistiksel değerdir. TF, DF ve IDF kısımlarını ayrı ayrı açıklayalım.



### TF (Terim Sıklığı)

İlgili kelimenin dökümandaki frekansıdır. Kelimenin **dökümanda geçme sayısını**, **dökümandaki toplam kelime sayısına** bölerek elde edilir.

### DF (Döküman Sıklığı)

TF ile benzemektedir ama bu kez diğer dökümanlara odaklanır. **Döküman sayısının** ilgili **kelimenin geçtiği döküman sayısına** bölünmesi ile hesaplanır.

### IDF (Ters Döküman Sıklığı)

DF değerinin logaritması alınarak hesaplanır. 

> Bir kelime diğer dökümanlarda ne kadar sık geçiyorsa DF değeri artar, IDF değeri o kadar azalır.



![Screenshot](../assets/images/tf-idf-formula.png)



### Örnek

Basit bir senaryo ve **python** ile konuyu detaylı inceleyelim.

Öncelikle elimizde 4 tane döküman olsun.

```python
doc1 = "a a b c"
doc2 = "a c c c d e f"
doc3 = "a c d d d"
doc4 = "a d f"
```

#### Problem1

**D** anahtar kelimesinin **3.dökümanı** ne denli temsil ettiğini bulalım yani tf-idf değerini bulalım.

```python
key = "d"
```

- Dökümanlarımızın tipi *string*. Daha kolay işlem yapabilmek için *liste* haline getirelim.

  ```python
  doc1 = doc1.split(" ")
  doc2 = doc2.split(" ")
  doc3 = doc3.split(" ")
  doc4 = doc4.split(" ")
  ```

- TF değerini hesaplayalım.

  ```python
  TF = doc3.count(key) / len(doc3)  # 3 / 5 == 0.6
  ```

- Kelimenin kaç dökümanda geçtiğini hesaplayalım.

  ```python
  all_documents = [doc1, doc2, doc3, doc4] # tüm dökümanları birleştir.
  count = 0
  for doc in all_documents:
      for word in doc:
          if word == key:
              count += 1
              break
  # count = 3
  ```

- Toplam döküman sayısını ve bulduğumuz değeri logaritmaya sokarak **IDF** değerini hesaplayalım.

  ```python
  total_doc_number = len(all_documents)
  DF = total_doc_number / count
  from math import log10
  IDF = log10(DF) # 0.12493873660829993
  ```

  

- Ve artık bulduğumuz sonuçları çarparak **TF-IDF** değerini görelim.

  ```python
  TF * IDF  # 0.07
  ```

#### Problem2 

**F** anahtar kelimesinin **2.döküman** için tf-idf değerini bulalım.

```python
key = "f"

# TF
TF = doc4.count(key) / len(doc4)

# IDF
all_documents = [doc1, doc2, doc3, doc4]
count = 0
for doc in all_documents:
    for word in doc:
        if word == key:
            count += 1
            break

total_doc_number = len(all_documents)
DF = total_doc_number / count

from math import log10
IDF = log10(DF)

TF * IDF # 0.1
```

Görüldüğü üzere 3 ayrı dökümanda geçen **D** daha düşük tf-idf değerine sahipken, 2 ayrı dökümanda geçen **F** daha yüksek tf-idf elde etti. İlgili dökümanlarda geçme sayılarını da unutmayalım. 

Bir sonraki yazıda görüşmek dileğiyle. 

## Referanslar

- [1](https://cs50.harvard.edu/ai/2020/weeks/6/)
- [2](https://en.wikipedia.org/wiki/Tf–idf)
- [3](https://nlpforhackers.io/tf-idf/)

