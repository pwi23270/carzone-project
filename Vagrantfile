

Vagrant.configure("2") do |config|

#---------------------------------------------
#Box setting
 config.vm.box = "ubuntu/bionic64"
 # config.vm.box_version = "~> 20210720.0.1"
#---------------------------------------------
#Network setting
 config.vm.network "forwarded_port", guest: 7000, host: 7000

#---------------------------------------------
#Folder setting

#---------------------------------------------
#Provider setting
  # config.vm.provider "virtualbox" do |vb|
  # Note: No need since it is by default virtualbox

#---------------------------------------------
#Provision setting
config.vm.provision "shell", inline: <<-SHELL
  systemctl disable apt-daily.service
  systemctl disable apt-daily.timer

  sudo apt-get update
  sudo apt-get install -y python3-venv zip
  touch /home/vagrant/.bash_aliases
  if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
    echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
    echo "alias python='python3'" >> /home/vagrant/.bash_aliases
  fi
SHELL
end
