# Enabling `cgroups` to Run `k3s`

To be able to run recent revisions of [`k3s`](https://k3s.io) (as well as being able to enforce resource quotas) you need to add the following options to `/boot/cmdline.txt` and reboot:

```
cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory swapaccount=1
```

Since some Pi firmwares require you to add this tweak to other files instead, you should check the results by doing `cat /proc/cmdline`.