#Script to be executed
$initscript = <<SCRIPT
yum install git ansible -y
git clone #Reponame
push repo
yum localinstall jdk
#Check for the first Run
if [ -f filename ]; then
	ansible-playbook exec
else
	ansible-playbook other playbook
fi
#Vagrant File for Centos 7
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "vagrant.localdomain"
  config.vm.provision "shell", inline: $initscript
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = "4"
  end
end
