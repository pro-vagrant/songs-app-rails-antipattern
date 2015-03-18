VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "http://boxes.gajdaw.pl/rails/rails-v0.5.5.box"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  config.vm.network :forwarded_port, guest: 3000, host: 3000, host_ip: "127.0.0.1"

$script = <<SCRIPT

cd /vagrant
rails server -b 0.0.0.0 -d

SCRIPT

  config.vm.provision "shell", inline: $script, run: "always"


end
