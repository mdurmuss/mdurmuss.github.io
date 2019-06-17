---
published: true
layout: post
date: '2019-03-09 22:44'
image: /assets/images/markdown.jpg
tag:
  - tensorflow
  - windows
  - gpu
  - deep learning
star: true
category: blog
author: mustafa
description: Markdown summary with different options
title: 'Windows 10, Tensorflow-GPU'
---
Derin öğrenme modelleri üzerine çalışmaya başladığım ilk andan itibaren yaşadığım en önemli sorun bu karmaşık yapıyı öğrenmek değil
eğitim için harcadığım vakitler oldu. [Tensorflow](https://www.tensorflow.org/) 'u CPU için kurup gerekli eğitimleri bilgisayarın işlemcisi üzerinden eğitiyordum. Hatta bir
sinir ağını eğitmek için işlemci kesintisiz bir gün çalışmıştı. 
## Peki herkes GPU kullanabilir mi?
Tensorflow için 2 seçeneğimiz var. CPU veya GPU. CPU kurulumunda yapacağınız tüm işlemler bilgisayarınızın kendi işlemcisini kullanacaktır. Tahmin edeceğiniz üzere bilgisayarın kullandığı işlemciye bir de eğitim için bir yük bindirdiğinizde hem bilgisayarınız ısınacak hem de eğitimlerin çok yavaş olduğunu göreceksiniz. Diğer seçeneğimiz olan GPU ise bu kurulumu ekran kartının işlemcisi üzerine yapar. İki ayrı işlemci farklı işleri aynı anda yaptığında daha hızlı eğitimler görürüz. 
Ekran kartınızın Nvidia olması zorunluluk. Eğer öyleyse bu [link](https://developer.nvidia.com/cuda-gpus) 'e tıklayarak kartınızın puanını bulun. 3.5 ve üzeri puanı olan tüm ekran kartları GPU kurulumu desteklemekte.

### Tensorflow GPU
Öncelikle CUDA ve CuDNN kurmamız gerekiyor.

**1.CUDA** 
* [Link](https://developer.nvidia.com/cuda-downloads) 'ten indirin.
* 10.0 sürümünü kurun, diğer sürümlerde hata alınabiliyor.
* Ardından bilgisayar-sağ tık-özellikler-gelişmiş sistem ayarları-ortam değişkenleri yolunu izleyin.
* Burada PATH kısmını seçip düzenleyin. Yeni'ye tıklayın ve şu yolları ekleyin.
	1. C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin
	2. C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\libnvvp
	3. C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\extras\CUPTI\libx64

**2.CuDNN** 
- [Link](https://developer.nvidia.com/rdp/cudnn-archive)'ten indirin.
- Ücretsiz indirim için üyelik gerekiyor, olun ve CUDNN 7.4.2 for CUDA tool kit 10.0'ı indirin.
- Bir zip dosyası inecek, buradan cudnn64_7.dll isimli dosyası kopyalayıp C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin  klasörüne yapıştırın.

**3.GPU Update**
- Ekran kartınızı [güncelleyin](http://www.nvidia.com.tr/drivers).

**4.Terminal**
- Komut istemi'ni açın ve şu komutu yazın.
~~~
pip install --upgrade tensorflow-gpu
~~~

**5.Test**
- Kurabildik mi gerçekten? Hadi test edelim. Komut istemci'sine şu kodları yazalım.
~~~
python
import tensorflow as tf
hello = tf.constant("Hello Tensorflow for GPU")
ses = tf.Session()
print(ses.run(hello))
~~~
Kurulum tamamlandı.Bu komuttan sonra Hello Tensorflow yazısını göreceksiniz ve kullandığınız işlemci hakkında bilgileriniz görüntülenecek. Bunlar hata değil yalnızca bilgilendirme metinleridir.
