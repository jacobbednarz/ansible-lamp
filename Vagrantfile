Vagrant::Config.run do |config|
  config.vm.define :server do |server_config|
    server_config.vm.box = "precise64"
    server_config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
    server_config.vm.forward_port 80, 8080
    server_config.vm.forward_port 443, 4443
    server_config.vm.network :bridged
    server_config.vm.network :hostonly, "192.168.100.10"

    server_config.vm.provision :ansible do |ansible|
      ansible.playbook = "servers.yml"
      ansible.verbose = true
      ansible.inventory_path = "hosts"
    end
  end
end