# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "base"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  config.vm.network :hostonly, "33.33.33.11"
  config.vm.forward_port 8000, 8000
  config.vm.forward_port 22, 2222

  # config.vm.network :bridged

  config.vm.share_folder("hackallthings", "/vagrant", ".", :nfs => true)

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "vagrant-main"
    chef.add_recipe "ubuntu"
    chef.add_recipe "build-essential"
    chef.add_recipe "chef-redis::source"
    chef.add_recipe "openssl"
    chef.add_recipe "git"
    chef.add_recipe "postgresql::server"
    chef.add_recipe "postgresql::client"
  end
end
