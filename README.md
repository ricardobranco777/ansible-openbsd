# ansible-openbsd

Ansible configuration for OpenBSD 7.3

NOTES:
- To create the QEMU VM change the CDROM from IDE to SATA like documented [here](https://www.wezm.net/v2/posts/2023/openbsd-db-atapi-start-not-ready/)
- OpenBSD 7.4+ may fail due to this [bug](https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=278318)
- Read [afterboot manpage](https://man.openbsd.org/afterboot)
- Use `shutdown -p now` instead of `poweroff`
- To search for packages: `pkg_info -Q package`

Run:

```
fw_update -a
syspatch
pkg_add -v python3
rcctl restart sshd
```

Check:
`ansible-playbook -v -C -i inventory main.yml`

Run with:
`ansible-playbook -v -i inventory main.yml`

To upgrade to CURRENT:
`sysupgrade -s`

To upgrade packages (add `-D snap` if running CURRENT):
`pkg_add -u`
