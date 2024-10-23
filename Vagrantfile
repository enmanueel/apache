# Vagrantfile para crear una máquina virtual con Apache
Vagrant.configure("2") do |config|
  # Aumentar el tiempo de espera para el arranque
  config.vm.boot_timeout = 900

  # Especificar la imagen base de Ubuntu
  config.vm.box = "ubuntu/bionic64"

  # Configurar los recursos de la máquina virtual
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"      # Asignar 700MB de RAM
    vb.cpus = 2            # Asignar 2 CPUs
  end

  # Configurar la carpeta compartida, desactivando la creación de symlinks
  config.vm.synced_folder "./", "/var/www/html", SharedFoldersEnableSymlinksCreate: false

  # Configurar la red con una IP estática para evitar conflictos de DHCP
  config.vm.network "private_network", ip: "192.168.56.10"

  # Configurar el script de provisión para instalar Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo ufw allow 'Apache Full'
  SHELL

  # Asignar un nombre a la máquina virtual
  config.vm.hostname = "apache-server"
end
