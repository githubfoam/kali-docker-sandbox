# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

#WORKING NOT OK
#interactive confirm!!!!
$kali_docker_script = <<SCRIPT
# https://www.kali.org/docs/containers/installing-docker-on-kali/

#Uninstall old versions
apt-get remove docker docker-engine docker.io containerd runc -qy
apt-get update -qy

#Install kali linux docker package
#interactive confirm!!!!
apt-get install docker.io -qy

# Client: Docker Engine - Community
# Server: Docker Engine - Community
docker version

docker --version

# https://docs.docker.com/install/linux/linux-postinstall/
# Manage Docker as a non-root user
# add user to the docker group
  usermod -aG docker $USER

docker run hello-world

#Uninstall Docker Engine
# apt-get purge docker-ce docker-ce-cli containerd.io -yq
# Images, containers, volumes, or customized configuration files on your host are not automatically removed
# delete all images, containers, and volumes
# rm -rf /var/lib/docker
# rm -rf /var/lib/containerd

  
docker --version
# # Manage Docker as a non-root user
# # https://docs.docker.com/install/linux/linux-postinstall/
# sudo groupadd docker && sudo usermod -aG docker vagrant # add user to the docker group
# sudo systemctl enable docker
# docker --version
SCRIPT

#WORKING OK
$kali_dockerce_debian_bullseye_script = <<SCRIPT
# Kali Linux is based on Debian, use Debian’s current stable version 
# (even though Kali Linux is a rolling distribution). 
# At the time of writing, its “buster”:
# https://www.kali.org/docs/containers/installing-docker-on-kali/
# https://docs.docker.com/engine/install/debian/
# https://www.debian.org/releases/stable/

#Uninstall old versions
apt-get remove docker docker-engine docker.io containerd runc -qy
apt-get update -qy

# Docker repository debian buster
printf "%s\n" "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-ce-archive-keyring.gpg] https://download.docker.com/linux/debian bullseye stable" \
  | sudo tee /etc/apt/sources.list.d/docker-ce.list



#Import the gpg key
curl -fsSL https://download.docker.com/linux/debian/gpg \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/docker-ce-archive-keyring.gpg

apt-get update -qy
#List the versions available in your repo
apt-cache madison docker-ce

# Install the latest version of docker-ce
apt-get install docker-ce docker-ce-cli containerd.io -yq

# Client: Docker Engine - Community
# Server: Docker Engine - Community
docker version

docker --version

# https://docs.docker.com/install/linux/linux-postinstall/
# Manage Docker as a non-root user
# add user to the docker group
#usermod -aG docker $USER # script run as root
usermod -aG docker vagrant

docker run hello-world

#Uninstall Docker Engine
# apt-get purge docker-ce docker-ce-cli containerd.io -yq
# Images, containers, volumes, or customized configuration files on your host are not automatically removed
# delete all images, containers, and volumes
# rm -rf /var/lib/docker
# rm -rf /var/lib/containerd

#install docker-compose
# https://docs.docker.com/compose/install/
curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose version
SCRIPT

#WORKING OK
$kali_dockerce_debian_buster_script = <<SCRIPT
# Kali Linux is based on Debian, use Debian’s current stable version 
# (even though Kali Linux is a rolling distribution). 
# At the time of writing, its “buster”:
# https://www.kali.org/docs/containers/installing-docker-on-kali/
# https://docs.docker.com/engine/install/debian/
# https://www.debian.org/releases/stable/

#Uninstall old versions
apt-get remove docker docker-engine docker.io containerd runc -qy
apt-get update -qy

# Docker repository debian buster
printf "%s\n" "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-ce-archive-keyring.gpg] https://download.docker.com/linux/debian buster stable" \
  | sudo tee /etc/apt/sources.list.d/docker-ce.list



#Import the gpg key
curl -fsSL https://download.docker.com/linux/debian/gpg \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/docker-ce-archive-keyring.gpg

apt-get update -qy
# List the versions available in your repo
apt-cache madison docker-ce

