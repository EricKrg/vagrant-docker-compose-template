# Vagrant docker-compose template

Since docker is not compatible with some IT-security precautions it becomes necessary to run containerized applications
in closed vitrual environment (even if that may sound a bit strange).

Because the offical vagrant-plugin for docker-compose only supports docker-compose v1, i created this template
which alows you to run docker-compose configurations with vagrant only using vagrants internal tools and hooks.

## Usage

Start the Example with: `vagrant up` Stop the box: `vagrant halt`

Define the docker-compose version you want to use in `./vagrant_data/docker/install.sh` currently `v2.12.2`

Replace the sample files and place all the relevant files for your docker-compose env. in `./vagrant_data/docker/`  

**Feel free to use and improve this template.**
