# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "frontend" do |frontend|
    frontend.vm.box = "debian/jessie64"
    frontend.vm.hostname = "frontend"
    frontend.vm.network "private_network", ip: "10.0.0.10"
    frontend.vm.network "forwarded_port", guest: 80, host: 8080
  end

N = 2
(1..N).each do |machine_id|
  config.vm.define "backend#{machine_id}" do |machine|
    machine.vm.box = "debian/jessie64"
    machine.vm.hostname = "backend#{machine_id}"
    machine.vm.network "private_network", ip: "10.0.0.#{10+machine_id}"
    if machine_id == N
      machine.vm.provision :ansible do |ansible|
        ansible.limit = "all"
        ansible.playbook = "playbook.yml"
        ansible.verbose = "vvv"
      end
    end
  end
end
end
