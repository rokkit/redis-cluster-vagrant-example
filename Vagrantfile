# frozen_string_literal: true

provision_script = <<~SCRIPT
  echo "10.11.8.2     redis01.vagrant.local" >> /etc/hosts
  echo "10.11.8.3     redis02.vagrant.local" >> /etc/hosts
  echo "10.11.8.4     redis03.vagrant.local" >> /etc/hosts
  echo "10.11.8.5     redis04.vagrant.local" >> /etc/hosts
  echo "10.11.8.6     redis05.vagrant.local" >> /etc/hosts
  echo "10.11.8.7     redis06.vagrant.local" >> /etc/hosts
  sudo apt-get update && \
      sudo apt-get upgrade -y && \
      sudo apt-get install -y redis-server
SCRIPT

master_config = <<~SCRIPT
  sudo sed -i 's/bind 127.0.0.1/# Bound to 0.0.0.0/' /etc/redis/redis.conf
  sudo sed -i 's/tcp-keepalive 0/tcp-keepalive 60/' /etc/redis/redis.conf
  sudo sed -i 's/appendonly no/appendonly yes/' /etc/redis/redis.conf
  echo "requirepass pass" | sudo tee -a /etc/redis/redis.conf
  echo "maxmemory-policy noeviction" | sudo tee -a /etc/redis/redis.conf

  echo "cluster-enabled yes" | sudo tee -a /etc/redis/redis.conf
  echo "cluster-config-file nodes.conf" | sudo tee -a /etc/redis/redis.conf
  echo "cluster-node-timeout 5000" | sudo tee -a /etc/redis/redis.conf

  sudo systemctl restart redis-server
SCRIPT

Vagrant.configure('2') do |config|
  config.vm.define 'redis01' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis01.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.2'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
  config.vm.define 'redis02' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis02.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.3'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
  config.vm.define 'redis03' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis03.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.4'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
  config.vm.define 'redis04' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis04.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.5'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
  config.vm.define 'redis05' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis05.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.6'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
  config.vm.define 'redis06' do |redis01|
    redis01.vm.box = 'ubuntu/focal64'
    redis01.vm.hostname = 'redis06.vagrant.local'
    redis01.vm.network 'private_network', ip: '10.11.8.7'
    redis01.vm.provision :shell, inline: provision_script
    redis01.vm.provision :shell, inline: master_config
  end
end
