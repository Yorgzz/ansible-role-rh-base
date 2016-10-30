# vi: ft=ruby

VAGRANTFILE_API_VERSION = '2'
ROLE_NAME = 'base'

hosts = [
  { maintainer: 'bertvv', distro: 'centos72', ip: '192.168.56.4' },
  { maintainer: 'bertvv', distro: 'fedora24', ip: '192.168.56.5' }
]

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  hosts.each do |host|
    host_name = host[:distro] + '-' + ROLE_NAME

    config.vm.define host_name do |node|
      node.vm.box = host[:maintainer] + '/' + host[:distro]
      node.vm.hostname = host_name
      node.vm.network :private_network, ip: host[:ip]
    end
  end
  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'test.yml'
  end
end
