Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.network "private_network", type: "dhcp"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "16384"
      vb.cpus = 4
      vb.gui = true
    end
    config.disksize.size = "200GB"

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
    end
  end
  