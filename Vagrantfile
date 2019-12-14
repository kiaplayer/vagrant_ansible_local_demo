Vagrant.configure(2) do |config|
    box_name = "ansible_demo"
    box_ip   = "10.2.2.155"
    config.vm.define box_name do |box_config|
        box_config.vm.box = "ubuntu/bionic64"
        box_config.vm.network :private_network, ip: box_ip
        box_config.vm.provision "ansible_local" do |ansible|
            ansible.become = true
            ansible.playbook = "playbook.yml"
            ansible.galaxy_role_file = "requirements.yml"
            ansible.galaxy_roles_path = "/etc/ansible/roles"
            ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
            ansible.groups = {
              "default" => ["ansible_demo"],
            }
        end
    end
end