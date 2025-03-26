Vagrant.configure("2") do |config|
    # Especificar la imagen base de Ubuntu
    config.vm.box = "ubuntu/jammy64"
  
    # Asignar IP estática
    config.vm.network "private_network", ip: "192.168.56.10"
  
    # Configurar CPU y RAM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Compartir carpeta local con Apache
    config.vm.synced_folder "./web_pages", "/var/www/html", owner: "www-data", group: "www-data", mount_options: ["dmode=775,fmode=664"]
  
    # Instalar Apache automáticamente
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl restart apache2
    SHELL
  end