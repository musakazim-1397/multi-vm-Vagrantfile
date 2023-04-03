Vagrant.configure("2") do |config|
  
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/bionic64"
	web.vm.network "private_network", ip:"192.168.40.11"
	web.vm.provider "virtualbox" do |vb|
		vb.memory = "1600"
		vb.cpus =2
	end
	web.vm.provision "shell", inline:<<-SHELL 
		apt update
		apt install -y apache2 wget unzip 
		systemctl start apache2
		systemctl enable apache2
		cd /tmp/
		wget https://www.tooplate.com/zip-templates/2133_moso_interior.zip
		unzip 2133_moso_interior.zip
		cp -r 2133_moso_interior/* /var/www/html/
		rm -rf 2133_moso_interior
		rm -rf 2133_moso_interior.zip
		systemctl restart apache2
	SHELL
  end

  config.vm.define "db" do |db|
    db.vm.box = "centos/7"
	db.vm.network "private_network", ip:"192.168.13.17"
	db.vm.provider "virtualbox" do |vb|
		vb.memory = "1600"
		vb.cpus =2
	end
	db.vm.provision "shell", inline:<<-SHELL
		yum install -y httpd wget unzip
		systemctl start httpd
		systemctl enable httpd
		cd /tmp/
		wget https://www.tooplate.com/zip-templates/2102_constructive.zip
		unzip 2102_constructive.zip
		cp -r 2102_constructive/* /var/www/html/
		rm -rf 2102_constructive
		rm -rf 2102_constructive.zip
		systemctl restart httpd
	SHELL
  end
end
