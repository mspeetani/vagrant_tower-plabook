# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

# TOWER
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.network "forwarded_port", guest: 443, host: 8443
  config.vm.define :gen8tower do |server|
    server.vm.box = "rhel72"
    server.vm.hostname = "gen8tower.lab.org"
    server.vm.provider :libvirt do |domain|
      domain.uri = 'qemu+unix:///system'
      domain.driver = 'kvm'
      domain.storage_pool_name = "VMs"
      domain.driver = "kvm"
      domain.memory = 4096
      domain.cpus = 1
    end
  end

# Provisioning
  config.vm.provision "ansible" do |ansible|
    ansible.limit = "all" 
    ansible.playbook = "playbook.yml"
    ansible.ask_vault_pass = true     
  end
end
