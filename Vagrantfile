
Vagrant.configure("2") do |config|
  config.vm.define "controller" do |controller|
    
    controller.vm.box = "bento/ubuntu-18.04"
    controller.vm.hostname = 'controller'
    controller.vm.network :private_network, ip: "192.168.33.12"
    controller.vm.synced_folder ".", "/home/vagrant/code"
    config.hostsupdater.aliases = ["development.controller"] 
    
  end
end

