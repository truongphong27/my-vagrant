# Vagrantfile: Cấu hình 2 máy ảo với Ubuntu và CentOS
Vagrant.configure("2") do |config|

  # Máy ảo Ubuntu
  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/focal64" # Hộp Ubuntu 20.04
    ubuntu.vm.hostname = "ubuntu"
    ubuntu.vm.network "private_network", ip: "192.168.33.11" # Địa chỉ IP tĩnh
    ubuntu.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
    SHELL
  end

# Máy ảo CentOS
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
    centos.vm.hostname = "centos"
    centos.vm.network "private_network", ip: "192.168.33.12"
    centos.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
  end

# Máy ảo Windows Server 2016
  config.vm.define "win2016" do |win|
    win.vm.box = "mwrock/Windows2016"
    win.vm.network "private_network", ip: "192.168.56.104"
    win.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = 2
    end
    win.vm.boot_timeout = 600
    win.vm.provision "shell", inline: <<-SHELL
      Write-Output "Cấu hình Windows Server 2016"
    SHELL
  end
 end
