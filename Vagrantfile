  # https://docs.vagrantup.com.
  # You can search for boxes at https://vagrantcloud.com/search.
Vagrant.configure("2") do |config|
  config.vm.provider = "virtualbox" do vb
    vb.gui = false
  end  
  
  config.vm.network "forwarded_port", guest: 80, host: 8090, host_ip: "127.0.0.1"
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
end
