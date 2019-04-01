

      Vagrant.configure(2) do |config|
        config.vm.box = "ubuntu/trusty64"

        config.vm.hostname = 'tomcat1'

        config.vm.provider 'virtualbox' do |virtualbox|
          virtualbox.linked_clone = true
          virtualbox.name = 'tomcat1'
          virtualbox.gui = true
          virtualbox.memory =  1024
          virtualbox.cpus = 1

        end



  config.vm.network "forwarded_port", guest: 8080, host: 8080, protocol: "tcp"
  config.vm.network "forwarded_port", guest: 9090, host: 9090, protocol: "tcp"

  config.vm.provision 'shell' do |initscript|
    initscript.path="user-data-scripts/user-data.sh"
  end

  config.vm.provision "file", source: "machine-content/port-modifier.sh", destination: "machine-content/port-modifier.sh"
end