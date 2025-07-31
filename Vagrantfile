Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"
  config.vm.network "forwarded_port", guest: 80, host: 7070, host_ip: "127.0.0.1"
  #config.vm.network "private_network", ip: "192.168.56.10", name: "vboxnet0"
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
  end
    config.vm.provision :ansible do |ansible|
        ansible.galaxy_role_file = "requirements.yml"
        ansible.playbook = "deploy.yml"

        # habilitar en caso de problemas
        # ansible.verbose = "vvv"

        ansible.raw_ssh_args = ["-o ForwardAgent=yes"]
        ansible.extra_vars = {
          ansible_user: "vagrant",
          #ansible_host: "192.168.56.10",
          ansible_python_interpreter: "/usr/bin/python3",
        }
    end
end