# Install the latest version of docker-ce
apt-get install docker-ce docker-ce-cli containerd.io -yq



# Client: Docker Engine - Community
# Server: Docker Engine - Community
docker version

docker --version

# https://docs.docker.com/install/linux/linux-postinstall/
# Manage Docker as a non-root user
# add user to the docker group
usermod -aG docker $USER

docker run hello-world

#install docker-compose
# https://docs.docker.com/compose/install/
curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose version

#Uninstall Docker Engine
# apt-get purge docker-ce docker-ce-cli containerd.io -yq
# Images, containers, volumes, or customized configuration files on your host are not automatically removed
# delete all images, containers, and volumes
# rm -rf /var/lib/docker
# rm -rf /var/lib/containerd
SCRIPT

#WORKING OK
$centos_docker_script = <<-SCRIPT

# Uninstall old versions
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

# # Set up the repository
yum install -y yum-utils
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo


# # Install Docker Engine
yum update -y
yum install \
    docker-ce \
    docker-ce-cli \
    containerd.io -y


systemctl start docker
systemctl is-active docker
# Configure Docker to start on boot
systemctl enable docker.service
systemctl enable containerd.service

docker --version
#both Client: Docker Engine and Server: Docker Engine
docker version 

# Verify that you can run docker commands without sudo
docker run hello-world
# su -c  'docker run hello-world' vagrant #run by vagrant user

# Post-installation steps for Linux
# Manage Docker as a non-root user

# Create the docker group
#groupadd: group 'docker' already exists
#groupadd docker

# Add your user to the docker group
# usermod -aG docker $USER # by default run by root
# id $USER
usermod -aG docker vagrant
# sudo lid -g docker # list members of group docker
grep "docker" /etc/group

# Log out and log back in so that your group membership is re-evaluated
# If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect

# newgrp docker #activate the changes to groups
# su -c  'newgrp docker' vagrant 



SCRIPT

#WORKING
$ubuntu_docker_script = <<SCRIPT
# Get Docker Engine - Community for Ubuntu
# https://docs.docker.com/engine/install/ubuntu/
echo "#######################################"
echo "#######################################"
whoami
echo "#######################################"
echo "#######################################"

#Uninstall old versions
sudo apt-get remove docker docker-engine docker.io containerd runc -y
sudo apt-get update -y

#Set up the repository
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release -y

#Add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

#corporate network SSL certificate problem
# curl -kfsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

#set up the stable repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#corporate network SSL certificate problem
# echo \
#   "deb [trusted=yes] https://download.docker.com/linux/ubuntu \
#   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
#corporate network SSL certificate problem
# sudo add-apt-repository "deb [trusted=yes] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

#Install Docker Engine
sudo apt-get update -y
sudo apt-get install \
    docker-ce \
    docker-ce-cli \
    containerd.io -y
   
systemctl start docker
systemctl is-active docker
# Configure Docker to start on boot
systemctl enable docker.service
systemctl enable containerd.service

docker --version
#both Client: Docker Engine and Server: Docker Engine
sudo docker version 

# Verify that you can run docker commands without sudo
docker run hello-world
# su -c  'docker run hello-world' vagrant #run by vagrant user

# Post-installation steps for Linux
# Manage Docker as a non-root user

# Create the docker group
groupadd docker
# Add your user to the docker group
# usermod -aG docker $USER # by default run by root
sudo usermod -aG docker vagrant
# sudo: lid: command not found
# sudo lid -g docker # list members of group docker
grep "docker" /etc/group

# Log out and log back in so that your group membership is re-evaluated
# If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect

# newgrp docker #activate the changes to groups
# su -c  'newgrp docker' vagrant 


SCRIPT

# WORKING
$dockerce_debian_bullseye_script = <<SCRIPT
# https://docs.docker.com/engine/install/debian/

echo "verify user...: $(whoami)"

# #Uninstall old versions
# apt-get remove docker docker-engine docker.io containerd runc -qy

