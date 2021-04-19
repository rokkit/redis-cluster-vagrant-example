# Redis Cluster Vagrant example

Create a Redis Cluster with 6 nodes. References in [tutorial](https://redis.io/topics/cluster-tutorial)

## How to start

Start VM set

```bash
vagrant up
```

SSH to one of VMs

```bash
vagrant ssh redis01
```

Create Redis Cluster

```bash
redis-cli -a pass --cluster create 10.11.8.2:6379 \
                                   10.11.8.3:6379 \
                                   10.11.8.4:6379 \
                                   10.11.8.5:6379 \
                                   10.11.8.6:6379 \
                                   10.11.8.7:6379 --cluster-replicas 1
```
