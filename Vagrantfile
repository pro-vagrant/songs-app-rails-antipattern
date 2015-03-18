VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty32"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  config.vm.network :forwarded_port, guest: 3000, host: 3000, host_ip: "127.0.0.1"

  config.vm.provision "shell", path: "script.sh"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.manifest_file  = "default.pp"
    puppet.options = ['--verbose']
  end

$script = <<SCRIPT

cd /vagrant
rails server -b 0.0.0.0 -d

SCRIPT

  config.vm.provision "shell", inline: $script, run: "always"

end
