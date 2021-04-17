Vagrant.configure("2") do |config|
  
  
  servers=[
	{
	:hostname => "LychUbuntu1",
	:box => "ubuntu/trusty64",
	:ip => "192.168.1.31",
	:ssh_port => '2201'
	},
		{
	:hostname => "LychUbuntu2",
	:box => "ubuntu/trusty64",
	:ip => "192.168.1.32",
	:ssh_port => '2202'
	}
  ]
  
  
  servers.each do |machine|
			config.vm.define machine[:hostname] do |node|
			node.vm.box = machine[:box]
			node.vm.hostname = machine[:hostname]
			node.vm.network :private_network, ip: machine[:ip]
			node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
			node.vm.synced_folder "C:/Users/Anton/Desktop/lab3", "/var/www"
			
			node.disksize.size = "10GB"
			
			node.vm.provision "shell", inline:  <<-SHELL
													sudo apt-get update
													sudo apt-get install git
													git init .
													git remote add -f origin https://raw.githubusercontent.com/tonymontanapaffpaff/osmu/blob/lab2/file.txt
													git checkout scrpit-lab3
													cat text.txt
													git remote
													git remote update myorigin --prune
													git pull
												SHELL
						
			node.vm.provision "shell", inline:  <<-SHELL 
													sudo apt-get update
													sudo apt-get install apt-transport-https ca-certificates
													sudo apt-key adv — keyserver hkp://p80.pool.sks-keyservers.net:80 — recv-keys 58118E89F3A912897C070ADBF76221572C52609D
													sudo cat /etc/apt/sources.list.d/docker.list<<EOF
													deb https://apt.dockerproject.org/repo ubuntu-xenial main
													EOF
													sudo apt-get purge lxc-docker
													sudo apt-cache policy docker-engine
													sudo apt-get install linux-image-extra-$(uname -rsu)
													sudo apt-get install docker.io
													sudo service docker start
													sudo docker run hello-world
													docker run hello-world	
													docker search ubuntu
												SHELL

			node.vm.provision "shell", inline: <<-SHELL
													docker pull ubuntu
													vagrant ssh vm1
													docker images
													sudo docker images -q
													docker run ubuntu
													docker run --name MyContainer -it ubuntu bash
													sudo docker start MyContainer
													sudo docker stop MyContainer sudo docker kill wonderful_kapitsa
													docker ps -all
													docker container ls -all
													sudo docker start ecc69fc8a431 
													sudo docker start d16c0969f195
													docker ps -a
													docker info
												SHELL
			
			node.vm.provision "shell", inline: <<-SHELL
													sudo dockerd --debug
													sudo systemctl stop docker
													sudo cp -au /var/lib/docker /var/lib/docker.bk
													echo '{ "storage-driver": "devicemapper" }' | sudo tee /etc/docker/daemon.json
													sudo systemctl start docker
													sudo systemctl status docker.service
													sudo systemctl stop docker
													sudo apt-get install -y thin-provisioning-tools
												SHELL

			node.vm.provision "shell", inline:  <<-SHELL
													sudo -s
													fdisk -l
													cat /proc/partitions
													fdisk /dev/sdb
													echo 'n, p, 1, 2048, +10G, w'
													mkfs.ext4 /dev/sdb1
													dd if=/dev/sdc of=/dev/sdd bs=64K conv=noerror,sync
													sudo -s
													sudo apt-get install mdadm
													sudo mdadm --examine /dev/sdb 
													sudo mdadm --examine /dev/sdb1 /dev/sdb2
													sudo mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdb2
													sudo mkfs.ext4 /dev/md0
													sudo mkdir /mnt/raid1
													sudo mount /dev/md0 /mnt/raid1
													df -h /mnt/raid1
												SHELL
			node.vm.provision "shell", inline:  <<-SHELL
													sudo visudo -f /etc/sudoers
													%sudo   ALL=(ALL:ALL)NOPASSWD:ALL
													sudo groupadd group
													sudo adduser -m vinid
													sudo usermod -G -a newgroup vinid
													sudo delgroup group
												SHELL
			
			node.vm.provision "shell", 
			inline: "
			",
			run: "always",
			privileged: "false"
			
			node.vm.disk :disk, size: "10GB", primary: true
			node.vm.provider :virtualbox do |vb|
				vb.customize ["modifyvm", :id, "--memory", 1024]
				vb.customize ["modifyvm", :id, "--cpus", 2]
				
			node.vm.provider :virtualbox do |vb|
				vb.gui = false
				vb.memory = 1024
				vb.cpus = 2
				
			end
				
		end
	
	end
	
end