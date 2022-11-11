Vagrant.configure("2") do |config|
    config.vm.define "ubuntu" do |ubuntu|
        ubuntu.vm.box = "bento/ubuntu-18.04"
        config.vm.provider "virtualbox" do |vb|
            vb.memory = "4096"
            vb.cpus = "1"
          end
        # check if more ports are needed for your application
        config.vm.network "forwarded_port", guest: 8000, host: 8000

        # mind the folder structure on your host machine, changes are synced to and from the guest
        config.vm.synced_folder "./vagrant_data", "/vagrant", SharedFoldersEnableSymlinksCreate: false

        config.vm.provision "docker-compose-setup", type: "shell", preserve_order: true, path: "./vagrant_data/docker/install.sh"
        config.vm.provision :docker
        config.vm.provision "docker-compose-run", type: "shell",preserve_order: true, :run => 'always', path: "./vagrant_data/docker/run.sh"

        ubuntu.trigger.before :destroy, :halt do |trigger|
            trigger.info = "Stopping container..."
            trigger.run_remote = {inline: "cd /vagrant/docker && docker-compose stop"}
        end
    end
end
