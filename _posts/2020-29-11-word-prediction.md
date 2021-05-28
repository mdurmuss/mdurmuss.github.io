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

[Link](https://word-predictor.herokuapp.com/) üzerinden uygulamayı test edebilirsiniz.

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

