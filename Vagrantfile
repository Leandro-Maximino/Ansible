$install_ansible = <<-SCRIPT
  apt-get update && apt-get install -y ansible
SCRIPT

Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.provider "virtualbox" do |vb| 
    vb.memory = 1024     
    vb.cpus = 1
  end

  config.vm.define "ansible" do |ansible|
    # Network
    ansible.vm.network "public_network", ip: "192.168.0.20"

    # Provider
    ansible.vm.provider "virtualbox" do |vb|

      vb.memory = 2048
      vb.name = "ubuntu_curso_ansible"
    end

    # Provision
    # ansible.vm.provision "shell", inline: "cat /Configs/id_ansible.pub >> .ssh/authorized_keys"
    ansible.vm.provision "shell", inline: $install_ansible

    # Shared Folder
    # ansible.vm.synced_folder "./Configs" "/Configs"    

  end

  config.vm.define "wordpress" do |wordpress|
    # Network
    wordpress.vm.network "public_network", ip: "192.168.0.21"

    # Provider
    wordpress.vm.provider "virtualbox" do |vb|
      vb.name = "ubuntu_curso_ansible_wordpress"
    end

  end
end
