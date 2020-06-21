# -*- mode: ruby -*-
# vi: set ft=ruby : 

Vagrant.configure("2") do |config|
  
  config.vm.define "nginx01" do |nginx|
    nginx.vm.box = "centos/8"
    nginx.vm.network  "private_network", ip: "192.168.50.100"
    nginx.vm.hostname = "nginx01"
    end



  config.vm.define "app-1" do |node|
      node.vm.box = "centos/8"
      node.vm.network "private_network", ip: "192.168.50.105"
      node.vm.hostname = "app-1"
  end


  config.vm.define "app-2" do |node|
      node.vm.box = "centos/8"
      node.vm.network "private_network", ip: "192.168.50.107"
      node.vm.hostname = "app-2"
  end

  config.vm.define "mysql01" do |mysql|
    mysql.vm.box = "centos/8"
    mysql.vm.network  "private_network", ip: "192.168.50.125"
    mysql.vm.hostname = "mysql01"
  end
    
  config.vm.provision :ansible do |ansible|
          ansible.playbook = "generate_inventory.yml"
          ansible.limit = "all"
          
          ansible.groups = {
             "cl_db" => ["mysql01"],
             "cl_nginx" => ["nginx01"],
             "cl_app" => ["app-1", "app-2"]
          }
          ansible.host_vars = {
            "mysql01" => {"vagrant_ip_address" => "192.168.50.125" },
            "app-1" => {"vagrant_ip_address" => "192.168.50.105" },
            "app-2" => {"vagrant_ip_address" => "192.168.50.107" }
            }


  end

end
