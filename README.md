# Introduction
`palign` checks, if hard drive partitions are aligned optimally by `logical block size` and `physical block size` using `bash`.

# Prerequisites
* The following packages are installed:
```no-highlight
awk
```

* The path `/usr/local/bin/` exists in the `${PATH}` variable:
```bash
$ echo "${PATH//:/\n}"
```
```
/home/ramon/bin
/usr/local/bin
/usr/bin
/bin
/usr/local/sbin
/usr/sbin
/sbin
/usr/local/games
/usr/games
/usr/lib/llvm/6/bin
/opt/bin
```

* `sysfs` and `procfs` are configured properly

# Installation
Clone the repository into your current working directory:
```bash
$ git clone "https://codeberg.org/keks24/palign.git"
```

Copy all necessary files:
```bash
$ cd "palign/"
$ cp "usr/local/bin/palign" "/usr/local/bin/"
$ chmod 755 "/usr/local/bin/palign"
```

# Usage
```bash
$ palign
/dev/sda1 (Partition size: 2000396746752 Byte)
    Divided by 512 Bytes (Logical block size)   3907024896.000000 Byte  Partition alignment optimal.
    Divided by 4096 Bytes (Physical block size) 488378112.000000 Byte   Partition alignment optimal.
```
```bash
$ palign sda sdb sdc sdd
/dev/sda1 (Partition size: 2000396746752 Byte)
    Divided by 512 Bytes (Logical block size)   3907024896.000000 Byte  Partition alignment optimal.
    Divided by 4096 Bytes (Physical block size) 488378112.000000 Byte   Partition alignment optimal.

/dev/sdb1 (Partition size: 10737418240 Byte)
    Divided by 512 Bytes (Logical block size)   20971520.000000 Byte    Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  20971520.000000 Byte    Partition alignment optimal.

/dev/sdb2 (Partition size: 489368346624 Byte)
    Divided by 512 Bytes (Logical block size)   955797552.000000 Byte   Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  955797552.000000 Byte   Partition alignment optimal.

/dev/sdc1 (Partition size: 2097152 Byte)
    Divided by 512 Bytes (Logical block size)   4096.000000 Byte        Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  4096.000000 Byte        Partition alignment optimal.

/dev/sdc2 (Partition size: 134217728 Byte)
    Divided by 512 Bytes (Logical block size)   262144.000000 Byte      Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  262144.000000 Byte      Partition alignment optimal.

/dev/sdc3 (Partition size: 59884068864 Byte)
    Divided by 512 Bytes (Logical block size)   116961072.000000 Byte   Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  116961072.000000 Byte   Partition alignment optimal.

/dev/sdd1 (Partition size: 320070483968 Byte)
    Divided by 512 Bytes (Logical block size)   625137664.000000 Byte   Partition alignment optimal.
    Divided by 512 Bytes (Physical block size)  625137664.000000 Byte   Partition alignment optimal.
```

# Parameters
Multiple `device names` can be analysed.
