## create cgroup

```
su
cd /sys/fs/cgroup/blkio/
mkdir foo
cd foo/
```

## limit and test

origin speed:

```
dd if=/dev/zero of=/home/lct/tmp/zero1 bs=1M count=511 oflag=direct
511+0 records in
511+0 records out
535822336 bytes (536 MB, 511 MiB) copied, 4.47307 s, 120 MB/s
```


set limit and write:

* write bps

```
echo "253:0 1048576" > blkio.throttle.write_bps_device
```

```
dd if=/dev/zero of=/home/lct/tmp/zero1 bs=1M count=5 oflag=direct
5+0 records in
5+0 records out
5242880 bytes (5.2 MB, 5.0 MiB) copied, 7.44286 s, 704 kB/s
```

* io bps

```
echo "253:0 2" > blkio.throttle.write_iops_device
```

```
dd if=/dev/zero of=/home/lct/tmp/zero1 bs=1M count=5 oflag=direct
5+0 records in
5+0 records out
5242880 bytes (5.2 MB, 5.0 MiB) copied, 5.00937 s, 1.0 MB/s
```
