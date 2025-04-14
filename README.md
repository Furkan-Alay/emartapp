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
* Bizler sıfırdan EC2 Instance oluşturduğumuz için Instance içerisine Docker engine ve Docker compose indirmemiz gerekiyor.Ayrıca "ubuntu" kullanıcısını "Docker" grubuna eklememiz gerekiyor.Bu işlemleri "User Data" kısmından yapabiliriz.Aşağıdaki kodu "User data" kısmına yapıştırın böylece bu komutlar boot işleminde çalışarak istediğimiz paketleri indirecektir. 
* #!/bin/bash
* Install docker on Ubuntu
* sudo apt-get update
   sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install docker-compose
   sudo apt-get update
   sudo apt-get install docker-ce docker-ce-cli containerd.io -y
   sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   sudo chmod +x /usr/local/bin/docker-compose

# Add ubuntu user into docker group
    sudo usermod -a -G docker ubuntu

