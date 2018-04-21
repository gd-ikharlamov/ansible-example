Vagrant.configure("2") do |config|
  
  VM_NAME = "rpm-deploy"

  config.vm.define VM_NAME do |config|
    config.vm.box = "centos/7"
    config.vm.network :forwarded_port, guest: 8080, host: 8080
    config.vm.network :private_network, ip: "192.168.88.2"

    config.vm.provider "virtualbox" do |vbox|
      vbox.name = VM_NAME
      vbox.linked_clone = true
      vbox.memory = 2048
      vbox.cpus = 2
    end

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/deploy.yml"
      ansible.config_file = "ansible/ansible.cfg"
    end

  end

end
