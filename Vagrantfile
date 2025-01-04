# https://docs.vagrantup.com.
# You can search for boxes at https://vagrantcloud.com/search.

Vagrant.configure("2") do |config|
  
  # Configuração do provedor VirtualBox (para todas as VMs)
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false # Desabilita a interface gráfica das VMs
  end

  # Definição da VM Debian
  config.vm.define "debian" do |debian|
    debian.vm.box = "debian/bullseye64"
    debian.vm.hostname = "Debian-VM"
    debian.vm.network "private_network", type: "static", ip:"192.168.11.11"
    
    debian.vm.provider "virtualbox" do |vb|
      vb.name = "Debian-VM-Lab"
      vb.memory = "1024"
      vb.cpus = 2
    end
  end

  # Definição da VM AlmaLinux
  config.vm.define "almalinux" do |almalinux|
    almalinux.vm.box = "almalinux/8"
    almalinux.vm.hostname = "AlmaLinux-VM"
    almalinux.vm.network "private_network", type: "static", ip:"192.168.10.10"
    
    almalinux.vm.provider "virtualbox" do |vb|
      vb.name = "AlmaLinux-VM-Lab"
      vb.memory = "1024"
      vb.cpus = 2
    end
  end

  # Definição da VM Windows Server
  config.vm.define "windows" do |windows|
    windows.vm.box = "mcree/win2019"
    windows.vm.hostname = "Windows-VM"
    windows.vm.network "private_network", type: "static", ip:"192.168.12.12"
    
    windows.vm.provider "virtualbox" do |vb|
      vb.name = "Windows-VM-Lab"
      vb.memory = "2048"
      vb.cpus = 2
    end
  end
  
  # Configuração de sincronização de pastas
  config.vm.synced_folder "/home/vagrant/ansible_project/playbooks", "/vagrant", type: "virtualbox"
  config.vm.synced_folder "C:/github-repos/devops/ansible", "/home/vagrant/ansible_project/playbooks"
end
