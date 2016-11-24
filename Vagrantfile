# -*- mode: ruby -*-

# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest:3306, host:3307

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.55.10"
#   config.vm.network "private_network", ip: "33.33.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "/Users/denisnascimento/Sites", "/var/www/html/sites", owner: "www-data", group: "www-data", :mount_options => ["dmode=777", "fmode=777"]

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
#   config.vm.provider "virtualbox" do |vb|
#     # Display the VirtualBox GUI when booting the machine
#     vb.gui = true
#   
#     # Customize the amount of memory on the VM:
#     vb.memory = "1024"
#   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo apt-get install -y php5 libapache2-mod-php5 php5-mcrypt
    sudo apt-get install -y php5-gd
    sudo apt-get install -y mcrypt php5-mcrypt
    sudo apt-get install -y php5-cli
    sudo apt-get install -y libapache2-mod-auth-mysql php5-mysql
    sudo apt-get install -y curl git
    curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
    sudo php5enmod mcrypt
    sudo a2enmod rewrite
    sudo service apache2 restart


#     Executar na mão
#     sudo apt-get install -y mysql-server mysql-client
#     sudo mysql_secure_installation
#     sudo mysql_install_db
#     sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mysql/my.cnf
#     mysql -u root -p -e "use mysql; GRANT ALL ON . to root@'33.33.33.10' IDENTIFIED BY 'root'; FLUSH PRIVILEGES;"
#     sudo service mysql restart

  SHELL

end