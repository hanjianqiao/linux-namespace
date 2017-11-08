## set weight

Create two groups

```
su
cd /sys/fs/cgroup/blkio/
mkdir blkio0
mkdir blkio1
```
*Make sure block uses cfq*

```
cat /sys/block/<DEVICE_NAME>/queue/scheduler
```
see: [Stackoverflow][no io scheduler]

```
echo 1000 > blkio0/blkio.weight
echo 500 > blkio1/blkio.weight
```

```
sudo cgexec -g blkio:blkio0 time dd if=/dev/zero of=file_0 bs=1M count=4000 oflag=direct &
sudo cgexec -g blkio:blkio1 time dd if=/dev/zero of=file_1 bs=1M count=4000 oflag=direct &
```

[no io scheduler]: https://serverfault.com/questions/693348/what-does-it-mean-when-linux-has-no-i-o-scheduler