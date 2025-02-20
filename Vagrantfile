Vagrant.configure("2") do |config|

  config.vm.define "server" do |tomcate|

    tomcate.vm.box = "ubuntu/focal64"

    # Désactivation de la vérification automatique des mises à jour de la box
    tomcate.vm.box_check_update = false

    # Redirection du port 80 de la VM vers le port 8082 de l'hôte
    # Cela permet d'accéder aux services web de Tomcat via http://localhost:8082
    tomcate.vm.network "forwarded_port", guest: 80, host: 8082

    # Augmentation du temps d'attente du démarrage de la VM à 800 secondes
    tomcate.vm.boot_timeout = 800

    # Configuration d'un réseau privé avec une IP statique
    # L'hôte pourra accéder à la VM via cette IP : 192.168.0.13
    tomcate.vm.network "private_network", type: "static", ip: "192.168.0.13"

    # Synchronisation du dossier local "./tomcatwebapps" avec "/opt/tomcat/webapps" dans la VM
    # Cela permet de partager les applications web entre l'hôte et la VM
    tomcate.vm.synced_folder "./tomcatwebapps", "/opt/tomcat/webapps"

    # Configuration du fournisseur VirtualBox
    tomcate.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "tomcate-server"
      vb.memory = "1024"
      vb.cpus = 1 
    end
  end
end
