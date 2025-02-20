
Vagrant.configure("2") do |config|
  config.vm.define "server" do |tomcate|

    tomcate.vm.box = "ubuntu/focal64"

    tomcate.vm.box_check_update = false

    tomcate.vm.network "forwarded_port", guest: 80, host: 8082

    tomcate.vm.boot_timeout = 800

     # Réseau privé avec IP statique
    tomcate.vm.network "private_network", type: "static", ip: "192.168.0.13"

    tomcate.vm.synced_folder "./tomcatwebapps", "/opt/tomcat/webapps"

    tomcate.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "tomcate-server"
      vb.memory = "1024"
      vb.cpus = 1
    end
  end
end