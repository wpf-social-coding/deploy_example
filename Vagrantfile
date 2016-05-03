INSTALL = <<-SCRIPT
apt-get install -y software-properties-common
apt-add-repository -y ppa:ansible/ansible
apt-get update
apt-get install -y ansible
ansible-playbook /home/vagrant/project/ansible/playbook.yml -e main_user=vagrant -c local -i /home/vagrant/project/ansible/inventory
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "yakshed/yoshida"

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder ".", "/home/vagrant/project", type: "nfs"

  config.vm.network "forwarded_port", guest: 3000, host: 3030

  config.ssh.forward_agent = true

  config.vm.provider "vmware_fusion" do |v|
    v.vmx["memsize"] = "4096"
    v.vmx["numvcpus"] = "2"
    v.vmx["tools.syncTime"] = "TRUE"
    v.vmx["tools.synchronize.restore"] = "TRUE"
  end

  config.vm.provider :virtualbox do |v|
    v.cpus = 2
    v.memory = 4096
  end

  config.vm.provision "shell", inline: INSTALL
end
