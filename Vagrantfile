Vagrant.configure("2") do |config|
  (1..3).each do |i|
    config.vm.define "ubuntu20-04-#{i}" do |node|
      node.vm.box = "ubuntu/focal64"
      node.vm.hostname = "ubuntu-20-04-#{i}"

      node.vm.network "private_network", ip: "192.168.56.10#{i}", mac: "00006c00010#{i}"

      node.vm.provider "virtualbox" do |vb|
        vb.name = "ubuntu_#{i}"
        vb.memory = "4096"
        vb.cpus = 2
        vb.gui = true
      end

      node.vm.provision "shell", inline: $common_provisioning
      node.vm.provision "shell", inline: $ubuntu_provisioning
    end
  end
end

$common_provisioning = <<-'SCRIPT'
  timedatectl set-timezone Asia/Tokyo
  sed -e s/^'PasswordAuthentication no'/'PasswordAuthentication yes'/ /etc/ssh/sshd_config > /tmp/sshd_config
  mv -f /tmp/sshd_config /etc/ssh/
  chmod 0600 /etc/ssh/sshd_config
  systemctl restart sshd.service
SCRIPT

$ubuntu_provisioning = <<-'SCRIPT'
  sudo apt update
  sudo apt upgrade -y
  reboot
SCRIPT

