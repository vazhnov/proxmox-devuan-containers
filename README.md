# pve-devuan-appliances

Devuan Virtual Appliances for Proxmox (LXC containers).

## Update

Proxmox will official support Devuan starting from PVE 5.1 (see: [Support for Devuan LXC container](https://bugzilla.proxmox.com/show_bug.cgi?id=1668)).

## Usage

### Use ready-to-use template

Download the [ready-to-use template](https://github.com/siddolo/pve-devuan-appliances/releases) and upload it into Proxmox using the web interface or copy it into Proxmox template directory (for example `/rpool/template/cache/` or `/var/lib/vz/template/cache`).

### Build Devuan template using DAB (Debian Appliance Builder)

```shell
cd devuan-3.0-standard-64
sudo make
```

Rename file before move into template directory.
Then move the tar.gz into proxmox template directory, for example:

```shell
mv debian-10.0-devuan-3.0-standard_1.2_amd64.tar.gz devuan-3.0-standard_1.2_amd64.tar.gz
sudo mv devuan-3.0-standard_1.2_amd64.tar.gz /var/lib/vz/template/cache/
```

## References

* https://pve.proxmox.com/wiki/Debian_Appliance_Builder
* https://bugzilla.proxmox.com/show_bug.cgi?id=1668
* https://git.proxmox.com/?p=dab-pve-appliances.git;a=blob;f=devuan-1.0-standard-64/dab.conf;h=b2c2ef7f046387beaf41215bd84c7c938fc25e6c;hb=HEAD
