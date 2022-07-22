# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
    # This might change later. 
    config.vm.box = "centos/7"
  
    # Disable automatic box update checking. If you disable this, then
    # boxes will only be checked for updates when the user runs
    # `vagrant box outdated`. This is not recommended.
    config.vm.box_check_update = false
  
    config.vm.synced_folder ".", "/vagrant", type:"virtualbox"

    if ARGV[0] != 'plugin'
      required_plugins = ['vagrant-vbguest', 'vagrant-reload']         
      plugins_to_install = required_plugins.select { |plugin| not Vagrant.has_plugin? plugin }
      if not plugins_to_install.empty?
        puts "Installing plugins: #{plugins_to_install.join(' ')}"
        if system "vagrant plugin install #{plugins_to_install.join(' ')}"
          exec "vagrant #{ARGV.join(' ')}"
        else
          abort "Installation of one or more plugins has failed. Aborting."
        end
      end
    end
  
    config.vm.provider :virtualbox do |vb|
      vb.gui = false
      vb.memory = 4096
      vb.cpus = 2
    end
   
    #Provisioning scripts
    install_packages = "/vagrant/vagrant/provision.sh"
  
    config.vm.define "default", primary: true do |default|
  
      default.vm.hostname = "sentel"
  
      # Static IP
      default.vm.network :private_network, ip: "192.168.50.100"
      # Port Forward
      # config.vm.forward_port 80, 8080
      
      default.vm.provision "shell", inline: "chmod +x /vagrant/vagrant/provision.sh"
      default.vm.provision "shell", inline: install_packages, privileged: true
  
      default.vm.post_up_message =
      <<~MSG
      ***************************************
      ****** Provisioned successfully! ******
      *************************************** 
      MSG
    
    end
  end