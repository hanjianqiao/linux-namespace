```
cd /sys/fs/cgroup/net_prio
su
mkdir low
mkdir high
echo "eth0 1" > /sys/fs/cgroup/net_prio/low/net_prio.ifpriomap
echo "eth1 1" > /sys/fs/cgroup/net_prio/low/net_prio.ifpriomap
```

run

```
cat net_prio.ifpriomap
```

get:

```
lo 0
eth0 1
eth1 1
docker0 0
```
