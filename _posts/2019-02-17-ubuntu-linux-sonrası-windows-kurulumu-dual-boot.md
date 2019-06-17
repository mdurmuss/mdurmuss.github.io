---
published: false
layout: post
date: '2019-02-17'
title: Ubuntu Yanına Windows (Dual Boot)
image: /assets/images/markdown.jpg
tag:
  - dual boot
  - windows
  - linux
  - boot order
  - operating system
star: true
category: blog
author: mustafa
---
Bu konuda bir araştırma yaptığınızda genellikle çoğu insanın önce Windows ardından Ubuntu veya linux dağıtımlarından birini kurduğunu görürsünüz. Bu yazı diğer soruya odaklanacak, eğer Ubuntu'dan sonra windows kurmak isteseydiniz nasıl olurdu?

Bilgisayarınızda hali hazırda çalışan bir Ubuntu işletim sisteminiz olduğu varsayılarak adım adım nasıl dual boot yapılır, anlatılacaktır.
### WINDOWS'U İNDİR
Microsoft daha önceden alışık olmadığımız ücretsiz bir şekilde Windows'u indirip kurmamıza izin veriyor. Tabii bir süreliğine. [Windows](https://www.microsoft.com/tr-tr/software-download/windows10ISO)'u sahip olduğunuz işlemciye göre indirin.
### PARÇALARA AYIR
Eğer Ubuntu için hard disk'inizde belirli bir yer ayırıp oraya kurmadıysanız tüm hafızanızı bu işletim sistemi için ayırmışsınız demektir. Bu adım biraz can sıkıcı olabilir çünkü hard diskinizden kullanmadığınız bir bölümü ayırmanız gerekecek ve bu biraz zaman alan bir işlem. Ubuntu Software'dan [Gparted](https://gparted.org/) uygulamasını indirelim. Gparted bölme işlemlerini komut satırı yerine arayüzden yapmamızı sağlayan bir araç.![Screenshot from 2019-02-13 19-43-45.png]({{site.baseurl}}/img/Screenshot from 2019-02-13 19-43-45.png)
Gördüğünüz üzere Ubuntu için çeşitli bölümler ayrılmış durumda. Ext4 hafıza için ayrılan kısım ve harddisk'in tamamını kapsıyor. Parçalama işlemini oturumdan yapamıyoruz. Bu sebeple;
- Bir [Ubuntu](https://www.ubuntu.com/download/desktop) boot usb'si veya cd'si takın ve boot edin.
- Ubuntu'yu dene seçeneğine tıklayın. 
- Ardından gparted uygulamasını açın. 

Şimdi ayırma işlemini yapabildiğinizi göreceksiniz. 
![Screenshot from 2019-02-17 15-38-33.png]({{site.baseurl}}/img/Screenshot from 2019-02-17 15-38-33.png)

Ubuntu'nun yüklü olduğu alana sağ tıklayıp yeniden boyutlandır'ı seçin. Karşınıza yukarıda gördüğünüz alan çıkacaktır. Windows için istediğiniz kadar yer ayırıp kapatın. Boş alanın dosya sistemini NFTS yapıp tüm işlemleri onayla'ya tıklayın. Ayırdığınız kapasiteye göre bu işlem vakit alacaktır. Yalnızca Windows sistem dosyalarının 20gb'a yakın yer tuttuğunu unutmayın. Örnek olarak 200GB hafıza alanı 2 saatte tamamlandı.
### WINDOWS KURULUMU
[WoeUsb](https://github.com/slacka/WoeUSB) ile boot edilebilir bir Windows usb'sini Ubuntu'da oluşturabilirsiniz. Artık Windows boot usb'nizi takıp boot ettiğinizde karşınıza gelen Windows için yer belirle kısmında az önce ayırdığınız alanı görebilirsiniz. Bu bölümü seçip gerekli adımları uygulayın ve Windows'u kurun.
### BOOT ORDER
Windows'unuz kuruldu ve gerekli güncellemeler yapıldı. Artık 2 işletim sistemine sahipsiniz. Bilgisayarınızı kapattınız ve bir süre sonra tekrar açtınız. Ve? Bir sorun var değil mi? Siz bir seçim  yapmadığınız halde Windows otomatik olarak açıldı. Nasıl tekrar Ubuntu'yu boot edeceksiniz? Bilgisayarınızın boot ayarlarına girdiğinizde orada Ubuntu'yu gördünüz ve çalıştırdınız. Hep buraya girmek zorunda mısınız? Hayır tabiiki. İhtiyacımız olan şey [GRUB](https://www.gnu.org/software/grub/). 
Windows kurulumu esnasında Grub bir şekilde silinir. Grub menüsü bilgisayarda yüklü olan boot edilebilen her şeyi görebileceğimiz bir menüdür. Bunu tekrar yüklemek oldukça basit bir işlem.
İşte kodlar:
~~~
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
~~~
Boot-repair uygulamasını açın ve Recommended repair'a tıklayın.\
Grub menüsü yüklendi. Ancak hala yeniden başlatmadan sonra Windows yükleniyor. Ubuntu'yu boot ayarlarından seçtiğinizde ise grub menüsünü görebilirsiniz. Bilgisayar en son yüklenen işletim sistemine öncelik veriyor.
Boot sıralamasını yapmak için [efibootmgr](https://linux.die.net/man/8/efibootmgr)'u yükleyelim.
~~~
sudo apt-get install efibootmgr
efibootmgr 
~~~
- Boot0000* ubuntu 
- Boot0001* Windows Boot Manager 

Böyle bir çıktınız olduğunu varsayarsak:
~~~
sudo efibootmgr -o 0000,0001
~~~
yazmanız yeterli olacaktır. 

Happy Dual-Booting!