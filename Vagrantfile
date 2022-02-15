# -*- mode: ruby -*-
# vi: set ft=ruby :
# vi: set tabstop=2 :
# vi: set shiftwidth=2 :

Vagrant.configure("2") do |config|

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = false
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = false

  vms_debian = [
    { :name => "teleport-server-debian-bullseye", :box => "debian/bullseye64", :ip => "192.168.78.22", :vars => {}, group: 'servers' },
    { :name => "teleport-node-debian-bullseye",   :box => "debian/bullseye64", :ip => "192.168.78.24", :vars => {}, group: 'nodes' },
  ]

# conts = [
#   { :name => "docker-debian-buster", :docker => "hanxhx/vagrant-ansible:debian10", :vars => {} },
#   { :name => "docker-debian-bullseye", :docker => "hanxhx/vagrant-ansible:debian11", :vars => {} },
# ]

# config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true

# conts.each do |opts|
#   config.vm.define opts[:name] do |m|
#     m.vm.provider "docker" do |d|
#       d.image = opts[:docker]
#       d.remains_running = true
#       d.has_ssh = true
#     end

#     m.vm.provision "ansible" do |ansible|
#       ansible.playbook = "tests/test.yml"
#       ansible.verbose = 'vv'
#       ansible.become = true
#       ansible.extra_vars = opts[:vars].merge({ is_docker: true })
#     end
#   end
# end

  vms_debian.each do |opts,index|
    config.vm.define opts[:name] do |m|
      m.vm.box = opts[:box]
#      m.vm.hostname = opts[:name] + ".vagrant"
      m.vm.hostname = opts[:name]
      m.vm.network "private_network", ip: opts[:ip]
      m.vm.provider "virtualbox" do |v|
        v.cpus = 1
        v.memory = 512
      end

      m.vm.provision "ansible" do |ansible|
        ansible.playbook = "tests/test.yml"
        ansible.verbose = 'vv'
        ansible.become = true
        #ansible.extra_vars = opts[:vars].merge({teleport_default_public_addr: opts[:ip]})
        ansible.extra_vars = opts[:vars].merge({})
        ansible.groups = { opts[:group] => opts[:name] }
      end
    end
  end

end
