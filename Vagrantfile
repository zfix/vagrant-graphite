# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
   config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
   config.vm.network "forwarded_port", guest: 88, host: 8088
  #
   config.vm.provider "virtualbox" do |vb|
     vb.name = "ZakazVM"
     vb.gui = false
     vb.cpus = 1
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "512"
   end
   config.vm.define "zakazbox" do |zakazbox|
   end
  #
	config.vm.provision "shell", inline: "apt-get install -y ansible" 
	config.vm.provision "ansible", run: "always" do |ansible|
		ansible.verbose = "v"
#		ansible.inventory_path = "./inventory"
		ansible.extra_vars = {
		graphite_admin: "myadmin",
		graphite_pass: "myadmin@example.com",
		graphite_email: "mypass"
		}
		ansible.playbook = "ansiblevagrant.yml"
	end
end
