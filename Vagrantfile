Vagrant.configure("2") do |config|
	config.vm.box = "bento/ubuntu-20.04"
	config.vm.provision :shell, path: "bootstrap.sh"
	config.vm.network :forwarded_port, guest: 3000, host: 3001
	config.vm.network :forwarded_port, guest: 27017, host: 27018
end
