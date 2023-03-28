Vagrant.configure("2") do |config|
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end  
  
  config.vm.define "server" do |server|
    server.vm.box = "nvkmv/rockylinux9"
    server.vm.host_name = "server"
    server.vm.network "private_network", ip: "192.168.56.10"
  end

  config.vm.define "client" do |client|
    client.vm.box = "nvkmv/rockylinux9"
    client.vm.host_name = "client"
    client.vm.network "private_network", ip: "192.168.56.11"
  end

  config.vm.synced_folder "./data/", "/home/vagrant/data"
end

