Vagrant.configure("2") do |config|
  
  config.vm.box = "ubuntu/focal64"

  config.vm.define "nginx" do |nginx|
    nginx.vm.provision "shell", path: "nginx.sh"
    nginx.vm.network "private_network", ip: "192.168.50.2"
    nginx.vm.network "forwarded_port", host: 4567, guest: 80
  end

  config.vm.define "sql" do |sql|
    sql.vm.provision "shell", path: "sql.sh"
    sql.vm.network "private_network", ip: "192.168.50.3"
  end

  config.vm.define "ghost" do |ghost|
    ghost.vm.provision "shell", path: "ghost.sh"
    ghost.vm.network "private_network", ip: "192.168.50.4"
  end
  config.vm.define "ghost2" do |ghost2|
    ghost2.vm.provision "shell", path: "ghost2.sh"
    ghost2.vm.network "private_network", ip: "192.168.50.5"
  end

  config.vm.provider "virtualbox" do |v|
    # v.name = "VM1"  
    # v.gui = true
    v.memory = 1024
    v.customize [ "modifyvm", :id, "--uartmode1", "file", File::NULL ]
  end
  
end
