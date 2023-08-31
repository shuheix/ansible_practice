Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.network "private_network", type: "dhcp"
    
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
    end
  
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
    end
  end
  