# pve-devuan-appliances

Devuan Virtual Appliances for Proxmox (LXC containers).

## Supporting versions

Proxmox supports Devuan starting from PVE 5.1 (see: [Support for Devuan LXC container](https://bugzilla.proxmox.com/show_bug.cgi?id=1668)).

* Devuan 1 Jessie (based on Debian 8)
* Devuan 2.1 ASCII (based on Debian 9 Stretch / 2017-06)
* Devuan 3 Beowulf (based on Debian 10 Buster / 2019-07)

See git repository [dab-pve-appliances](https://git.proxmox.com/?p=dab-pve-appliances.git;a=tree) for current DAB templates.

## Usage

### Use ready-to-use template

Download the [ready-to-use template](https://github.com/siddolo/pve-devuan-appliances/releases) and upload it into Proxmox using the web interface or copy it into Proxmox template directory (for example `/rpool/template/cache/` or `/var/lib/vz/template/cache`).

### Build Devuan template using DAB (Debian Appliance Builder)

```shell
cd devuan-3.0-standard-64
sudo make
```

**Rename** file **before** moving into template directory.

```shell
mv 'debian-10.0-devuan-3.0-standard_1.2_amd64.tar.gz' 'devuan-3.0-standard_1.2_amd64.tar.gz'
```
Then move the tar.gz into proxmox template directory, for example:

```shell
sudo mv 'devuan-3.0-standard_1.2_amd64.tar.gz' '/var/lib/vz/template/cache/'
```

Then do some cleanup:

```shell
sudo make clean
```

## References

* https://pve.proxmox.com/wiki/Debian\_Appliance\_Builder — how to build your own application appliances
* [Support for Devuan LXC container](https://bugzilla.proxmox.com/show_bug.cgi?id=1668) — original bugreport from Pasquale Fiorillo to support Devuan 1.0
* [Support for LXC containers Devuan 2, 3 (and maybe 4)](https://bugzilla.proxmox.com/show_bug.cgi?id=3096) — next bugreport, to support fresh Devuan images
* [dab-pve-appliances](https://git.proxmox.com/?p=dab-pve-appliances.git;a=tree) — git repository with current DAB templates
