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

### Preparation

Install `dab` ([Debian appliance builder](https://pve.proxmox.com/wiki/Debian_Appliance_Builder)) tool:

```sh
sudo apt install dab
```

#### Support for Devuan testing

Manually edit `/usr/share/perl5/PVE/LXC/Setup/Devuan.pm`:

```diff
--- /usr/share/perl5/PVE/LXC/Setup/Devuan.pm.ORIG	2022-05-04 08:36:45.000000000 +0200
+++ /usr/share/perl5/PVE/LXC/Setup/Devuan.pm	2022-06-19 21:36:59.039446517 +0200
@@ -25,6 +25,8 @@
 	'beowulf/ceres' => 10,
 	'chimaera' => 11, # Devuan 4.0
 	'chimaera/ceres' => 11,
+	'daedalus' => 12, # Devuan 5.0
+	'daedalus/ceres' => 12,
     };
     die "unsupported Devuan version '$version'\n" if !exists($version_map->{$version});
```

### Build Devuan template

Example:

```shell
git clone 'https://github.com/vazhnov/proxmox-devuan-containers.git'
cd devuan-4.0-minimal-64
sudo make
```

Rename file **before** moving into template directory:

```shell
mv -v 'devuan-4.0-minimal_1.0_amd64.tar.gz' "devuan-4.0-minimal_$(date +%F)_amd64.tar.gz"
```
Then move the tar.gz into proxmox template directory, for example:

```shell
sudo mv -v -- devuan-*_amd64.tar.gz '/var/lib/vz/template/cache/'
```

Then do some cleanup:

```shell
sudo make clean
```

## References

### Sources

* [dab-pve-appliances](https://git.proxmox.com/?p=dab-pve-appliances.git;a=tree) — git repository with current DAB templates;
* https://gitlab.com/vazhnov/proxmox-devuan-containers — this repository at GitHub;
* https://github.com/vazhnov/proxmox-devuan-containers — this repository at GitLab;
* https://github.com/siddolo/pve-devuan-appliances — original repository;

### Documentation

* https://pve.proxmox.com/wiki/Debian_Appliance_Builder — how to build your own application appliances;

### Proxmox bugzilla requests

* [Support for Devuan LXC container](https://bugzilla.proxmox.com/show_bug.cgi?id=1668) — original bugreport from Pasquale Fiorillo to support Devuan 1.0;
* [Support for LXC containers Devuan 2, 3 (and maybe 4)](https://bugzilla.proxmox.com/show_bug.cgi?id=3096) — support Devuan 2, 3, 4;
* [Support for LXC containers Devuan 5](https://bugzilla.proxmox.com/show_bug.cgi?id=4007) — next bugreport to support upcoming Devuan 5;
