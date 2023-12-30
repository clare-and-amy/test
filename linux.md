# Linux 常用的命令
## watch
```linux
watch -n 1 'free -m'
```

## swap 妙用
https://cloud.tencent.com/developer/article/1562033

## systemd
> 历史上，Linux 的启动一直采用init进程
```bash
$ sudo /etc/init.d/apache2 start
# 或者
$ service apache2 start
```
这种方法有两个缺点。

一是启动时间长。init进程是串行启动，只有前一个进程启动完，才会启动下一个进程。

二是启动脚本复杂。init进程只是执行启动脚本，不管其他事情。脚本需要自己处理各种情况，这往往使得脚本变得很长

---

Systemd 就是为了解决这些问题而诞生的。它的设计目标是，为系统的启动和管理提供一套完整的解决方案。

根据 Linux 惯例，字母d是守护进程（daemon）的缩写。 Systemd 这个名字的含义，就是它要守护整个系统。

使用了 Systemd，就不需要再用init了。Systemd 取代了initd，成为系统的第一个进程（PID 等于 1），其他进程都是它的子进程。
### systemctl
> systemctl是 Systemd 的主命令，用于管理系统

```bash
systemctl --version
```

## sysctl 
> 命令允许你查看并且修改 Linux 内核参数

[参考](https://www.cnblogs.com/zwcry/p/9602756.html)