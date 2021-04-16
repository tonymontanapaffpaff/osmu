Vagrant.configure("2") do |config|
  
  
  servers=[
	{
	:hostname => "m1",
	:box => "ubuntu/trusty64",
	:ip => "192.168.10.21",
	:ssh_port => '2221'
	},
	{
	:hostname => "m2",
	:box => "ubuntu/trusty64",
	:ip => 192.168.10.22",
	:ssh_port => '2222'
	},
	{
	:hostname => "m3",
	:box => "ubuntu/trusty64",
	:ip => 192.168.10.23",
	:ssh_port => '2223'
	}
  ]
  
  
  servers.each do |machine|
		config.vm.define machine[:hostname] do |node|
			node.vm.box = machine[:box]
			node.vm.hostname = machine[:hostname]
			node.vm.network :private_network, ip: machine[:ip]
			node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
			node.vm.synced_folder "d:/osmu", "/var/www"

			
			#SSH
			#ssh-keygen -b 4096
			#ssh-copy-id anton@192.168.10.22
			#ssh anton@192.168.10.22
			#sudo nano /etc/ssh/sshd_config
			#sudo systemctl restart ssh
			
			#chmod 777 file.txt
			#scp root@192.168.1.21:dirlist.txt 
			#tar -cf filename.tar file file1 fileN
			
			#mkdir current new old 
			#tar cf myarch.tar current new old 

			
			node.vm.provision "shell", 
				
			inline: '
			
			',
			run: "always",
			privileged: "false"

				
			node.vm.provider :virtualbox do |vb|
				vb.gui = false
				vb.memory = 1024
				vb.cpus = 2
				
			end
				
		end
	
	end
	
end