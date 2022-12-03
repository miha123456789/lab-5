Vagrant.configure("2") do |config|
  config.vm.define "mm5" do |mm5|
    mm5.vm.hostname = "mm5"
    mm5.vm.box = "centos/7"
    mm5.vm.network "private_network", ip: "192.168.33.10"
    mm5.vm.network "forwarded_port", guest: 80, host: 8888


    mm5.vm.provider "virtualbox" do |vb|
      vb.name = "mm5"
      vb.gui = false
      vb.memory = "1024"
    end
    
    mm5.vm.provision "shell", run: "always",  inline: <<-SHELL
        echo "Hello from the Centos VM"
	mkdir /etc/folder1
        mkdir /etc/folder2
        cat /vagrant/mv.service > /etc/systemd/system/mv.service
        systemctl daemon-reload
        systemctl start mv.service
        systemctl enable mv.service
        
    SHELL
  end
  
  
end