# apt-get update -qy
# apt-get install \
#     ca-certificates \
#     curl \
#     gnupg \
#     lsb-release -yq

# #Import the gpg key
# curl -fsSL https://download.docker.com/linux/debian/gpg | \
#   gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# echo \
#   "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
#   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# apt-get update -qy
# #List the versions available in your repo
# apt-cache madison docker-ce

# # Install the latest version of docker-ce
# apt-get install docker-ce docker-ce-cli containerd.io -yq

# # Client: Docker Engine - Community
# # Server: Docker Engine - Community
# docker version

# docker --version

# # https://docs.docker.com/install/linux/linux-postinstall/
# # Manage Docker as a non-root user
# # add user to the docker group
# echo $USER
# usermod -aG docker $USER

# docker run hello-world



# #install docker-compose
# # https://docs.docker.com/compose/install/
# curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
# chmod +x /usr/local/bin/docker-compose
# docker-compose version

# # #Uninstall Docker Engine
# # # apt-get purge docker-ce docker-ce-cli containerd.io -yq
# # # Images, containers, volumes, or customized configuration files on your host are not automatically removed
# # # delete all images, containers, and volumes
# # # rm -rf /var/lib/docker
# # # rm -rf /var/lib/containerd

SCRIPT


Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = false
    vb.memory = "1024"
    vb.cpus = 2
    # vb.customize ["modifyvm", :id, "--groups", "/kali-sandbox"] # create vbox group
  end


  #bridged network, DHCP enabled auto IP assignment
  # Username: vagrant; Password: vagrant. 
  config.vm.define "vg-kali-02" do |kalicluster|
    kalicluster.vm.box = "kalilinux/rolling"
    kalicluster.vm.hostname = "vg-kali-02"
    kalicluster.vm.network "public_network"
    kalicluster.vm.boot_timeout = 31999 # 30 minutes
    # kalicluster.vm.network "forwarded_port", guest: 22, host: 2203
    # kalicluster.vm.network "forwarded_port", guest: 22, host: 2215
    # config.vm.network :forwarded_port, guest: 22, host: 2201, id: "ssh", auto_correct: true
    #Disabling the default /vagrant share can be done as follows:
    # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
    kalicluster.vm.provider "virtualbox" do |vb|
        vb.name = "vbox-kali-02"
        vb.memory = "1024"
        vb.gui = true
    end
    kalicluster.vm.provision "shell", inline: $kali_dockerce_debian_buster_script #OK
    # kalicluster.vm.provision "shell", inline: $kali_dockerce_debian_bullseye_script  #OK
    kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
  end 

    #bridged network, DHCP disabled,manual IP assignment
    config.vm.define "vg-kali-03" do |kalicluster|
      kalicluster.vm.box = "kalilinux/rolling"
      kalicluster.vm.hostname = "vg-kali-03"
      # kalicluster.vm.network "public_network", ip: "192.168.40.1"
      kalicluster.vm.network "public_network" 
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-kali-03"
          vb.memory = "1024"
          # vb.gui = true 
      end
      # kalicluster.vm.provision "shell", inline: $kali_dockerce_debian_buster_script #OK
      # kalicluster.vm.provision "shell", inline: $kali_dockerce_debian_bullseye_script  #OK
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end 



  #### private network

    config.vm.define "vg-kali-04" do |kalicluster|
      kalicluster.vm.box = "kalilinux/rolling"
      kalicluster.vm.hostname = "vg-kali-04"
      kalicluster.vm.network "private_network", ip: "192.168.50.5"
      kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-kali-04"
          vb.memory = "1024"
          vb.gui = true
      end
      kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-04"
      kalicluster.vm.provision "shell", inline: $kalisandbox_script
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
      
    end 
  
    config.vm.define "vg-kali-05" do |kalicluster|
      kalicluster.vm.box = "kalilinux/rolling"
      kalicluster.vm.hostname = "vg-kali-05"
      kalicluster.vm.network "private_network", ip: "192.168.50.6"
      kalicluster.vm.network "forwarded_port", guest: 9392, host: 9392 #openVAS Web GUI
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-kali-05"
          vb.memory = "1024"
          vb.gui = true
      end
      kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
      kalicluster.vm.provision "shell", inline: $kalisandbox_script
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"

    end 

    #bridged network, DHCP enabled auto IP assignment
    config.vm.define "vg-ubuntu-01" do |kalicluster|
      kalicluster.vm.box = "bento/ubuntu-20.04"
      kalicluster.vm.hostname = "vg-ubuntu-01"
      kalicluster.vm.network "public_network"
      kalicluster.vm.network "forwarded_port", guest: 22, host: 2214
      # kalicluster.vm.network "forwarded_port", guest: 22, host: 2202
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-ubuntu-01"
          vb.memory = "1024"
          vb.gui = false
      end
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end

    #bridged network, DHCP enabled auto IP assignment
    config.vm.define "vg-ubuntu-02" do |kalicluster|
      # https://app.vagrantup.com/ubuntu/boxes/hirsute64
      # kalicluster.vm.box = "ubuntu/hirsute64" #21.04
      # https://app.vagrantup.com/ubuntu/boxes/bionic64
      kalicluster.vm.box = "ubuntu/bionic64"
      kalicluster.vm.box_download_insecure=true
      kalicluster.vm.hostname = "vg-ubuntu-02"
      kalicluster.vm.network "public_network"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-ubuntu-02"
          vb.memory = "786"
          vb.gui = false
      end
      # with root user, sudo not required
      kalicluster.vm.provision "shell", inline: $ubuntu_docker_script, privileged: true 
      # with vagrant user, sudo required
      # kalicluster.vm.provision "shell", inline: $ubuntu_docker_script, privileged: false
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end

    #bridged network, DHCP enabled auto IP assignment
    config.vm.define "vg-ubuntu-03" do |kalicluster|
      # https://app.vagrantup.com/ubuntu/boxes/impish64
      # kalicluster.vm.box = "ubuntu/impish64" #21.10      
      # https://app.vagrantup.com/ubuntu/boxes/focal64
      kalicluster.vm.box = "ubuntu/focal64" #20.04 
      kalicluster.vm.box_download_insecure=true
      kalicluster.vm.hostname = "vg-ubuntu-03"
      kalicluster.vm.network "public_network"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-ubuntu-03"
          vb.memory = "1024"
          vb.gui = false
      end
      # kalicluster.vm.provision "shell", inline: $ubuntu_docker_script, privileged: false
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end

    #https://kifarunix.com/install-and-setup-gvm-20-08-on-ubuntu/
    config.vm.define "vg-ubuntu-04" do |kalicluster|
      # kalicluster.vm.box = "bento/ubuntu-20.04"
      # kalicluster.vm.box = "bento/ubuntu-16.04"
      # https://app.vagrantup.com/ubuntu/boxes/xenial64
      kalicluster.vm.box = "ubuntu/xenial64"
      kalicluster.vm.hostname = "vg-ubuntu-04"
      kalicluster.vm.boot_timeout = 1800 # 30 minutes
      kalicluster.vm.network "public_network"
      # kalicluster.vm.network "private_network", ip: "192.168.50.6"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-ubuntu-04"
          vb.memory = "1024"
          vb.gui = false
      end
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end    
    
    #bridged network,DHCP enabled,auto IP assignment
    config.vm.define "vg-centos-01" do |kalicluster|
      # https://app.vagrantup.com/centos/boxes/stream8
      kalicluster.vm.box = "centos/stream8" 
      kalicluster.vm.hostname = "vg-centos-01"
      kalicluster.vm.network "public_network"
      kalicluster.vm.network "forwarded_port", guest: 22, host: 2216
      # kalicluster.vm.network "private_network", ip: "192.168.50.6"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-centos-01"
          vb.memory = "1024"
          vb.gui = false
      end
      # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
      # kalicluster.vm.provision "shell", inline: $centos_docker_script
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"

    end 

    #bridged network, DHCP enabled auto IP assignment
    config.vm.define "vg-centos-02" do |kalicluster|
      # https://app.vagrantup.com/centos/boxes/8
      # kalicluster.vm.box = "centos/8"       
      kalicluster.vm.box = "centos/8"
      kalicluster.vm.hostname = "vg-centos-02"
      kalicluster.vm.network "public_network"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-centos-02"
          vb.memory = "1024"
          vb.gui = true
      end
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end

    # https://geekflare.com/apache-setup-ssl-certificate/
    config.vm.define "vg-centos-03" do |kalicluster|
      # https://app.vagrantup.com/centos/boxes/8
      # kalicluster.vm.box = "centos/8"       
      kalicluster.vm.box = "centos/8"
      kalicluster.vm.hostname = "vg-centos-03"
      # kalicluster.vm.network "public_network"
      kalicluster.vm.network "private_network", ip: "192.168.50.7"
      # kalicluster.vm.network "forwarded_port", guest: 80, host: 80
      #Disabling the default /vagrant share can be done as follows:
      # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
      kalicluster.vm.provider "virtualbox" do |vb|
          vb.name = "vbox-centos-03"
          vb.memory = "768"
          vb.gui = false
      end
      kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    end    
        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-fedora-01" do |kalicluster|
          # https://app.vagrantup.com/bento/boxes/fedora-latest
          kalicluster.vm.box = "bento/fedora-latest" 
          kalicluster.vm.hostname = "vg-fedora-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vbox-fedora-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $debian_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end  

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-fedora-cl01" do |kalicluster|
          # https://app.vagrantup.com/fedora/boxes/35-cloud-base
          kalicluster.vm.box = "fedora/35-cloud-base" 
          kalicluster.vm.hostname = "vg-fedora-cl01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-fedora-cl01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $debian_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end 

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-debian-01" do |kalicluster|
          # https://app.vagrantup.com/debian/boxes/bullseye64
          kalicluster.vm.box = "debian/bullseye64" #debian 11
          kalicluster.vm.hostname = "vg-debian-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vbox-debian-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          kalicluster.vm.provision "shell", inline: $dockerce_debian_bullseye_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end     

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-opensuse-tw01" do |kalicluster|
          # https://app.vagrantup.com/opensuse/boxes/Tumbleweed.x86_64
          kalicluster.vm.box = "opensuse/Tumbleweed.x86_64" 
          kalicluster.vm.hostname = "vg-opensuse-tw01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vbox-opensuse-tw01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $opensuse_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end         

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-opensuse-tw-arm01" do |kalicluster|
          # https://app.vagrantup.com/opensuse/boxes/Tumbleweed.aarch64
          kalicluster.vm.box = "opensuse/Tumbleweed.aarch64" 
          kalicluster.vm.hostname = "vg-opensuse-tw-arm01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vbox-opensuse-tw-arm01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $opensuse_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end           

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-opensuse-lp01" do |kalicluster|
          # https://app.vagrantup.com/opensuse/boxes/Leap-15.3.x86_64
          kalicluster.vm.box = "opensuse/Leap-15.3.x86_64" 
          kalicluster.vm.hostname = "vg-opensuse-lp01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vbox-opensuse-lp01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $opensuse_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end 

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-opensuse-lp-arm01" do |kalicluster|
          # https://app.vagrantup.com/opensuse/boxes/Leap-15.3.aarch64
          # AArch64 (also known as ARMv8) is the name for the new 64-bit ARM architecture
          kalicluster.vm.box = "opensuse/Leap-15.3.aarch64" #libvirt
          kalicluster.vm.hostname = "vg-opensuse-lp-arm01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-opensuse-lp-arm01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $opensuse_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end      

        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-archlinux-01" do |kalicluster|
          # https://app.vagrantup.com/archlinux/boxes/archlinux
          kalicluster.vm.box = "archlinux/archlinux" #libvirt
          kalicluster.vm.hostname = "vg-archlinux-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-archlinux-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $archlinux_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end  

        # PROBLEM!!! vg-freebsd-01: Warning: Connection aborted. Retrying...
        #bridged network,DHCP enabled,auto IP assignment
        config.vm.define "vg-freebsd-01" do |kalicluster|
          # https://app.vagrantup.com/freebsd/boxes/FreeBSD-13.0-RELEASE
          kalicluster.vm.box = "freebsd/FreeBSD-13.0-RELEASE" #libvirt
          kalicluster.vm.hostname = "vg-freebsd-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-freebsd-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end

        #vg-freebsd-02: sh: /tmp/vagrant-shell: not found The SSH command responded with a non-zero exit status.
        config.vm.define "vg-freebsd-02" do |kalicluster|
          # https://app.vagrantup.com/freebsd/boxes/FreeBSD-13.0-RELEASE
          kalicluster.vm.box = "bento/freebsd-13.0" #libvirt
          kalicluster.vm.hostname = "vg-freebsd-02"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-freebsd-02"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end


        #bridged network,DHCP enabled,auto IP assignment
        #https://rockylinux.org/
        config.vm.define "vg-rockylinux-01" do |kalicluster|
          # https://github.com/chef/bento/blob/main/packer_templates/rockylinux
          kalicluster.vm.box = "bento/rockylinux-8.4" #libvirt
          kalicluster.vm.hostname = "vg-rockylinux-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-rockylinux-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end

        #bridged network,DHCP enabled,auto IP assignment
        #https://rockylinux.org/
        # https://app.vagrantup.com/rockylinux
        config.vm.define "vg-rockylinux-02" do |kalicluster|
          # https://github.com/chef/bento/blob/main/packer_templates/rockylinux
          kalicluster.vm.box = "bento/rockylinux-8.4" #libvirt
          kalicluster.vm.hostname = "vg-rockylinux-02"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-rockylinux-02"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end        

        #bridged network,DHCP enabled,auto IP assignment
        #https://springdale.math.ias.edu/
        config.vm.define "vg-springdalelinux-01" do |kalicluster|
          # https://github.com/chef/bento/blob/main/packer_templates/rockylinux
          kalicluster.vm.box = "bento/springdalelinux-7.9" #libvirt
          kalicluster.vm.hostname = "vg-springdalelinux-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-springdalelinux-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end

        #bridged network,DHCP enabled,auto IP assignment
        #https://springdale.math.ias.edu/
        config.vm.define "vg-scientific-01" do |kalicluster|
          # https://github.com/chef/bento/blob/main/packer_templates/rockylinux
          kalicluster.vm.box = "bento/scientific-7.9" #libvirt
          kalicluster.vm.hostname = "vg-scientific-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-scientific-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end

        #bridged network,DHCP enabled,auto IP assignment
        # vg-rhel-01: sh: /tmp/vagrant-shell: not found
        config.vm.define "vg-rhel-01" do |kalicluster|
          # https://github.com/chef/bento/blob/main/packer_templates/rockylinux
          kalicluster.vm.box = "bento/windows-2016-standard" #libvirt
          kalicluster.vm.hostname = "vg-rhel-01"
          kalicluster.vm.network "public_network"
          # kalicluster.vm.network "private_network", ip: "192.168.50.6"
          # kalicluster.vm.network "forwarded_port", guest: 80, host: 81
          #Disabling the default /vagrant share can be done as follows:
          # kalicluster.vm.synced_folder ".", "/vagrant", disabled: true
          kalicluster.vm.provider "virtualbox" do |vb|
              vb.name = "vg-rhel-01"
              vb.memory = "768"
              vb.gui = false
          end
          # kalicluster.vm.provision "shell",    inline: "hostnamectl set-hostname vg-kali-05"
          # kalicluster.vm.provision "shell", inline: $freebsd_docker_script
          kalicluster.vm.provision :shell, path: "provisioning/bootstrap.sh"
    
        end

end
