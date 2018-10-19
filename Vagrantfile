require 'yaml'

vagrant_root = File.dirname(__FILE__)
defaults_config_filepath = vagrant_root + '/configuration/defaults.yml'
containers_filepath = vagrant_root + '/docker/containers.yml'

Vagrant.configure('2') do |config|

  properties = YAML.load(File.read(defaults_config_filepath))
  containers = YAML.load(File.read(containers_filepath))

  config.vm.box = properties['vm'].fetch('box', 'bento/ubuntu-16.04')

  config.vm.provider 'virtualbox' do |vm|
    vm.memory = properties['vm']['memory']
    vm.cpus = properties['vm']['cpus']
  end

  config.vm.network 'private_network', ip: properties['vm']['network_ip']

  config.vm.synced_folder ".", "/vagrant/"
  
  containers.each do |container|
    config.vm.provision "docker" do |d|
      d.build_image "/vagrant/" + container["dir"],
                    args: "-t %s" % container["name"]
    end
  end
  
  config.vm.provision 'docker_compose', yml: "/vagrant/docker/docker-compose.yml", run: "always"
end