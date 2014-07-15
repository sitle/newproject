# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define :chef do |c|
    # Personnalisation de la box (OS)
    c.vm.box = "centos6.5"

    # Personnalisation du hostname dans la VM
    c.vm.hostname = "chef.example.com"

    # Configuration réseau
    c.vm.network "private_network", ip: "192.168.10.2"

    # Configuration du provisionner CHEF
    c.vm.provision "chef_solo" do |chef|
      chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
      chef.roles_path = "roles"
      chef.data_bags_path = ["data_bags"]
      chef.encrypted_data_bag_secret_key_path = '.chef/encrypted_data_bag_secret'
      chef.custom_config_path = "Vagrantfile.chef"

      # Application des recipes/roles
      # chef.add_role("base-servers")
    end

    # Personnalisation du provider : virtualbox
    c.vm.provider "virtualbox" do |v|
      v.gui = false
      v.name = "chef"
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define :node1 do |c|
    # Personnalisation de la box (OS)
    c.vm.box = "centos6.5"

    # Personnalisation du hostname dans la VM
    c.vm.hostname = "node1.example.com"

    # Configuration réseau
    c.vm.network "private_network", ip: "192.168.10.11"

    # Configuration du provisionner CHEF
    c.vm.provision "chef_solo" do |chef|
      chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
      chef.roles_path = "roles"
      chef.data_bags_path = ["data_bags"]
      chef.encrypted_data_bag_secret_key_path = '.chef/encrypted_data_bag_secret'
      chef.custom_config_path = "Vagrantfile.chef"

      # Application des recipes/roles
      chef.add_role("bareos-server")
    end

    # Personnalisation du provider : virtualbox
    c.vm.provider "virtualbox" do |v|
      v.gui = false
      v.name = "node1"
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define :node2 do |c|
    # Personnalisation de la box (OS)
    c.vm.box = "centos6.5"

    # Personnalisation du hostname dans la VM
    c.vm.hostname = "node2.example.com"

    # Configuration réseau
    c.vm.network "private_network", ip: "192.168.10.12"

    # Configuration du provisionner CHEF
    c.vm.provision "chef_solo" do |chef|
      chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
      chef.roles_path = "roles"
      chef.data_bags_path = ["data_bags"]
      chef.encrypted_data_bag_secret_key_path = '.chef/encrypted_data_bag_secret'
      chef.custom_config_path = "Vagrantfile.chef"

      # Application des recipes/roles
      chef.add_role("bareos-client")
    end

    # Personnalisation du provider : virtualbox
    c.vm.provider "virtualbox" do |v|
      v.gui = false
      v.name = "node2"
      v.memory = 512
      v.cpus = 1
    end
  end
end
