Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
#  config.vm.box = "debian/stretch64"
 
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048 
  end

  config.vm.network "public_network", bridge: [
        "en11: Thunderbolt Ethernet Slot 1",
        "en0: Wi-Fi (AirPort)"
    ]

  config.vm.provision "shell", inline: <<-SHELL
    apt -y update
    apt install -y python-minimal
  SHELL

  config.vm.provision "ansible" do |x|
    x.playbook = "indico-dev.yml"
  end

end
