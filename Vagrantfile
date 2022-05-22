Vagrant.configure("2") do |config|
    config.vm.define "HOST1" do |debian|
      debian.vm.box = "debian/bullseye64"
      debian.vm.network "forwarded_port", guest: 80, host: 9998
      debian.vm.network "private_network", ip: "192.168.56.50"
      #debian.vm.provision "file", source: "index.html", destination: "~/"
      debian.vm.hostname = "Debian11"  
      debian.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "1024"
        vb.cpus = "1"
      #debian.vm.provision "shell", inline: <<-SHELL
       #sudo apt-get update && apt-get upgrade -yqq
       #sudo apt-get install vim git wget curl nginx -y
       #sudo systemctl start nginx
       #sudo systemctl enable nginx
       #sudo cp index.html /var/www/html/index.nginx-debian.html
       #sudo systemctl restart nginx
       #sudo rm -rf /var/lib/apt/lists/*  /tmp/*  /var/tmp/* /usr/share/man /usr/share/doc /usr/share/doc-base
       #sudo cat /dev/null > ~/.bash_history && history -c && exit
      #SHELL
      end
  end
   
  config.vm.define "HOST2" do |centos|
    centos.vm.box = "centos/8"
    centos.vm.network "forwarded_port", guest: 80, host: 9999
    centos.vm.network "private_network", ip: "192.168.56.51"
    #centos.vm.provision "file", source: "index.html", destination: "~/"
    centos.vm.hostname = "centos8"
    centos.vm.provision "file", source: "id_rsa.pub", destination: "~/"
    centos.vm.provision :shell, :inline => "cat ~/id_rsa.pub >> ~/.ssh/authorized_keys", run: "always"
    centos.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "1024"
      vb.cpus = "1"
    #centos.vm.provision "shell", inline: <<-SHELL
     #sudo cd /etc/yum.repos.d/
     #sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
     #sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
     #sudo yum update && yum upgrade -yqq
     #sudo yum install vim git wget curl nginx -y
     #sudo systemctl start nginx
     #sudo systemctl enable nginx
     #sudo cp index.html /usr/share/nginx/html
     #sudo systemctl restart nginx
     #sudo rm -rf /var/lib/apt/lists/*  /tmp/*  /var/tmp/* /usr/share/man /usr/share/doc /usr/share/doc-base
     #sudo cat /dev/null > ~/.bash_history && history -c && exit
    #SHELL
    end
   end

 config.vm.define "HOST3" do |deb|
      deb.vm.box = "ubuntu/bionic64"
      deb.vm.network "forwarded_port", guest: 80, host: 9997
      deb.vm.network "private_network", ip: "192.168.56.52"
      #deb.vm.provision "file", source: "index.html", destination: "~/"
      #deb.vm.provision "file", source: "id_rsa.pub", destination: "~/"
      #deb.vm.provision :shell, :inline => "cat ~/id_rsa.pub >> ~/.ssh/authorized_keys", run: "always"
      deb.vm.hostname = "ubuntubionic64"
      deb.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "1024"
        vb.cpus = "1"
    end
   end
end
