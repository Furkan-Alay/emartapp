# emart-app Projeme hoşgeldiniz bu projem micro-servis yapısına sahip bir e-ticaret sitesini konteynerleştirmeden oluşmaktadır.
## Proje için gerekli olan docker ve container kodlarını kendim yazmış bulunmaktayım.
## E-Ticaret sitenizi kodlarımda gerekli düzenlemeler yaparak konteynerleştirebilirsiniz.
### Projenin çalışması için vereceğim basit talimatları takip etmelisiniz.
* Buradaki kaynak kodumuzu açtık.
* Kaynak kodun "https" linkini kopyaladık.
* Gitbash terminali yüklü değilse kuralım ve açalım.Buradaki kodları Terminale yazalım
* mkdir -p /f/microsvc (C klasörü varsa ona göre kodları yazın).
* cd /f/microsvc
* git clone https://github.com/Furkan-Alay/emartapp.git
* Şimdi ise kaynak kodumuzun ssh linkini kopyaladık.
* git clone git@github.com:Furkan-Alay/emartapp.git
* ls
* cd emartapp/
* Vscode kurmadıysanız indirin.
* code . (Bu komutla beraber Kaynak kodumuzu VSCode ile açmış olacağız)
* AWS Hesabınız yoksa oluşturmalısınız.AWS kısmından Sanal makine oluşturmak istemiyorsanız ve yerel makinede çalıştırmak istiyorsanız Yerel makinenize docker engine ve docker kurulumunu yapmış olmanız gerekiyor.
### Bizler build işlemi hızlı olması için AWS'te bir EC2 Instance oluşturacağız.
* AWS Hesabımızı açmamız gerekiyor.
* Launch instance bastık ve EC2 Instance için isim verdik.
* Ubuntu AMI seçtik.
* Instance type için "t3.medium" seçmemiz lazım çünkü docker engine kurmak ve build,run işlemi için yeterli depolama alanına sahip olmamız gerekiyor.
* Key-pair oluşturduk.("RSA",".pem" türünü seçmemiz gerekiyor.)
* Network Settingsk kısmında "MY IP" seçeneğini seçtik."Allow HTTP traffic from the internet" seçtik.
* 20GB Root Volume seçtik.
* 
* 
