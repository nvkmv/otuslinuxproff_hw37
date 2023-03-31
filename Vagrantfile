Vagrant.configure("2") do |config|
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end  
  
  config.vm.define "router" do |router|
    router.vm.box = "nvkmv/rockylinux9"
    router.vm.host_name = "router"
    router.vm.network "private_network", ip: "192.168.56.10"
  end

  config.vm.define "server" do |server|
    server.vm.box = "nvkmv/rockylinux9"
    server.vm.host_name = "server"
    server.vm.network "private_network", ip: "192.168.56.11"
  end

  config.vm.synced_folder "./data/", "/home/vagrant/data"
end

