Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  config.vm.define "master" do |masterconfig|
    masterconfig.vm.box = "ubuntu/bionic64"
    masterconfig.vm.hostname = "master"
    masterconfig.vm.network :private_network, ip: "192.168.53.21"
  end

  config.vm.define "replica" do |replicaconfig|
    replicaconfig.vm.box = "ubuntu/bionic64"
    replicaconfig.vm.hostname = "replica"
    replicaconfig.vm.network :private_network, ip: "192.168.53.22"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3"
    }
  end

end
