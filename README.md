ioping
======

forked from [koct9i/ioping](https://github.com/koct9i/ioping).
Added Extra Feature `-O` and `-Q` for output .

An tool to monitor I/O latency in real time.
It shows disk latency in the same way as ping shows network latency.

Homepage: https://github.com/koct9i/ioping/
(migrated from http://code.google.com/p/ioping/)

Please send your patches, issues and questions to
https://github.com/koct9i/ioping/issues/

Supported OS
------------

* GNU/Linux
* GNU/HURD
* Windows
* OS X
* FreeBSD
* DragonFlyBSD
* OpenBSD

Packages
--------

* Debian: https://packages.debian.org/unstable/main/ioping
* Ubuntu: https://launchpad.net/ubuntu/+source/ioping
* Fedora: https://apps.fedoraproject.org/packages/ioping
* ArchLinux: https://www.archlinux.org/packages/community/x86_64/ioping
* AltLinux: http://www.sisyphus.ru/en/srpm/Sisyphus/ioping
* Gentoo: https://packages.gentoo.org/package/app-benchmarks/ioping
* Nix: https://github.com/NixOS/nixpkgs/blob/master/pkgs/tools/system/ioping/default.nix
* FreeBSD: http://www.freshports.org/sysutils/ioping
* OS X: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/ioping.rb

Extra Feature
-------------

The main aim is to  give the user opportunity to get statistics always in ms unit.
It's useful for metrics and monitoring.

`-Q` sets always ms
```
$ .\ioping.exe -Q -c 2 c:\ClusterStorage\Volume1\temp
ioping: non-cached I/O not supported by this platform
ioping: you can use write I/O to get reliable results
4 KiB <<< c:\ClusterStorage\Volume1\temp ( ): request=1 time=473 us time=0.5 ms (warmup)
4 KiB <<< c:\ClusterStorage\Volume1\temp ( ): request=2 time=662 us time=0.7 ms

--- c:\ClusterStorage\Volume1\temp ( ) ioping statistics ---
662 us time=0.7 ms time=0.7 ms requests completed in 662 us, 4 KiB read, 1.51 k iops, 5.90 MiB/s
generated 1.00 s time=1001.5 ms requests in 1.00 s, 8 KiB, 1 iops, 7.99 KiB/s
min/avg/max/mdev = 662 us time=0.7 ms / 662 us time=0.7 ms / 662 us time=0.7 ms / 0 ns time=0.0 ms
``` 

`-O` sets old style of output

```
$ .\ioping.exe -O -c 2 c:\ClusterStorage\Volume1\temp
ioping: non-cached I/O not supported by this platform
ioping: you can use write I/O to get reliable results
4 KiB <<< c:\ClusterStorage\Volume1\temp ( ): request=1 time=451 us (warmup)
4 KiB <<< c:\ClusterStorage\Volume1\temp ( ): request=2 time=755 us

--- c:\ClusterStorage\Volume1\temp ( ) ioping statistics ---
755 us0.8 ms requests completed in 755 us, 4 KiB read, 1.32 k iops, 5.17 MiB/s
generated 1.00 s requests in 1.00 s, 8 KiB, 1 iops, 7.98 KiB/s
min/avg/max/mdev = 755 us / 755 us / 755 us / 0 ns
```

Examples
--------

Show disk I/O latency using the default values and the current directory, until interrupted

```
$ ioping .
4096 bytes from . (ext4 /dev/sda3): request=1 time=0.2 ms
4096 bytes from . (ext4 /dev/sda3): request=2 time=0.2 ms
4096 bytes from . (ext4 /dev/sda3): request=3 time=0.3 ms
4096 bytes from . (ext4 /dev/sda3): request=4 time=12.7 ms
4096 bytes from . (ext4 /dev/sda3): request=5 time=0.3 ms
^C
--- . (ext4 /dev/sda3) ioping statistics ---
5 requests completed in 4794.0 ms, 364 iops, 1.4 MiB/s
min/avg/max/mdev = 0.2/2.8/12.7/5.0 ms
```

Measure disk seek rate (iops, avg)

```
$ ioping -R /dev/sda

--- /dev/sda (device 465.8 GiB) ioping statistics ---
186 requests completed in 3004.6 ms, 62 iops, 0.2 MiB/s
min/avg/max/mdev = 6.4/16.0/26.8/4.7 ms
```

Measure disk sequential speed (MiB/s)

```
$ ioping -RL /dev/sda

--- /dev/sda (device 465.8 GiB) ioping statistics ---
837 requests completed in 3004.1 ms, 292 iops, 72.9 MiB/s
min/avg/max/mdev = 2.0/3.4/28.9/2.0 ms
```

Authors
-------

* Konstantin Khlebnikov <koct9i@gmail.com>
* Kir Kolyshkin <kir@openvz.org>
* Extra Feature - Przemyslaw Mika <przemyslaw@mika.pro>

Licensed under GPLv3 (or later) <http://www.gnu.org/licenses/gpl-3.0.txt>