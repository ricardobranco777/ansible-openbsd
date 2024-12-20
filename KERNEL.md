
Tracking -current:

```
# Upgrade to latest snapshot
sysupgrade -s
sudo pkg_add -u
```

Tracking -stable:

```
wget -O- https://ftp.openbsd.org/pub/OpenBSD/7.6/src.tar.gz | tar -zxf - -C /usr/src/
cd /usr/
cvs -qd anoncvs@ftp.hostserver.de:/cvs checkout -rOPENBSD_7_6 -P src
```

Updating the above:

```
cd /usr/src
cvs -q up -Pd -rOPENBSD_7_6
```

Compile kernel:

```
cd /sys/arch/amd64/conf
config CUSTOM
cd ../compile/CUSTOM
make obj
make config
make -j8
sudo make install
```

Compile world (not worth it if you have latest snapshot):

```
cd /usr/src
make obj
make -j8 build
sysmerge
cd /dev && ./MAKEDEV all
```
