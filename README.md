# Redis Cluster Vagrant example

## How to start

vagrant up
vagrant ssh redis01
redis-cli -a pass --cluster create 10.11.8.2:6379 10.11.8.3:6379 10.11.8.4:6379 10.11.8.5:6379 10.11.8.6:6379 10.11.8.7:6379 --cluster-replicas 1
