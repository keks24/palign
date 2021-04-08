# Introduction
`palign` checks, if hard drive partitions are aligned optimally by `logical block size` and `physical block size` using `bash`.

# Prerequisites
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
    * `/sys/` and `/proc/` are accessable

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
$ palign [device_name...]
```

## Examples
```bash
$ palign
/dev/sda:
    /dev/sda1
        Start sector size (2048 Sectors, 1048576 Byte)
            Divided by 'Logical block size' (512 Byte):         4.000000 Sectors        Partition alignment optimal.
            Divided by 'Physical block size' (4096 Byte):       0.000000 Sectors        Partition not aligned!
```
```bash
$ palign sda sdb sdc sdd
/dev/sda:
    /dev/sda1
        Start sector size (2048 Sectors, 1048576 Byte)
            Divided by 'Logical block size' (512 Byte):         4.000000 Sectors        Partition alignment optimal.
            Divided by 'Physical block size' (4096 Byte):       0.000000 Sectors        Partition not aligned!

/dev/sdb:
    /dev/sdb1
        Start sector size (2048 Sectors, 1048576 Byte)
            Divided by 'Logical block size' (512 Byte):         4.000000 Sectors        Partition alignment optimal.
            Divided by 'Physical block size' (512 Byte):        4.000000 Sectors        Partition alignment optimal.
    /dev/sdb2
        Start sector size (20973568 Sectors, 10738466816 Byte)
            Divided by 'Logical block size' (512 Byte):         40964.000000 Sectors    Partition alignment optimal.
            Divided by 'Physical block size' (512 Byte):        40964.000000 Sectors    Partition alignment optimal.

/dev/sdc:
    /dev/sdc1
        Start sector size (2048 Sectors, 1048576 Byte)
            Divided by 'Logical block size' (512 Byte):         4.000000 Sectors        Partition alignment optimal.
            Divided by 'Physical block size' (512 Byte):        4.000000 Sectors        Partition alignment optimal.
    /dev/sdc2
        Start sector size (6144 Sectors, 3145728 Byte)
            Divided by 'Logical block size' (512 Byte):         12.000000 Sectors       Partition alignment optimal.
            Divided by 'Physical block size' (512 Byte):        12.000000 Sectors       Partition alignment optimal.
    /dev/sdc3
        Start sector size (268288 Sectors, 137363456 Byte)
            Divided by 'Logical block size' (512 Byte):         524.000000 Sectors      Partition alignment optimal.
            Divided by 'Physical block size' (512 Byte):        524.000000 Sectors      Partition alignment optimal.

/dev/sdd:
    /dev/sdd1
        Start sector size (40 Sectors, 20480 Byte)
            Divided by 'Logical block size' (512 Byte):         0.000000 Sectors        Partition not aligned!
            Divided by 'Physical block size' (512 Byte):        0.000000 Sectors        Partition not aligned!
```

# Parameters
Multiple `device names` can be analysed.
