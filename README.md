# ansible-openbsd

Ansible configuration for OpenBSD 7.4

NOTES:
- To create the QEMU VM change the CDROM from IDE to SATA like documented [here](https://www.wezm.net/v2/posts/2023/openbsd-db-atapi-start-not-ready/)
- Read [afterboot manpage](https://man.openbsd.org/afterboot)
- Use `shutdown -p now` instead of `poweroff`
- To search for packages: `pkg_info -Q package`

Run:

```
syspatch
pkg_add -v python3
```

Check:
`ansible-playbook -v -C -i inventory main.yml`

Run with:
`ansible-playbook -v -i inventory main.yml`

TODO

- As user:

```
cd /usr
cvs -qd anoncvs@anoncvs.ca.openbsd.org:/cvs checkout -rOPENBSD_7_4 -P src
```