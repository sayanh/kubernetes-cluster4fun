# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

  boxes = [
    {
      :name => 'master1',
      :box => 'ubuntu/xenial64',
      :ip => '192.168.1.2',
      :cpu => '33',
      :ram => '1024'
    },
    {
      :name => 'node1',
      :box => 'ubuntu/xenial64',
      :ip => '192.168.1.3',
      :cpu => '33',
      :ram => '1024'
    },
    {
      :name => 'node2',
      :box => 'ubuntu/xenial64',
      :ip => '192.168.1.4',
      :cpu => '33',
      :ram => '1024'
    },
    {
        :name => 'etcd1',
        :box => 'ubuntu/xenial64',
        :ip => '192.168.1.5',
        :cpu => '33',
        :ram => '1024'
    }
  ]

  Vagrant.configure('2') do |config|
    boxes.each do |box|
      config.vm.define box[:name] do |vms|
        vms.vm.box = box[:box]
        vms.vm.hostname = "#{box[:name]}"

        vms.vm.provider 'virtualbox' do |v|
          v.customize ['modifyvm', :id, '--cpuexecutioncap', box[:cpu]]
          v.customize ['modifyvm', :id, '--memory', box[:ram]]
        end

        vms.vm.network :private_network, ip: box[:ip]

      end
    end
  end
