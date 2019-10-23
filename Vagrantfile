#Script to be executed
$initscript = <<SCRIPT
if [ ! -f /root/provisioner ]; then
	yum install git ansible -y
	curl -O https://data-viewer-setup.s3.amazonaws.com/jdk-8u161-linux-x64.rpm
	yum localinstall jdk-8u161-linux-x64.rpm -y
	curl -O http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
        rpm -ivh mysql-community-release-el7-5.noarch.rpm
	yum install mysql-connector-java.noarch -y
	git clone https://github.com/saikrishnavedaraju/ansible-vagrant.git
	pushd ansible-vagrant/ansible/playbooks
	ansible-playbook iw-play.yml -i hosts --connection=local
fi
touch /root/provisioner
SCRIPT
#Vagrant File for Centos 7
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  config.vm.hostname = "vagrant.localdomain"
  config.vm.network "public_network"
  config.vm.provision "shell", inline: $initscript
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = "4"
  end
end
