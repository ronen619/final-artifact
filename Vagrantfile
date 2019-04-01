Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = 'tomcat1'

  config.vm.provider 'virtualbox' do |virtualbox|
    virtualbox.linked_clone = true
    virtualbox.name = 'tomcat1'
    virtualbox.gui = false
    virtualbox.memory =  1024
    virtualbox.cpus = 1
    virtualbox.customize ['modifyvm', :id, '--vram', 64]
    virtualbox.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    virtualbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    virtualbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080, protocol: "tcp"
  config.vm.network "forwarded_port", guest: 9090, host: 9090, protocol: "tcp"

  config.vm.provision 'shell' do |initscript|
    initscript.path="user-data-scripts/user-data.sh"
  end

  config.vm.provision "file", source: "machine-content/port-modifier.sh", destination: "/etc/tomcat/port-modifier.sh"
end
