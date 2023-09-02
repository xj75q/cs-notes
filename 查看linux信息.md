#### 【查看CPU 信息】

以下2条都可以

```
>> uname -a 
>> cat /proc/cpuinf
```

查看cpu型号

```
>> cat /proc/cpuinfo | grep name | cut -f2 -d: | uniq -c
```

查看物理cpu个数

```
>> cat /proc/cpuinfo | grep "physical id" | sort | uniq | wc -l
```

查看每个物理CPU中core的个数(即核数)

```
>> cat /proc/cpuinfo | grep "cpu cores" | uniq
cpu cores    : 8
```

查看逻辑CPU的个数

```
>> cat /proc/cpuinfo | grep "processor" | wc -l

16
```



关闭CPU的超线程

```
>> echo off > /sys/devices/system/cpu/smt/control
```



#### 【查看内存条信息】

安装工具dmidecode

使用

1.查看内存槽及内存条

```auto
$ sudo dmidecode -t memory
```

2.查看内存的插槽数,已经使用多少插槽.每条内存多大

```auto
$ sudo dmidecode -t memory | grep Size
```

3.查看服务器型号、序列号

```auto
$ sudo dmidecode | grep "System Information" -A9 | egrep "Manufacturer|Product|Serial"
```

