***************************************************************************
Ansible Lab  
***************************************************************************

Description
==========================================

A lab for learning and experimenting with ansible.

This uses vagrant to simulate a linux server.


Env Setup
====================

1. Start by going to a command line terminal that uses unix like commands such as git bash or Mac CLI. Then create a directory 
on your filesystem that you would like to place the project in. Ex: /Documents/Projects/AnsibleLab.

2. Clone the project from git into your project directory. Then run 'git checkout develop' to checkout the develop branch. 
To get the latest code run 'git pull'.

3. Install the latest versions of VirtualBox (https://www.virtualbox.org/wiki/Downloads) and Vagrant (https://www.vagrantup.com/). 
Once these are installed go to your project directory and run 'vagrant --version' to make sure you have vagrant installed. 
Then install the Guest Additions by running 'vagrant plugin install vagrant-vbguest --plugin-version 0.21'. 
You might be fine with just 'vagrant plugin install vagrant-vbguest' on a MAC using version 0.21 was to address a Windows bug. 
This plugin for VirtualBox allows you to do many things as a developer most importantly it allows you to sync your code 
changes with your VM. Lastly, for both Windows and Mac there is a security setting you need to address first. 
For Mac Google "VirtualBox Problems on macOS (Security & Access)". Follow these instructions. 
After this step you should not have to do this again unless you need to uninstall your VirtualBox.

4. While in your project directory (the one with the Vagrantfile) run 'vagrant up'. This will take a little bit as it is 
downloading and installing packages and setting up the virtual env. To get into your Vagrant machine run 'vagrant ssh'. 
When you are in run "cd /vagrant" to get access to the project code while in the vagrant env. 
To shut down you can either go to the VirtualBox GUI to turn your box off or run "vagrant halt". 
This turns it off and saves your session. If you want to turn it back on again just run "vagrant ssh" again.

5. After that you can use any IDE or text editor such as VS Code or IntelliJ to edit code on your host machine. 
The project folder on your host machine should be synced with the folder on your guest VM in /vagrant. 
Any env specific tasks will be run while in Vagrant. Any git or Vagrant commands can be run outside of the Vagrant VM. 

6. Exit the vagrat ssh if still logged in. To start a ssh client session run vagrant ssh-config to see all the info you need to
run this command:: 

    ssh vagrant@127.0.0.1 -p 2222 -i <Absolute_path_to_your_project>/.vagrant/machines/default/virtualbox/private_key

The Identity file at the end is the private key (cert) that vagrant created for you. 

7. Exit. Make sure you have Ansible installed. If on Windows you will need to do this through WLS using Ubuntu. This is
where you should install ansible and run commands to your testserver (Vagrant).

Quick Start - Comping back after running the above steps
---------------
