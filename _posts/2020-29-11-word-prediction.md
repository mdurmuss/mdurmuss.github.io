---
title: "N-gram ile Sonraki Kelime Tahmini"
layout: post
date: '2020-10-01 22:10:00'
tag:
- nlp
- python
- ngram
image: https://cdn.analyticsvidhya.com/wp-content/uploads/2019/08/language_model.png
headerImage: true
projects: true
hidden: true
category: project
author: mustafadurmus
externalLink: false
published: true
---

Bu proje ngram teknikleri kullanarak girdiden sonra gelebilecek olan kelimeleri tahmin etmeyi hedefler.


### Demo

[Link](https://arcane-scrubland-44556.herokuapp.com/) üzerinden uygulamayı test edebilirsiniz.

### Kullanım

[Github](https://github.com/mdurmuss/word-predictor/) üzerinden proje kodlarına erişebilirsiniz.
Repoyu indirdikten sonra gerekli kütüphaneleri **requirements.txt** ile kurabilirsiniz.

```shell
pip install -r requirements.txt
```

Flask'ın çalışması için komutları girin.

```shell
export FLASK_APP=app.py
flask run
```

Şimdi tarayıcınızda `localhost:5000` ziyaret edin. :tada:

![](https://raw.githubusercontent.com/mdurmuss/word-predictor/main/images/img1.png)

### Gerekli Düzenlemeler

- **Kullanıcıdan girdi olarak kelime alınmalı ve en yüksek 3 ihtimalli kelime gösterilmeli. :heavy_check_mark:**
- **Flask ile web üzerinde çalıştırma. :heavy_check_mark:**
- **Kelime düzeltme (spellchecking) fonksiyonu ekle. :heavy_check_mark:**
- Kelime kelime ayırım yaparken noktalama işaretleri siliniyor. Ancak nokta'dan sonra gelen kelime ile noktadan önce gelen kelime aslında komşu değildir. 
    - *Öğle yemeğini dışarda yedim. İş yerine yakın yeni bir yer keşfettim.* Bu cümlede **yedim** ile **İş** kelimeleri birbirinden bağımsızdır.

- Daha büyük bir veriseti ile dene.

- Birden fazla kelime ile tahmin yapma. (trigram)


