  # https://docs.vagrantup.com.
  # You can search for boxes at https://vagrantcloud.com/search.
Vagrant.configure("2") do |config|
  config.vm.provider = "virtualbox" do vb
    vb.gui = false
  end  
  
  #config.vm.network "forwarded_port", guest: 80, host: 8090, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"

  # config.vm.synced_folder "../data", "/vagrant_data"

  # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

  # Debian Server
  config.vm.define "debian" do |debian|
    debian.vm.box = "debian/bullseye64"
    debian.vm.hostname = "Debian-VM"
    debian.vm.network "private_network", type: "dhcp"
    debian.vm.provider "virtualbox" do |vb|
    vb.name = "Debian-VM-Lab"
    vb.memory = "1024"
    vb.cpus = 2
    end
  end

  # AlmaLinux Server
  config.vm.define "almalinux" do |almalinux|
    almalinux.vm.box = "almalinux/8"
    almalinux.vm.hostname = "AlmaLinux-VM"
    almalinux.vm.network "private_network", type: "dhcp"
    almalinux.vm.provider "virtualbox" do |vb|
    vb.name = "AlmaLinux-VM-Lab"
    vb.memory = "1024"
    vb.cpus = 2
    end
  end

  # Windows Server
  config.vm.define "windows" do |windows|
    windows.vm.box = "mcree/win2019"
    windows.vm.hostname = "Windows-VM"
    windows.vm.network "private_network", type: "dhcp"
    windows.vm.provider "virtualbox" do |vb|
    vb.name = "Windows-VM-Lab"
    vb.memory = "2048"
    vb.cpus = 2
    end
  end
end