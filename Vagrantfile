Vagrant.configure("2") do |config|
  #config.vm.box = "debian/bookworm64"
  #config.vm.box = "ubuntu/jammy64"
  config.vm.box = "ubuntu/focal64"
  #config.vm.network "forwarded_port", guest: 80, host: 9090, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.56.10", name: "vboxnet0"
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
  end
    config.vm.provision :ansible do |ansible|
        #ansible.galaxy_role_file = "ansible/requirements/roles.yml"
        ansible.playbook = "deploy.yml"
        ansible.verbose = "vvv"
        #ansible.inventory_path = "ansible/inventory.ini"  
        ansible.raw_ssh_args = ["-o ForwardAgent=yes"]
        ansible.extra_vars = {
          ansible_user: "vagrant",
          ansible_host: "192.168.56.100",
          ansible_python_interpreter: "/usr/bin/python3",
        }
    end
end

