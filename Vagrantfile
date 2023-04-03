Vagrant.configure("2") do |config|
  
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/bionic64"
	web.vm.network "private_network", ip:"192.168.40.11"
	web.vm.provider "virtualbox" do |vb|
		vb.memory = "1600"
		vb.cpus =2
	end
	web.vm.provision "shell", inline:<<-SHELL 
	
	SHELL
  end

  config.vm.define "db" do |db|
    db.vm.box = "mysql"
  end
end
