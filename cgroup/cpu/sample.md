# limit cpu usage sample

operation should be done under root user

```
su
mkdir /sys/fs/cgroup/cpu/10percent
mkdir /sys/fs/cgroup/cpu/20percent

echo 100000 > /sys/fs/cgroup/cpu/10percent/cpu.cfs_period_us
echo 10000 > /sys/fs/cgroup/cpu/10percent/cpu.cfs_quota_us

echo 100000 > /sys/fs/cgroup/cpu/20percent/cpu.cfs_period_us
echo 20000 > /sys/fs/cgroup/cpu/20percent/cpu.cfs_quota_us
```

then open top with

```
top
```

run cpu consumer DIY or from lct-utils

do the following will see cpu usage limited

```
echo ${PID} > /sys/fs/cgroup/cpu/20percent/tasks
echo ${PID} > /sys/fs/cgroup/cpu/20percent/tasks
```


