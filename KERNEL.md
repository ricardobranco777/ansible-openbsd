
Tracking -current:

```
# Upgrade to latest snapshot
sysupgrade -s
sudo pkg_add -u
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

Compile world (not worth it if you have latest snapshot):

```
cd /usr/src
make obj
make -j8 build
sysmerge
cd /dev && ./MAKEDEV all
```
