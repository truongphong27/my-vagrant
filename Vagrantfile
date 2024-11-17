Vagrant.configure("2") do |config|
  # Máy ảo Windows Server 2016
  config.vm.define "win2016" do |win|
    win.vm.box = "mwrock/Windows2016"
    win.vm.network "public_network"  # Sử dụng mạng Bridge (Public Network)
    win.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = 2
    end
    # Cài đặt IIS trên Windows Server 2016
    win.vm.provision "shell", inline: <<-SHELL
      Write-Output "Cài đặt IIS trên Windows Server 2016"
      Install-WindowsFeature -Name Web-Server -IncludeManagementTools
    SHELL
  end

  # Máy ảo Ubuntu Server
  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/bionic64" # Ubuntu 18.04 LTS
    ubuntu.vm.network "public_network"  # Sử dụng mạng Bridge (Public Network)
    ubuntu.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      echo "Cài đặt nginx trên Ubuntu"
      sudo apt-get update -y
      sudo apt-get install -y nginx
      sudo systemctl enable nginx
      sudo systemctl start nginx
    SHELL
  end

  # Máy ảo CentOS
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
    centos.vm.network "public_network"  # Sử dụng mạng Bridge (Public Network)
    centos.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    centos.vm.provision "shell", inline: <<-SHELL
      echo "Cài đặt nginx trên CentOS"
      sudo yum update -y
      sudo yum install -y nginx
      sudo systemctl enable nginx
      sudo systemctl start nginx
    SHELL
  end
end
