# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	config.vm.define "base" do |base|
		base.vm.box = "base"
		base.vm.synced_folder "/sync", "/sync", create: true, type: "nfs"
		base.vm.network "private_network", ip: "192.168.200.2"
		base.vm.network "forwarded_port", guest: 80, host: 8080
		base.vm.network "forwarded_port", guest: 443, host: 8443
		base.vm.provider :virtualbox do |vb|
			vb.name = "base"
		end
		base.vm.provision :shell, :path => "config/setup.sh"
	end

	config.vm.define "laravel" do |laravel|
		laravel.vm.box = "laravel"
		laravel.vm.synced_folder "/sync", "/sync", create: true, type: "nfs"
		laravel.vm.network "private_network", ip: "192.168.200.2"
		laravel.vm.network "forwarded_port", guest: 80, host: 8080
		laravel.vm.network "forwarded_port", guest: 443, host: 8443
		laravel.vm.provider :virtualbox do |vb|
			vb.name = "laravel"
		end
		laravel.vm.provision :shell, :path => "config/laravel.sh"
	end

end
