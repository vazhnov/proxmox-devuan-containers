# pve-devuan-appliances

Devuan Virtual Appliances for [Proxmox Virtual Environment](https://proxmox.com/en/) (LXC containers).

## Supporting versions

Proxmox supports Devuan starting from Proxmox VE v5.1 (released 24.10.2017).

* Devuan 1 Jessie (based on Debian 8)
* Devuan 2.1 ASCII (based on Debian 9 Stretch / 2017-06)
* Devuan 3 Beowulf (based on Debian 10 Buster / 2019-07)
* Devuan 4 Chimaera (based on Debian 11 Bullseye / 2021-11)

See git repository [dab-pve-appliances](https://git.proxmox.com/?p=dab-pve-appliances.git;a=tree) for current DAB templates.

## Usage

### Build Devuan template using DAB (Debian Appliance Builder)

```shell
cd devuan-4.0-minimal-64
sudo make
```

**Rename** file **before** moving into template directory.

```shell
mv -v 'debian-11-devuan-4.0-minimal_1.0_amd64.tar.gz' "devuan-4.0-minimal_$(date +%F)_amd64.tar.gz"
```
Then move the tar.gz into proxmox template directory, for example:

```shell
sudo mv -v -- devuan-4.0-minimal_*_amd64.tar.gz '/var/lib/vz/template/cache/'
```

Then do some cleanup:

```shell
sudo make clean
```

## References

* https://pve.proxmox.com/wiki/Debian_Appliance_Builder — how to build your own application appliances
* [Support for Devuan LXC container](https://bugzilla.proxmox.com/show_bug.cgi?id=1668) — original bugreport from Pasquale Fiorillo to support Devuan 1.0
* [Support for LXC containers Devuan 2, 3 (and maybe 4)](https://bugzilla.proxmox.com/show_bug.cgi?id=3096) — next bugreport, to support fresh Devuan images
* [dab-pve-appliances](https://git.proxmox.com/?p=dab-pve-appliances.git;a=tree) — git repository with current DAB templates
