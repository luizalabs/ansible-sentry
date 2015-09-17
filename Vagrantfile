# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    # boxes at https://atlas.hashicorp.com/search.

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
    end

    config.vm.define "development_vm" do |development_vm|
        development_vm.vm.box = "ubuntu/trusty64"
        development_vm.vm.network "forwarded_port", guest: 80, host: 8000

        development_vm.vm.provision "ansible" do |ansible|
            ansible.playbook = "all.yml"
            ansible.groups = {
                "development" => ["development_vm"]
            }
        end
    end
end
