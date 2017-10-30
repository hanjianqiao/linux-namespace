# Limit CPU cores


```
su

mkdir /sys/fs/cgroup/cpuset/0cpu

echo 0 > /sys/fs/cgroup/cpuset/0cpu/cpuset.cpus
echo 0 > /sys/fs/cgroup/cpuset/0cpu/cpuset.mems

echo ${PID} > /sys/fs/cgroup/cpuset/0cpu/tasks
```
will limit ${PID} to cpu 0




