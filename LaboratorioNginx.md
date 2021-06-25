## Laboratorio Nginx

>Elementos necesarios para el desarrollo del Laboratorio Nginx:

- Vagrant 2.2.16
- GIT Bash

Pasos a seguir para la creacion del Laboratio Nginx:

>1. Ingresamos via SSH a  vm_lab_1 
`````
$ vagrant ssh vm_lab_1

`````
>2. Entramos como superusuarios
`````
[vagrant@vm1 ~]$ sudo su

`````
>5. En este caso, Nginx se encuentra en el repositorio EPEL, por lo que si no lo tienes instalado aún, hazlo ahora:
`````
[root@vm1 vagrant]# yum -y install epel-release
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.ufro.cl
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
Resolving Dependencies
--> Running transaction check
---> Package epel-release.noarch 0:7-11 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                Arch             Version         Repository        Size
================================================================================
Installing:
 epel-release           noarch           7-11            extras            15 k

Transaction Summary
================================================================================
Install  1 Package

Total download size: 15 k
Installed size: 24 k
Downloading packages:
warning: /var/cache/yum/x86_64/7/extras/packages/epel-release-7-11.noarch.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
Public key for epel-release-7-11.noarch.rpm is not installed
epel-release-7-11.noarch.rpm                               |  15 kB   00:00
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-8.2003.0.el7.centos.x86_64 (@anaconda)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : epel-release-7-11.noarch                                     1/1
  Verifying  : epel-release-7-11.noarch                                     1/1

Installed:
  epel-release.noarch 0:7-11

Complete!
`````

>4. Hecho esto, incluso si ya teníamos EPEL configurado en nuestro sistema, actualizaremos la información de los repositorios y los paquetes instalados:

`````
[root@vm1 vagrant]# sudo yum update -y

Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
epel/x86_64/metalink                                                            |  14 kB  00:00:00
 * base: mirror.ufro.cl
 * epel: mirrors.upr.edu
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
epel                                                                            | 4.7 kB  00:00:00
(1/3): epel/x86_64/group_gz                                                     |  96 kB  00:00:00
(2/3): epel/x86_64/updateinfo                                                   | 1.0 MB  00:00:02
(3/3): epel/x86_64/primary_db                                                   | 6.9 MB  00:00:02
Resolving Dependencies
--> Running transaction check
---> Package NetworkManager.x86_64 1:1.18.4-3.el7 will be updated
---> Package NetworkManager.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-libnm.x86_64 1:1.18.4-3.el7 will be updated
---> Package NetworkManager-libnm.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-team.x86_64 1:1.18.4-3.el7 will be updated
---> Package NetworkManager-team.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package NetworkManager-tui.x86_64 1:1.18.4-3.el7 will be updated
---> Package NetworkManager-tui.x86_64 1:1.18.8-2.el7_9 will be an update
---> Package bind-export-libs.x86_64 32:9.11.4-16.P2.el7_8.2 will be updated
---> Package bind-export-libs.x86_64 32:9.11.4-26.P2.el7_9.5 will be an update
---> Package binutils.x86_64 0:2.27-43.base.el7 will be updated
---> Package binutils.x86_64 0:2.27-44.base.el7 will be an update
---> Package ca-certificates.noarch 0:2019.2.32-76.el7_7 will be updated
---> Package ca-certificates.noarch 0:2020.2.41-70.0.el7_8 will be an update
---> Package centos-release.x86_64 0:7-8.2003.0.el7.centos will be updated
---> Package centos-release.x86_64 0:7-9.2009.1.el7.centos will be an update
---> Package chkconfig.x86_64 0:1.7.4-1.el7 will be updated
---> Package chkconfig.x86_64 0:1.7.6-1.el7 will be an update
---> Package coreutils.x86_64 0:8.22-24.el7 will be updated
---> Package coreutils.x86_64 0:8.22-24.el7_9.2 will be an update
---> Package cpio.x86_64 0:2.11-27.el7 will be updated
---> Package cpio.x86_64 0:2.11-28.el7 will be an update
---> Package cups-libs.x86_64 1:1.6.3-43.el7 will be updated
---> Package cups-libs.x86_64 1:1.6.3-51.el7 will be an update
---> Package curl.x86_64 0:7.29.0-57.el7 will be updated
---> Package curl.x86_64 0:7.29.0-59.el7_9.1 will be an update
---> Package dbus.x86_64 1:1.10.24-13.el7_6 will be updated
---> Package dbus.x86_64 1:1.10.24-15.el7 will be an update
---> Package dbus-libs.x86_64 1:1.10.24-13.el7_6 will be updated
---> Package dbus-libs.x86_64 1:1.10.24-15.el7 will be an update
---> Package device-mapper.x86_64 7:1.02.164-7.el7_8.1 will be updated
---> Package device-mapper.x86_64 7:1.02.170-6.el7_9.5 will be an update
---> Package device-mapper-libs.x86_64 7:1.02.164-7.el7_8.1 will be updated
---> Package device-mapper-libs.x86_64 7:1.02.170-6.el7_9.5 will be an update
---> Package dhclient.x86_64 12:4.2.5-79.el7.centos will be updated
---> Package dhclient.x86_64 12:4.2.5-83.el7.centos.1 will be an update
---> Package dhcp-common.x86_64 12:4.2.5-79.el7.centos will be updated
---> Package dhcp-common.x86_64 12:4.2.5-83.el7.centos.1 will be an update
---> Package dhcp-libs.x86_64 12:4.2.5-79.el7.centos will be updated
---> Package dhcp-libs.x86_64 12:4.2.5-83.el7.centos.1 will be an update
---> Package dmidecode.x86_64 1:3.2-3.el7 will be updated
---> Package dmidecode.x86_64 1:3.2-5.el7_9.1 will be an update
---> Package dracut.x86_64 0:033-568.el7 will be updated
---> Package dracut.x86_64 0:033-572.el7 will be an update
---> Package e2fsprogs.x86_64 0:1.42.9-17.el7 will be updated
---> Package e2fsprogs.x86_64 0:1.42.9-19.el7 will be an update
---> Package e2fsprogs-libs.x86_64 0:1.42.9-17.el7 will be updated
---> Package e2fsprogs-libs.x86_64 0:1.42.9-19.el7 will be an update
---> Package elfutils-default-yama-scope.noarch 0:0.176-4.el7 will be updated
---> Package elfutils-default-yama-scope.noarch 0:0.176-5.el7 will be an update
---> Package elfutils-libelf.x86_64 0:0.176-4.el7 will be updated
---> Package elfutils-libelf.x86_64 0:0.176-5.el7 will be an update
---> Package elfutils-libs.x86_64 0:0.176-4.el7 will be updated
---> Package elfutils-libs.x86_64 0:0.176-5.el7 will be an update
---> Package epel-release.noarch 0:7-11 will be updated
---> Package epel-release.noarch 0:7-13 will be an update
---> Package expat.x86_64 0:2.1.0-11.el7 will be updated
---> Package expat.x86_64 0:2.1.0-12.el7 will be an update
---> Package file.x86_64 0:5.11-36.el7 will be updated
---> Package file.x86_64 0:5.11-37.el7 will be an update
---> Package file-libs.x86_64 0:5.11-36.el7 will be updated
---> Package file-libs.x86_64 0:5.11-37.el7 will be an update
---> Package firewalld.noarch 0:0.6.3-8.el7_8.1 will be updated
---> Package firewalld.noarch 0:0.6.3-13.el7_9 will be an update
---> Package firewalld-filesystem.noarch 0:0.6.3-8.el7_8.1 will be updated
---> Package firewalld-filesystem.noarch 0:0.6.3-13.el7_9 will be an update
---> Package freetype.x86_64 0:2.8-14.el7 will be updated
---> Package freetype.x86_64 0:2.8-14.el7_9.1 will be an update
---> Package glib2.x86_64 0:2.56.1-5.el7 will be updated
---> Package glib2.x86_64 0:2.56.1-9.el7_9 will be an update
---> Package glibc.x86_64 0:2.17-307.el7.1 will be updated
---> Package glibc.x86_64 0:2.17-324.el7_9 will be an update
---> Package glibc-common.x86_64 0:2.17-307.el7.1 will be updated
---> Package glibc-common.x86_64 0:2.17-324.el7_9 will be an update
---> Package grub2.x86_64 1:2.02-0.81.el7.centos will be updated
---> Package grub2.x86_64 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-common.noarch 1:2.02-0.81.el7.centos will be updated
---> Package grub2-common.noarch 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-pc.x86_64 1:2.02-0.81.el7.centos will be updated
---> Package grub2-pc.x86_64 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-pc-modules.noarch 1:2.02-0.81.el7.centos will be updated
---> Package grub2-pc-modules.noarch 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-tools.x86_64 1:2.02-0.81.el7.centos will be updated
---> Package grub2-tools.x86_64 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-tools-extra.x86_64 1:2.02-0.81.el7.centos will be updated
---> Package grub2-tools-extra.x86_64 1:2.02-0.87.el7.centos.6 will be an update
---> Package grub2-tools-minimal.x86_64 1:2.02-0.81.el7.centos will be updated
---> Package grub2-tools-minimal.x86_64 1:2.02-0.87.el7.centos.6 will be an update
---> Package gssproxy.x86_64 0:0.7.0-28.el7 will be updated
---> Package gssproxy.x86_64 0:0.7.0-30.el7_9 will be an update
---> Package hwdata.x86_64 0:0.252-9.5.el7 will be updated
---> Package hwdata.x86_64 0:0.252-9.7.el7 will be an update
---> Package initscripts.x86_64 0:9.49.49-1.el7 will be updated
---> Package initscripts.x86_64 0:9.49.53-1.el7_9.1 will be an update
--> Processing Dependency: bc for package: initscripts-9.49.53-1.el7_9.1.x86_64
---> Package iproute.x86_64 0:4.11.0-25.el7_7.2 will be updated
---> Package iproute.x86_64 0:4.11.0-30.el7 will be an update
---> Package iptables.x86_64 0:1.4.21-34.el7 will be updated
---> Package iptables.x86_64 0:1.4.21-35.el7 will be an update
---> Package kernel.x86_64 0:3.10.0-1160.31.1.el7 will be installed
---> Package kernel-tools.x86_64 0:3.10.0-1127.el7 will be updated
---> Package kernel-tools.x86_64 0:3.10.0-1160.31.1.el7 will be an update
---> Package kernel-tools-libs.x86_64 0:3.10.0-1127.el7 will be updated
---> Package kernel-tools-libs.x86_64 0:3.10.0-1160.31.1.el7 will be an update
---> Package kpartx.x86_64 0:0.4.9-131.el7 will be updated
---> Package kpartx.x86_64 0:0.4.9-134.el7_9 will be an update
---> Package krb5-libs.x86_64 0:1.15.1-46.el7 will be updated
---> Package krb5-libs.x86_64 0:1.15.1-50.el7 will be an update
---> Package libblkid.x86_64 0:2.23.2-63.el7 will be updated
---> Package libblkid.x86_64 0:2.23.2-65.el7_9.1 will be an update
---> Package libcom_err.x86_64 0:1.42.9-17.el7 will be updated
---> Package libcom_err.x86_64 0:1.42.9-19.el7 will be an update
---> Package libcroco.x86_64 0:0.6.12-4.el7 will be updated
---> Package libcroco.x86_64 0:0.6.12-6.el7_9 will be an update
---> Package libcurl.x86_64 0:7.29.0-57.el7 will be updated
---> Package libcurl.x86_64 0:7.29.0-59.el7_9.1 will be an update
---> Package libgcc.x86_64 0:4.8.5-39.el7 will be updated
---> Package libgcc.x86_64 0:4.8.5-44.el7 will be an update
---> Package libgomp.x86_64 0:4.8.5-39.el7 will be updated
---> Package libgomp.x86_64 0:4.8.5-44.el7 will be an update
---> Package libldb.x86_64 0:1.5.4-1.el7 will be updated
---> Package libldb.x86_64 0:1.5.4-2.el7 will be an update
---> Package libmount.x86_64 0:2.23.2-63.el7 will be updated
---> Package libmount.x86_64 0:2.23.2-65.el7_9.1 will be an update
---> Package libmspack.x86_64 0:0.5-0.7.alpha.el7 will be updated
---> Package libmspack.x86_64 0:0.5-0.8.alpha.el7 will be an update
---> Package libpng.x86_64 2:1.5.13-7.el7_2 will be updated
---> Package libpng.x86_64 2:1.5.13-8.el7 will be an update
---> Package libsmartcols.x86_64 0:2.23.2-63.el7 will be updated
---> Package libsmartcols.x86_64 0:2.23.2-65.el7_9.1 will be an update
---> Package libss.x86_64 0:1.42.9-17.el7 will be updated
---> Package libss.x86_64 0:1.42.9-19.el7 will be an update
---> Package libssh2.x86_64 0:1.8.0-3.el7 will be updated
---> Package libssh2.x86_64 0:1.8.0-4.el7 will be an update
---> Package libstdc++.x86_64 0:4.8.5-39.el7 will be updated
---> Package libstdc++.x86_64 0:4.8.5-44.el7 will be an update
---> Package libteam.x86_64 0:1.29-1.el7 will be updated
---> Package libteam.x86_64 0:1.29-3.el7 will be an update
---> Package libuuid.x86_64 0:2.23.2-63.el7 will be updated
---> Package libuuid.x86_64 0:2.23.2-65.el7_9.1 will be an update
---> Package libwbclient.x86_64 0:4.10.4-10.el7 will be updated
---> Package libwbclient.x86_64 0:4.10.16-15.el7_9 will be an update
---> Package libxml2.x86_64 0:2.9.1-6.el7.4 will be updated
---> Package libxml2.x86_64 0:2.9.1-6.el7.5 will be an update
---> Package libxml2-python.x86_64 0:2.9.1-6.el7.4 will be updated
---> Package libxml2-python.x86_64 0:2.9.1-6.el7.5 will be an update
---> Package libxslt.x86_64 0:1.1.28-5.el7 will be updated
---> Package libxslt.x86_64 0:1.1.28-6.el7 will be an update
---> Package linux-firmware.noarch 0:20191203-76.gite8a0f4c.el7 will be updated
---> Package linux-firmware.noarch 0:20200421-80.git78c0348.el7_9 will be an update
---> Package lshw.x86_64 0:B.02.18-14.el7 will be updated
---> Package lshw.x86_64 0:B.02.18-17.el7 will be an update
---> Package lz4.x86_64 0:1.7.5-3.el7 will be updated
---> Package lz4.x86_64 0:1.8.3-1.el7 will be an update
---> Package mariadb-libs.x86_64 1:5.5.65-1.el7 will be updated
---> Package mariadb-libs.x86_64 1:5.5.68-1.el7 will be an update
---> Package nettle.x86_64 0:2.7.1-8.el7 will be updated
---> Package nettle.x86_64 0:2.7.1-9.el7_9 will be an update
---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7 will be an update
---> Package nspr.x86_64 0:4.21.0-1.el7 will be updated
---> Package nspr.x86_64 0:4.25.0-2.el7_9 will be an update
---> Package nss.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-softokn.x86_64 0:3.44.0-8.el7_7 will be updated
---> Package nss-softokn.x86_64 0:3.53.1-6.el7_9 will be an update
---> Package nss-softokn-freebl.x86_64 0:3.44.0-8.el7_7 will be updated
---> Package nss-softokn-freebl.x86_64 0:3.53.1-6.el7_9 will be an update
---> Package nss-sysinit.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss-sysinit.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-tools.x86_64 0:3.44.0-7.el7_7 will be updated
---> Package nss-tools.x86_64 0:3.53.1-7.el7_9 will be an update
---> Package nss-util.x86_64 0:3.44.0-4.el7_7 will be updated
---> Package nss-util.x86_64 0:3.53.1-1.el7_9 will be an update
---> Package open-vm-tools.x86_64 0:10.3.10-2.el7 will be updated
---> Package open-vm-tools.x86_64 0:11.0.5-3.el7_9.3 will be an update
---> Package openldap.x86_64 0:2.4.44-21.el7_6 will be updated
---> Package openldap.x86_64 0:2.4.44-23.el7_9 will be an update
---> Package openssl.x86_64 1:1.0.2k-19.el7 will be updated
---> Package openssl.x86_64 1:1.0.2k-21.el7_9 will be an update
---> Package openssl-libs.x86_64 1:1.0.2k-19.el7 will be updated
---> Package openssl-libs.x86_64 1:1.0.2k-21.el7_9 will be an update
---> Package procps-ng.x86_64 0:3.3.10-27.el7 will be updated
---> Package procps-ng.x86_64 0:3.3.10-28.el7 will be an update
---> Package pyldb.x86_64 0:1.5.4-1.el7 will be updated
---> Package pyldb.x86_64 0:1.5.4-2.el7 will be an update
---> Package python.x86_64 0:2.7.5-88.el7 will be updated
---> Package python.x86_64 0:2.7.5-90.el7 will be an update
---> Package python-firewall.noarch 0:0.6.3-8.el7_8.1 will be updated
---> Package python-firewall.noarch 0:0.6.3-13.el7_9 will be an update
---> Package python-libs.x86_64 0:2.7.5-88.el7 will be updated
---> Package python-libs.x86_64 0:2.7.5-90.el7 will be an update
---> Package python-perf.x86_64 0:3.10.0-1127.el7 will be updated
---> Package python-perf.x86_64 0:3.10.0-1160.31.1.el7 will be an update
---> Package rpm.x86_64 0:4.11.3-43.el7 will be updated
---> Package rpm.x86_64 0:4.11.3-45.el7 will be an update
---> Package rpm-build-libs.x86_64 0:4.11.3-43.el7 will be updated
---> Package rpm-build-libs.x86_64 0:4.11.3-45.el7 will be an update
---> Package rpm-libs.x86_64 0:4.11.3-43.el7 will be updated
---> Package rpm-libs.x86_64 0:4.11.3-45.el7 will be an update
---> Package rpm-python.x86_64 0:4.11.3-43.el7 will be updated
---> Package rpm-python.x86_64 0:4.11.3-45.el7 will be an update
---> Package rsyslog.x86_64 0:8.24.0-52.el7 will be updated
---> Package rsyslog.x86_64 0:8.24.0-57.el7_9.1 will be an update
---> Package samba-client-libs.x86_64 0:4.10.4-10.el7 will be updated
---> Package samba-client-libs.x86_64 0:4.10.16-15.el7_9 will be an update
---> Package samba-common.noarch 0:4.10.4-10.el7 will be updated
---> Package samba-common.noarch 0:4.10.16-15.el7_9 will be an update
---> Package samba-common-libs.x86_64 0:4.10.4-10.el7 will be updated
---> Package samba-common-libs.x86_64 0:4.10.16-15.el7_9 will be an update
---> Package samba-libs.x86_64 0:4.10.4-10.el7 will be updated
---> Package samba-libs.x86_64 0:4.10.16-15.el7_9 will be an update
---> Package sed.x86_64 0:4.2.2-6.el7 will be updated
---> Package sed.x86_64 0:4.2.2-7.el7 will be an update
---> Package selinux-policy.noarch 0:3.13.1-266.el7 will be updated
---> Package selinux-policy.noarch 0:3.13.1-268.el7_9.2 will be an update
---> Package selinux-policy-targeted.noarch 0:3.13.1-266.el7 will be updated
---> Package selinux-policy-targeted.noarch 0:3.13.1-268.el7_9.2 will be an update
---> Package sudo.x86_64 0:1.8.23-9.el7 will be updated
---> Package sudo.x86_64 0:1.8.23-10.el7_9.1 will be an update
---> Package systemd.x86_64 0:219-73.el7_8.5 will be updated
---> Package systemd.x86_64 0:219-78.el7_9.3 will be an update
---> Package systemd-libs.x86_64 0:219-73.el7_8.5 will be updated
---> Package systemd-libs.x86_64 0:219-78.el7_9.3 will be an update
---> Package systemd-sysv.x86_64 0:219-73.el7_8.5 will be updated
---> Package systemd-sysv.x86_64 0:219-78.el7_9.3 will be an update
---> Package teamd.x86_64 0:1.29-1.el7 will be updated
---> Package teamd.x86_64 0:1.29-3.el7 will be an update
---> Package tuned.noarch 0:2.11.0-8.el7 will be updated
---> Package tuned.noarch 0:2.11.0-11.el7_9 will be an update
---> Package tzdata.noarch 0:2020a-1.el7 will be updated
---> Package tzdata.noarch 0:2021a-1.el7 will be an update
---> Package util-linux.x86_64 0:2.23.2-63.el7 will be updated
---> Package util-linux.x86_64 0:2.23.2-65.el7_9.1 will be an update
---> Package vim-minimal.x86_64 2:7.4.629-6.el7 will be updated
---> Package vim-minimal.x86_64 2:7.4.629-8.el7_9 will be an update
---> Package wpa_supplicant.x86_64 1:2.6-12.el7 will be updated
---> Package wpa_supplicant.x86_64 1:2.6-12.el7_9.2 will be an update
---> Package xfsprogs.x86_64 0:4.5.0-20.el7 will be updated
---> Package xfsprogs.x86_64 0:4.5.0-22.el7 will be an update
---> Package yum.noarch 0:3.4.3-167.el7.centos will be updated
---> Package yum.noarch 0:3.4.3-168.el7.centos will be an update
---> Package yum-plugin-fastestmirror.noarch 0:1.1.31-53.el7 will be updated
---> Package yum-plugin-fastestmirror.noarch 0:1.1.31-54.el7_8 will be an update
---> Package yum-utils.noarch 0:1.1.31-53.el7 will be updated
---> Package yum-utils.noarch 0:1.1.31-54.el7_8 will be an update
---> Package zlib.x86_64 0:1.2.7-18.el7 will be updated
---> Package zlib.x86_64 0:1.2.7-19.el7_9 will be an update
--> Running transaction check
---> Package bc.x86_64 0:1.06.95-13.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=======================================================================================================
 Package                           Arch         Version                            Repository     Size
=======================================================================================================
Installing:
 kernel                            x86_64       3.10.0-1160.31.1.el7               updates        50 M
Updating:
 NetworkManager                    x86_64       1:1.18.8-2.el7_9                   updates       1.9 M
 NetworkManager-libnm              x86_64       1:1.18.8-2.el7_9                   updates       1.7 M
 NetworkManager-team               x86_64       1:1.18.8-2.el7_9                   updates       165 k
 NetworkManager-tui                x86_64       1:1.18.8-2.el7_9                   updates       329 k
 bind-export-libs                  x86_64       32:9.11.4-26.P2.el7_9.5            updates       1.1 M
 binutils                          x86_64       2.27-44.base.el7                   base          5.9 M
 ca-certificates                   noarch       2020.2.41-70.0.el7_8               base          382 k
 centos-release                    x86_64       7-9.2009.1.el7.centos              updates        27 k
 chkconfig                         x86_64       1.7.6-1.el7                        base          182 k
 coreutils                         x86_64       8.22-24.el7_9.2                    updates       3.3 M
 cpio                              x86_64       2.11-28.el7                        base          211 k
 cups-libs                         x86_64       1:1.6.3-51.el7                     base          359 k
 curl                              x86_64       7.29.0-59.el7_9.1                  updates       271 k
 dbus                              x86_64       1:1.10.24-15.el7                   base          245 k
 dbus-libs                         x86_64       1:1.10.24-15.el7                   base          169 k
 device-mapper                     x86_64       7:1.02.170-6.el7_9.5               updates       297 k
 device-mapper-libs                x86_64       7:1.02.170-6.el7_9.5               updates       325 k
 dhclient                          x86_64       12:4.2.5-83.el7.centos.1           updates       286 k
 dhcp-common                       x86_64       12:4.2.5-83.el7.centos.1           updates       177 k
 dhcp-libs                         x86_64       12:4.2.5-83.el7.centos.1           updates       133 k
 dmidecode                         x86_64       1:3.2-5.el7_9.1                    updates        82 k
 dracut                            x86_64       033-572.el7                        base          329 k
 e2fsprogs                         x86_64       1.42.9-19.el7                      base          701 k
 e2fsprogs-libs                    x86_64       1.42.9-19.el7                      base          168 k
 elfutils-default-yama-scope       noarch       0.176-5.el7                        base           33 k
 elfutils-libelf                   x86_64       0.176-5.el7                        base          195 k
 elfutils-libs                     x86_64       0.176-5.el7                        base          291 k
 epel-release                      noarch       7-13                               epel           15 k
 expat                             x86_64       2.1.0-12.el7                       base           81 k
 file                              x86_64       5.11-37.el7                        base           57 k
 file-libs                         x86_64       5.11-37.el7                        base          340 k
 firewalld                         noarch       0.6.3-13.el7_9                     updates       449 k
 firewalld-filesystem              noarch       0.6.3-13.el7_9                     updates        51 k
 freetype                          x86_64       2.8-14.el7_9.1                     updates       380 k
 glib2                             x86_64       2.56.1-9.el7_9                     updates       2.5 M
 glibc                             x86_64       2.17-324.el7_9                     updates       3.6 M
 glibc-common                      x86_64       2.17-324.el7_9                     updates        12 M
 grub2                             x86_64       1:2.02-0.87.el7.centos.6           updates        34 k
 grub2-common                      noarch       1:2.02-0.87.el7.centos.6           updates       732 k
 grub2-pc                          x86_64       1:2.02-0.87.el7.centos.6           updates        34 k
 grub2-pc-modules                  noarch       1:2.02-0.87.el7.centos.6           updates       858 k
 grub2-tools                       x86_64       1:2.02-0.87.el7.centos.6           updates       1.8 M
 grub2-tools-extra                 x86_64       1:2.02-0.87.el7.centos.6           updates       1.0 M
 grub2-tools-minimal               x86_64       1:2.02-0.87.el7.centos.6           updates       177 k
 gssproxy                          x86_64       0.7.0-30.el7_9                     updates       111 k
 hwdata                            x86_64       0.252-9.7.el7                      base          2.5 M
 initscripts                       x86_64       9.49.53-1.el7_9.1                  updates       440 k
 iproute                           x86_64       4.11.0-30.el7                      base          805 k
 iptables                          x86_64       1.4.21-35.el7                      base          432 k
 kernel-tools                      x86_64       3.10.0-1160.31.1.el7               updates       8.1 M
 kernel-tools-libs                 x86_64       3.10.0-1160.31.1.el7               updates       8.0 M
 kpartx                            x86_64       0.4.9-134.el7_9                    updates        81 k
 krb5-libs                         x86_64       1.15.1-50.el7                      base          809 k
 libblkid                          x86_64       2.23.2-65.el7_9.1                  updates       183 k
 libcom_err                        x86_64       1.42.9-19.el7                      base           42 k
 libcroco                          x86_64       0.6.12-6.el7_9                     updates       105 k
 libcurl                           x86_64       7.29.0-59.el7_9.1                  updates       223 k
 libgcc                            x86_64       4.8.5-44.el7                       base          103 k
 libgomp                           x86_64       4.8.5-44.el7                       base          159 k
 libldb                            x86_64       1.5.4-2.el7                        updates       149 k
 libmount                          x86_64       2.23.2-65.el7_9.1                  updates       185 k
 libmspack                         x86_64       0.5-0.8.alpha.el7                  base           64 k
 libpng                            x86_64       2:1.5.13-8.el7                     base          213 k
 libsmartcols                      x86_64       2.23.2-65.el7_9.1                  updates       143 k
 libss                             x86_64       1.42.9-19.el7                      base           47 k
 libssh2                           x86_64       1.8.0-4.el7                        base           88 k
 libstdc++                         x86_64       4.8.5-44.el7                       base          306 k
 libteam                           x86_64       1.29-3.el7                         base           50 k
 libuuid                           x86_64       2.23.2-65.el7_9.1                  updates        84 k
 libwbclient                       x86_64       4.10.16-15.el7_9                   updates       116 k
 libxml2                           x86_64       2.9.1-6.el7.5                      base          668 k
 libxml2-python                    x86_64       2.9.1-6.el7.5                      base          247 k
 libxslt                           x86_64       1.1.28-6.el7                       base          242 k
 linux-firmware                    noarch       20200421-80.git78c0348.el7_9       updates        80 M
 lshw                              x86_64       B.02.18-17.el7                     base          324 k
 lz4                               x86_64       1.8.3-1.el7                        base           85 k
 mariadb-libs                      x86_64       1:5.5.68-1.el7                     base          760 k
 nettle                            x86_64       2.7.1-9.el7_9                      updates       328 k
 nfs-utils                         x86_64       1:1.3.0-0.68.el7                   base          412 k
 nspr                              x86_64       4.25.0-2.el7_9                     updates       127 k
 nss                               x86_64       3.53.1-7.el7_9                     updates       869 k
 nss-softokn                       x86_64       3.53.1-6.el7_9                     updates       354 k
 nss-softokn-freebl                x86_64       3.53.1-6.el7_9                     updates       322 k
 nss-sysinit                       x86_64       3.53.1-7.el7_9                     updates        66 k
 nss-tools                         x86_64       3.53.1-7.el7_9                     updates       535 k
 nss-util                          x86_64       3.53.1-1.el7_9                     updates        79 k
 open-vm-tools                     x86_64       11.0.5-3.el7_9.3                   updates       676 k
 openldap                          x86_64       2.4.44-23.el7_9                    updates       356 k
 openssl                           x86_64       1:1.0.2k-21.el7_9                  updates       493 k
 openssl-libs                      x86_64       1:1.0.2k-21.el7_9                  updates       1.2 M
 procps-ng                         x86_64       3.3.10-28.el7                      base          291 k
 pyldb                             x86_64       1.5.4-2.el7                        updates        49 k
 python                            x86_64       2.7.5-90.el7                       updates        96 k
 python-firewall                   noarch       0.6.3-13.el7_9                     updates       355 k
 python-libs                       x86_64       2.7.5-90.el7                       updates       5.6 M
 python-perf                       x86_64       3.10.0-1160.31.1.el7               updates       8.1 M
 rpm                               x86_64       4.11.3-45.el7                      base          1.2 M
 rpm-build-libs                    x86_64       4.11.3-45.el7                      base          107 k
 rpm-libs                          x86_64       4.11.3-45.el7                      base          278 k
 rpm-python                        x86_64       4.11.3-45.el7                      base           84 k
 rsyslog                           x86_64       8.24.0-57.el7_9.1                  updates       622 k
 samba-client-libs                 x86_64       4.10.16-15.el7_9                   updates       5.0 M
 samba-common                      noarch       4.10.16-15.el7_9                   updates       215 k
 samba-common-libs                 x86_64       4.10.16-15.el7_9                   updates       182 k
 samba-libs                        x86_64       4.10.16-15.el7_9                   updates       271 k
 sed                               x86_64       4.2.2-7.el7                        base          231 k
 selinux-policy                    noarch       3.13.1-268.el7_9.2                 updates       498 k
 selinux-policy-targeted           noarch       3.13.1-268.el7_9.2                 updates       7.0 M
 sudo                              x86_64       1.8.23-10.el7_9.1                  updates       843 k
 systemd                           x86_64       219-78.el7_9.3                     updates       5.1 M
 systemd-libs                      x86_64       219-78.el7_9.3                     updates       418 k
 systemd-sysv                      x86_64       219-78.el7_9.3                     updates        97 k
 teamd                             x86_64       1.29-3.el7                         base          116 k
 tuned                             noarch       2.11.0-11.el7_9                    updates       269 k
 tzdata                            noarch       2021a-1.el7                        updates       501 k
 util-linux                        x86_64       2.23.2-65.el7_9.1                  updates       2.0 M
 vim-minimal                       x86_64       2:7.4.629-8.el7_9                  updates       443 k
 wpa_supplicant                    x86_64       1:2.6-12.el7_9.2                   updates       1.2 M
 xfsprogs                          x86_64       4.5.0-22.el7                       base          897 k
 yum                               noarch       3.4.3-168.el7.centos               base          1.2 M
 yum-plugin-fastestmirror          noarch       1.1.31-54.el7_8                    base           34 k
 yum-utils                         noarch       1.1.31-54.el7_8                    base          122 k
 zlib                              x86_64       1.2.7-19.el7_9                     updates        90 k
Installing for dependencies:
 bc                                x86_64       1.06.95-13.el7                     base          115 k

Transaction Summary
=======================================================================================================
Install    1 Package  (+1 Dependent package)
Upgrade  123 Packages

Total download size: 248 M
Downloading packages:
No Presto metadata available for base
No Presto metadata available for updates
epel/x86_64/prestodelta                                                         | 1.5 kB  00:00:01
(1/125): NetworkManager-1.18.8-2.el7_9.x86_64.rpm                               | 1.9 MB  00:00:00
(2/125): NetworkManager-team-1.18.8-2.el7_9.x86_64.rpm                          | 165 kB  00:00:00
(3/125): NetworkManager-libnm-1.18.8-2.el7_9.x86_64.rpm                         | 1.7 MB  00:00:01
(4/125): NetworkManager-tui-1.18.8-2.el7_9.x86_64.rpm                           | 329 kB  00:00:00
(5/125): bind-export-libs-9.11.4-26.P2.el7_9.5.x86_64.rpm                       | 1.1 MB  00:00:00
(6/125): bc-1.06.95-13.el7.x86_64.rpm                                           | 115 kB  00:00:00
(7/125): ca-certificates-2020.2.41-70.0.el7_8.noarch.rpm                        | 382 kB  00:00:00
(8/125): centos-release-7-9.2009.1.el7.centos.x86_64.rpm                        |  27 kB  00:00:00
(9/125): chkconfig-1.7.6-1.el7.x86_64.rpm                                       | 182 kB  00:00:00
(10/125): cpio-2.11-28.el7.x86_64.rpm                                           | 211 kB  00:00:00
(11/125): cups-libs-1.6.3-51.el7.x86_64.rpm                                     | 359 kB  00:00:00
(12/125): dbus-1.10.24-15.el7.x86_64.rpm                                        | 245 kB  00:00:00
(13/125): dbus-libs-1.10.24-15.el7.x86_64.rpm                                   | 169 kB  00:00:00
(14/125): binutils-2.27-44.base.el7.x86_64.rpm                                  | 5.9 MB  00:00:02
(15/125): curl-7.29.0-59.el7_9.1.x86_64.rpm                                     | 271 kB  00:00:01
(16/125): device-mapper-1.02.170-6.el7_9.5.x86_64.rpm                           | 297 kB  00:00:00
(17/125): device-mapper-libs-1.02.170-6.el7_9.5.x86_64.rpm                      | 325 kB  00:00:00
(18/125): dhclient-4.2.5-83.el7.centos.1.x86_64.rpm                             | 286 kB  00:00:00
(19/125): coreutils-8.22-24.el7_9.2.x86_64.rpm                                  | 3.3 MB  00:00:01
(20/125): dhcp-common-4.2.5-83.el7.centos.1.x86_64.rpm                          | 177 kB  00:00:00
(21/125): dhcp-libs-4.2.5-83.el7.centos.1.x86_64.rpm                            | 133 kB  00:00:00
(22/125): dmidecode-3.2-5.el7_9.1.x86_64.rpm                                    |  82 kB  00:00:00
(23/125): dracut-033-572.el7.x86_64.rpm                                         | 329 kB  00:00:00
(24/125): e2fsprogs-libs-1.42.9-19.el7.x86_64.rpm                               | 168 kB  00:00:00
(25/125): elfutils-default-yama-scope-0.176-5.el7.noarch.rpm                    |  33 kB  00:00:00
(26/125): e2fsprogs-1.42.9-19.el7.x86_64.rpm                                    | 701 kB  00:00:00
(27/125): elfutils-libelf-0.176-5.el7.x86_64.rpm                                | 195 kB  00:00:00
(28/125): expat-2.1.0-12.el7.x86_64.rpm                                         |  81 kB  00:00:00
(29/125): elfutils-libs-0.176-5.el7.x86_64.rpm                                  | 291 kB  00:00:00
(30/125): file-5.11-37.el7.x86_64.rpm                                           |  57 kB  00:00:00
(31/125): file-libs-5.11-37.el7.x86_64.rpm                                      | 340 kB  00:00:00
(32/125): firewalld-filesystem-0.6.3-13.el7_9.noarch.rpm                        |  51 kB  00:00:00
(33/125): firewalld-0.6.3-13.el7_9.noarch.rpm                                   | 449 kB  00:00:00
warning: /var/cache/yum/x86_64/7/epel/packages/epel-release-7-13.noarch.rpm: Header V4 RSA/SHA256 Signature, key ID 352c64e5: NOKEY
Public key for epel-release-7-13.noarch.rpm is not installed
(34/125): epel-release-7-13.noarch.rpm                                          |  15 kB  00:00:00
(35/125): freetype-2.8-14.el7_9.1.x86_64.rpm                                    | 380 kB  00:00:00
(36/125): glib2-2.56.1-9.el7_9.x86_64.rpm                                       | 2.5 MB  00:00:00
(37/125): glibc-2.17-324.el7_9.x86_64.rpm                                       | 3.6 MB  00:00:01
(38/125): grub2-2.02-0.87.el7.centos.6.x86_64.rpm                               |  34 kB  00:00:00
(39/125): grub2-common-2.02-0.87.el7.centos.6.noarch.rpm                        | 732 kB  00:00:00
(40/125): grub2-pc-2.02-0.87.el7.centos.6.x86_64.rpm                            |  34 kB  00:00:00
(41/125): grub2-pc-modules-2.02-0.87.el7.centos.6.noarch.rpm                    | 858 kB  00:00:00
(42/125): grub2-tools-2.02-0.87.el7.centos.6.x86_64.rpm                         | 1.8 MB  00:00:00
(43/125): grub2-tools-extra-2.02-0.87.el7.centos.6.x86_64.rpm                   | 1.0 MB  00:00:00
(44/125): grub2-tools-minimal-2.02-0.87.el7.centos.6.x86_64.rpm                 | 177 kB  00:00:00
(45/125): gssproxy-0.7.0-30.el7_9.x86_64.rpm                                    | 111 kB  00:00:00
(46/125): glibc-common-2.17-324.el7_9.x86_64.rpm                                |  12 MB  00:00:03
(47/125): initscripts-9.49.53-1.el7_9.1.x86_64.rpm                              | 440 kB  00:00:00
(48/125): iproute-4.11.0-30.el7.x86_64.rpm                                      | 805 kB  00:00:00
(49/125): iptables-1.4.21-35.el7.x86_64.rpm                                     | 432 kB  00:00:00
(50/125): hwdata-0.252-9.7.el7.x86_64.rpm                                       | 2.5 MB  00:00:01
(51/125): kernel-tools-3.10.0-1160.31.1.el7.x86_64.rpm                          | 8.1 MB  00:00:03
(52/125): kernel-tools-libs-3.10.0-1160.31.1.el7.x86_64.rpm                     | 8.0 MB  00:00:03
(53/125): kpartx-0.4.9-134.el7_9.x86_64.rpm                                     |  81 kB  00:00:00
(54/125): libblkid-2.23.2-65.el7_9.1.x86_64.rpm                                 | 183 kB  00:00:00
(55/125): libcroco-0.6.12-6.el7_9.x86_64.rpm                                    | 105 kB  00:00:00
(56/125): libcurl-7.29.0-59.el7_9.1.x86_64.rpm                                  | 223 kB  00:00:00
(57/125): libcom_err-1.42.9-19.el7.x86_64.rpm                                   |  42 kB  00:00:00
(58/125): libgcc-4.8.5-44.el7.x86_64.rpm                                        | 103 kB  00:00:00
(59/125): krb5-libs-1.15.1-50.el7.x86_64.rpm                                    | 809 kB  00:00:01
(60/125): libmspack-0.5-0.8.alpha.el7.x86_64.rpm                                |  64 kB  00:00:00
(61/125): libpng-1.5.13-8.el7.x86_64.rpm                                        | 213 kB  00:00:00
(62/125): libldb-1.5.4-2.el7.x86_64.rpm                                         | 149 kB  00:00:00
(63/125): libss-1.42.9-19.el7.x86_64.rpm                                        |  47 kB  00:00:00
(64/125): libssh2-1.8.0-4.el7.x86_64.rpm                                        |  88 kB  00:00:00
(65/125): libstdc++-4.8.5-44.el7.x86_64.rpm                                     | 306 kB  00:00:00
(66/125): libsmartcols-2.23.2-65.el7_9.1.x86_64.rpm                             | 143 kB  00:00:00
(67/125): libteam-1.29-3.el7.x86_64.rpm                                         |  50 kB  00:00:00
(68/125): libgomp-4.8.5-44.el7.x86_64.rpm                                       | 159 kB  00:00:01
(69/125): libmount-2.23.2-65.el7_9.1.x86_64.rpm                                 | 185 kB  00:00:02
(70/125): libxml2-2.9.1-6.el7.5.x86_64.rpm                                      | 668 kB  00:00:00
(71/125): libxslt-1.1.28-6.el7.x86_64.rpm                                       | 242 kB  00:00:00
(72/125): libwbclient-4.10.16-15.el7_9.x86_64.rpm                               | 116 kB  00:00:00
(73/125): libuuid-2.23.2-65.el7_9.1.x86_64.rpm                                  |  84 kB  00:00:00
(74/125): lshw-B.02.18-17.el7.x86_64.rpm                                        | 324 kB  00:00:00
(75/125): libxml2-python-2.9.1-6.el7.5.x86_64.rpm                               | 247 kB  00:00:01
(76/125): lz4-1.8.3-1.el7.x86_64.rpm                                            |  85 kB  00:00:00
(77/125): mariadb-libs-5.5.68-1.el7.x86_64.rpm                                  | 760 kB  00:00:00
(78/125): nettle-2.7.1-9.el7_9.x86_64.rpm                                       | 328 kB  00:00:00
(79/125): nss-3.53.1-7.el7_9.x86_64.rpm                                         | 869 kB  00:00:00
(80/125): nspr-4.25.0-2.el7_9.x86_64.rpm                                        | 127 kB  00:00:00
(81/125): nss-softokn-3.53.1-6.el7_9.x86_64.rpm                                 | 354 kB  00:00:00
(82/125): nss-sysinit-3.53.1-7.el7_9.x86_64.rpm                                 |  66 kB  00:00:00
(83/125): nfs-utils-1.3.0-0.68.el7.x86_64.rpm                                   | 412 kB  00:00:01
(84/125): nss-tools-3.53.1-7.el7_9.x86_64.rpm                                   | 535 kB  00:00:00
(85/125): nss-softokn-freebl-3.53.1-6.el7_9.x86_64.rpm                          | 322 kB  00:00:01
(86/125): open-vm-tools-11.0.5-3.el7_9.3.x86_64.rpm                             | 676 kB  00:00:00
(87/125): openssl-1.0.2k-21.el7_9.x86_64.rpm                                    | 493 kB  00:00:00
(88/125): openssl-libs-1.0.2k-21.el7_9.x86_64.rpm                               | 1.2 MB  00:00:00
(89/125): nss-util-3.53.1-1.el7_9.x86_64.rpm                                    |  79 kB  00:00:01
(90/125): openldap-2.4.44-23.el7_9.x86_64.rpm                                   | 356 kB  00:00:01
(91/125): procps-ng-3.3.10-28.el7.x86_64.rpm                                    | 291 kB  00:00:00
(92/125): kernel-3.10.0-1160.31.1.el7.x86_64.rpm                                |  50 MB  00:00:15
(93/125): python-2.7.5-90.el7.x86_64.rpm                                        |  96 kB  00:00:00
(94/125): pyldb-1.5.4-2.el7.x86_64.rpm                                          |  49 kB  00:00:00
(95/125): python-firewall-0.6.3-13.el7_9.noarch.rpm                             | 355 kB  00:00:01
(96/125): rpm-build-libs-4.11.3-45.el7.x86_64.rpm                               | 107 kB  00:00:01
(97/125): rpm-4.11.3-45.el7.x86_64.rpm                                          | 1.2 MB  00:00:01
(98/125): python-libs-2.7.5-90.el7.x86_64.rpm                                   | 5.6 MB  00:00:01
(99/125): rpm-libs-4.11.3-45.el7.x86_64.rpm                                     | 278 kB  00:00:00
(100/125): rpm-python-4.11.3-45.el7.x86_64.rpm                                  |  84 kB  00:00:00
(101/125): rsyslog-8.24.0-57.el7_9.1.x86_64.rpm                                 | 622 kB  00:00:00
(102/125): samba-common-4.10.16-15.el7_9.noarch.rpm                             | 215 kB  00:00:00
(103/125): python-perf-3.10.0-1160.31.1.el7.x86_64.rpm                          | 8.1 MB  00:00:03
(104/125): samba-common-libs-4.10.16-15.el7_9.x86_64.rpm                        | 182 kB  00:00:01
(105/125): sed-4.2.2-7.el7.x86_64.rpm                                           | 231 kB  00:00:00
(106/125): samba-libs-4.10.16-15.el7_9.x86_64.rpm                               | 271 kB  00:00:00
(107/125): samba-client-libs-4.10.16-15.el7_9.x86_64.rpm                        | 5.0 MB  00:00:03
(108/125): selinux-policy-3.13.1-268.el7_9.2.noarch.rpm                         | 498 kB  00:00:01
(109/125): sudo-1.8.23-10.el7_9.1.x86_64.rpm                                    | 843 kB  00:00:01
(110/125): selinux-policy-targeted-3.13.1-268.el7_9.2.noarch.rpm                | 7.0 MB  00:00:02
(111/125): systemd-libs-219-78.el7_9.3.x86_64.rpm                               | 418 kB  00:00:01
(112/125): teamd-1.29-3.el7.x86_64.rpm                                          | 116 kB  00:00:00
(113/125): tzdata-2021a-1.el7.noarch.rpm                                        | 501 kB  00:00:00
(114/125): systemd-sysv-219-78.el7_9.3.x86_64.rpm                               |  97 kB  00:00:00
(115/125): tuned-2.11.0-11.el7_9.noarch.rpm                                     | 269 kB  00:00:00
(116/125): util-linux-2.23.2-65.el7_9.1.x86_64.rpm                              | 2.0 MB  00:00:00
(117/125): xfsprogs-4.5.0-22.el7.x86_64.rpm                                     | 897 kB  00:00:00
(118/125): systemd-219-78.el7_9.3.x86_64.rpm                                    | 5.1 MB  00:00:02
(119/125): yum-3.4.3-168.el7.centos.noarch.rpm                                  | 1.2 MB  00:00:00
(120/125): vim-minimal-7.4.629-8.el7_9.x86_64.rpm                               | 443 kB  00:00:01
(121/125): yum-utils-1.1.31-54.el7_8.noarch.rpm                                 | 122 kB  00:00:00
(122/125): zlib-1.2.7-19.el7_9.x86_64.rpm                                       |  90 kB  00:00:00
(123/125): wpa_supplicant-2.6-12.el7_9.2.x86_64.rpm                             | 1.2 MB  00:00:01
(124/125): yum-plugin-fastestmirror-1.1.31-54.el7_8.noarch.rpm                  |  34 kB  00:00:01
(125/125): linux-firmware-20200421-80.git78c0348.el7_9.noarch.rpm               |  80 MB  00:00:58
-------------------------------------------------------------------------------------------------------
Total                                                                  3.1 MB/s | 248 MB  00:01:19
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Importing GPG key 0x352C64E5:
 Userid     : "Fedora EPEL (7) <epel@fedoraproject.org>"
 Fingerprint: 91e9 7d7c 4a5e 96f1 7f3e 888f 6a2f aea2 352c 64e5
 Package    : epel-release-7-11.noarch (@extras)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : libgcc-4.8.5-44.el7.x86_64                                                        1/248
  Updating   : 1:grub2-common-2.02-0.87.el7.centos.6.noarch                                      2/248
  Updating   : centos-release-7-9.2009.1.el7.centos.x86_64                                       3/248
  Updating   : 1:grub2-pc-modules-2.02-0.87.el7.centos.6.noarch                                  4/248
  Updating   : tzdata-2021a-1.el7.noarch                                                         5/248
  Updating   : glibc-common-2.17-324.el7_9.x86_64                                                6/248
  Updating   : nss-softokn-freebl-3.53.1-6.el7_9.x86_64                                          7/248
  Updating   : glibc-2.17-324.el7_9.x86_64                                                       8/248
  Updating   : nspr-4.25.0-2.el7_9.x86_64                                                        9/248
  Updating   : nss-util-3.53.1-1.el7_9.x86_64                                                   10/248
  Updating   : zlib-1.2.7-19.el7_9.x86_64                                                       11/248
  Updating   : libcom_err-1.42.9-19.el7.x86_64                                                  12/248
  Updating   : libuuid-2.23.2-65.el7_9.1.x86_64                                                 13/248
  Updating   : sed-4.2.2-7.el7.x86_64                                                           14/248
  Updating   : elfutils-libelf-0.176-5.el7.x86_64                                               15/248
  Updating   : chkconfig-1.7.6-1.el7.x86_64                                                     16/248
  Updating   : libxml2-2.9.1-6.el7.5.x86_64                                                     17/248
  Updating   : libldb-1.5.4-2.el7.x86_64                                                        18/248
  Updating   : file-libs-5.11-37.el7.x86_64                                                     19/248
  Updating   : file-5.11-37.el7.x86_64                                                          20/248
  Updating   : libstdc++-4.8.5-44.el7.x86_64                                                    21/248
  Updating   : cpio-2.11-28.el7.x86_64                                                          22/248
  Updating   : nss-softokn-3.53.1-6.el7_9.x86_64                                                23/248
  Updating   : expat-2.1.0-12.el7.x86_64                                                        24/248
  Updating   : lz4-1.8.3-1.el7.x86_64                                                           25/248
  Updating   : iptables-1.4.21-35.el7.x86_64                                                    26/248
  Updating   : iproute-4.11.0-30.el7.x86_64                                                     27/248
  Updating   : libxslt-1.1.28-6.el7.x86_64                                                      28/248
  Updating   : e2fsprogs-libs-1.42.9-19.el7.x86_64                                              29/248
  Updating   : libss-1.42.9-19.el7.x86_64                                                       30/248
  Updating   : 2:libpng-1.5.13-8.el7.x86_64                                                     31/248
  Updating   : freetype-2.8-14.el7_9.1.x86_64                                                   32/248
  Updating   : libsmartcols-2.23.2-65.el7_9.1.x86_64                                            33/248
  Updating   : kernel-tools-libs-3.10.0-1160.31.1.el7.x86_64                                    34/248
  Updating   : 2:vim-minimal-7.4.629-8.el7_9.x86_64                                             35/248
  Installing : bc-1.06.95-13.el7.x86_64                                                         36/248
  Updating   : libmspack-0.5-0.8.alpha.el7.x86_64                                               37/248
  Updating   : libteam-1.29-3.el7.x86_64                                                        38/248
  Updating   : firewalld-filesystem-0.6.3-13.el7_9.noarch                                       39/248
  Updating   : ca-certificates-2020.2.41-70.0.el7_8.noarch                                      40/248
  Updating   : coreutils-8.22-24.el7_9.2.x86_64                                                 41/248
  Updating   : 1:openssl-libs-1.0.2k-21.el7_9.x86_64                                            42/248
  Updating   : krb5-libs-1.15.1-50.el7.x86_64                                                   43/248
  Updating   : python-libs-2.7.5-90.el7.x86_64                                                  44/248
  Updating   : python-2.7.5-90.el7.x86_64                                                       45/248
  Updating   : libblkid-2.23.2-65.el7_9.1.x86_64                                                46/248
  Updating   : libmount-2.23.2-65.el7_9.1.x86_64                                                47/248
  Updating   : glib2-2.56.1-9.el7_9.x86_64                                                      48/248
  Updating   : 1:cups-libs-1.6.3-51.el7.x86_64                                                  49/248
  Updating   : libxml2-python-2.9.1-6.el7.5.x86_64                                              50/248
  Updating   : python-firewall-0.6.3-13.el7_9.noarch                                            51/248
  Updating   : pyldb-1.5.4-2.el7.x86_64                                                         52/248
  Updating   : python-perf-3.10.0-1160.31.1.el7.x86_64                                          53/248
  Updating   : 32:bind-export-libs-9.11.4-26.P2.el7_9.5.x86_64                                  54/248
  Updating   : libssh2-1.8.0-4.el7.x86_64                                                       55/248
  Updating   : selinux-policy-3.13.1-268.el7_9.2.noarch                                         56/248
  Updating   : nss-3.53.1-7.el7_9.x86_64                                                        57/248
  Updating   : nss-sysinit-3.53.1-7.el7_9.x86_64                                                58/248
  Updating   : nss-tools-3.53.1-7.el7_9.x86_64                                                  59/248
  Updating   : libcurl-7.29.0-59.el7_9.1.x86_64                                                 60/248
  Updating   : curl-7.29.0-59.el7_9.1.x86_64                                                    61/248
  Updating   : rpm-libs-4.11.3-45.el7.x86_64                                                    62/248
  Updating   : rpm-4.11.3-45.el7.x86_64                                                         63/248
  Updating   : openldap-2.4.44-23.el7_9.x86_64                                                  64/248
  Updating   : elfutils-libs-0.176-5.el7.x86_64                                                 65/248
  Updating   : systemd-libs-219-78.el7_9.3.x86_64                                               66/248
  Updating   : 1:dbus-libs-1.10.24-15.el7.x86_64                                                67/248
  Updating   : systemd-219-78.el7_9.3.x86_64                                                    68/248
  Updating   : 1:dbus-1.10.24-15.el7.x86_64                                                     69/248
  Updating   : elfutils-default-yama-scope-0.176-5.el7.noarch                                   70/248
  Updating   : util-linux-2.23.2-65.el7_9.1.x86_64                                              71/248
  Updating   : samba-common-4.10.16-15.el7_9.noarch                                             72/248
  Updating   : libwbclient-4.10.16-15.el7_9.x86_64                                              73/248
  Updating   : samba-client-libs-4.10.16-15.el7_9.x86_64                                        74/248
  Updating   : samba-common-libs-4.10.16-15.el7_9.x86_64                                        75/248
  Updating   : 1:NetworkManager-libnm-1.18.8-2.el7_9.x86_64                                     76/248
  Updating   : procps-ng-3.3.10-28.el7.x86_64                                                   77/248
  Updating   : initscripts-9.49.53-1.el7_9.1.x86_64                                             78/248
  Updating   : 12:dhcp-libs-4.2.5-83.el7.centos.1.x86_64                                        79/248
  Updating   : 12:dhcp-common-4.2.5-83.el7.centos.1.x86_64                                      80/248
  Updating   : 7:device-mapper-1.02.170-6.el7_9.5.x86_64                                        81/248
  Updating   : 7:device-mapper-libs-1.02.170-6.el7_9.5.x86_64                                   82/248
  Updating   : 1:grub2-tools-minimal-2.02-0.87.el7.centos.6.x86_64                              83/248
  Updating   : kpartx-0.4.9-134.el7_9.x86_64                                                    84/248
  Updating   : dracut-033-572.el7.x86_64                                                        85/248
  Updating   : 1:grub2-tools-2.02-0.87.el7.centos.6.x86_64                                      86/248
  Updating   : 1:grub2-tools-extra-2.02-0.87.el7.centos.6.x86_64                                87/248
  Updating   : 1:grub2-pc-2.02-0.87.el7.centos.6.x86_64                                         88/248
  Updating   : gssproxy-0.7.0-30.el7_9.x86_64                                                   89/248
  Updating   : systemd-sysv-219-78.el7_9.3.x86_64                                               90/248
  Updating   : 1:wpa_supplicant-2.6-12.el7_9.2.x86_64                                           91/248
  Updating   : 1:NetworkManager-1.18.8-2.el7_9.x86_64                                           92/248
  Updating   : hwdata-0.252-9.7.el7.x86_64                                                      93/248
  Updating   : teamd-1.29-3.el7.x86_64                                                          94/248
  Updating   : rpm-build-libs-4.11.3-45.el7.x86_64                                              95/248
  Updating   : rpm-python-4.11.3-45.el7.x86_64                                                  96/248
  Updating   : yum-plugin-fastestmirror-1.1.31-54.el7_8.noarch                                  97/248
  Updating   : yum-3.4.3-168.el7.centos.noarch                                                  98/248
  Updating   : linux-firmware-20200421-80.git78c0348.el7_9.noarch                               99/248
  Installing : kernel-3.10.0-1160.31.1.el7.x86_64                                              100/248
  Updating   : yum-utils-1.1.31-54.el7_8.noarch                                                101/248
  Updating   : 1:NetworkManager-team-1.18.8-2.el7_9.x86_64                                     102/248
  Updating   : lshw-B.02.18-17.el7.x86_64                                                      103/248
  Updating   : 1:NetworkManager-tui-1.18.8-2.el7_9.x86_64                                      104/248
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.x86_64                                               105/248
  Updating   : 1:grub2-2.02-0.87.el7.centos.6.x86_64                                           106/248
  Updating   : 12:dhclient-4.2.5-83.el7.centos.1.x86_64                                        107/248
  Updating   : samba-libs-4.10.16-15.el7_9.x86_64                                              108/248
  Updating   : tuned-2.11.0-11.el7_9.noarch                                                    109/248
  Updating   : firewalld-0.6.3-13.el7_9.noarch                                                 110/248
  Updating   : open-vm-tools-11.0.5-3.el7_9.3.x86_64                                           111/248
  Updating   : rsyslog-8.24.0-57.el7_9.1.x86_64                                                112/248
  Updating   : sudo-1.8.23-10.el7_9.1.x86_64                                                   113/248
  Updating   : selinux-policy-targeted-3.13.1-268.el7_9.2.noarch                               114/248
  Updating   : libcroco-0.6.12-6.el7_9.x86_64                                                  115/248
  Updating   : e2fsprogs-1.42.9-19.el7.x86_64                                                  116/248
  Updating   : xfsprogs-4.5.0-22.el7.x86_64                                                    117/248
  Updating   : 1:openssl-1.0.2k-21.el7_9.x86_64                                                118/248
  Updating   : 1:mariadb-libs-5.5.68-1.el7.x86_64                                              119/248
  Updating   : binutils-2.27-44.base.el7.x86_64                                                120/248
  Updating   : kernel-tools-3.10.0-1160.31.1.el7.x86_64                                        121/248
  Updating   : 1:dmidecode-3.2-5.el7_9.1.x86_64                                                122/248
  Updating   : nettle-2.7.1-9.el7_9.x86_64                                                     123/248
  Updating   : libgomp-4.8.5-44.el7.x86_64                                                     124/248
  Updating   : epel-release-7-13.noarch                                                        125/248
  Cleanup    : 12:dhclient-4.2.5-79.el7.centos.x86_64                                          126/248
  Cleanup    : tuned-2.11.0-8.el7.noarch                                                       127/248
  Cleanup    : firewalld-0.6.3-8.el7_8.1.noarch                                                128/248
  Cleanup    : yum-utils-1.1.31-53.el7.noarch                                                  129/248
  Cleanup    : yum-3.4.3-167.el7.centos.noarch                                                 130/248
  Cleanup    : yum-plugin-fastestmirror-1.1.31-53.el7.noarch                                   131/248
  Cleanup    : selinux-policy-targeted-3.13.1-266.el7.noarch                                   132/248
  Cleanup    : selinux-policy-3.13.1-266.el7.noarch                                            133/248
  Cleanup    : python-firewall-0.6.3-8.el7_8.1.noarch                                          134/248
  Cleanup    : 12:dhcp-common-4.2.5-79.el7.centos.x86_64                                       135/248
  Cleanup    : 12:dhcp-libs-4.2.5-79.el7.centos.x86_64                                         136/248
  Cleanup    : epel-release-7-11.noarch                                                        137/248
  Cleanup    : 1:grub2-2.02-0.81.el7.centos.x86_64                                             138/248
  Cleanup    : 1:grub2-pc-2.02-0.81.el7.centos.x86_64                                          139/248
  Cleanup    : 1:grub2-pc-modules-2.02-0.81.el7.centos.noarch                                  140/248
  Cleanup    : firewalld-filesystem-0.6.3-8.el7_8.1.noarch                                     141/248
  Cleanup    : linux-firmware-20191203-76.gite8a0f4c.el7.noarch                                142/248
  Cleanup    : samba-common-libs-4.10.4-10.el7.x86_64                                          143/248
  Cleanup    : samba-libs-4.10.4-10.el7.x86_64                                                 144/248
  Cleanup    : libwbclient-4.10.4-10.el7.x86_64                                                145/248
  Cleanup    : samba-client-libs-4.10.4-10.el7.x86_64                                          146/248
  Cleanup    : open-vm-tools-10.3.10-2.el7.x86_64                                              147/248
  Cleanup    : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                               148/248
  Cleanup    : rpm-python-4.11.3-43.el7.x86_64                                                 149/248
  Cleanup    : 1:NetworkManager-tui-1.18.4-3.el7.x86_64                                        150/248
  Cleanup    : initscripts-9.49.49-1.el7.x86_64                                                151/248
  Cleanup    : 1:cups-libs-1.6.3-43.el7.x86_64                                                 152/248
  Cleanup    : rpm-build-libs-4.11.3-43.el7.x86_64                                             153/248
  Cleanup    : 1:openssl-1.0.2k-19.el7.x86_64                                                  154/248
  Cleanup    : 1:grub2-tools-extra-2.02-0.81.el7.centos.x86_64                                 155/248
  Cleanup    : 1:grub2-tools-2.02-0.81.el7.centos.x86_64                                       156/248
  Cleanup    : dracut-033-568.el7.x86_64                                                       157/248
  Cleanup    : libxml2-python-2.9.1-6.el7.4.x86_64                                             158/248
  Cleanup    : rsyslog-8.24.0-52.el7.x86_64                                                    159/248
  Cleanup    : e2fsprogs-1.42.9-17.el7.x86_64                                                  160/248
  Cleanup    : pyldb-1.5.4-1.el7.x86_64                                                        161/248
  Cleanup    : 1:NetworkManager-team-1.18.4-3.el7.x86_64                                       162/248
  Cleanup    : 1:NetworkManager-1.18.4-3.el7.x86_64                                            163/248
  Cleanup    : 1:NetworkManager-libnm-1.18.4-3.el7.x86_64                                      164/248
  Cleanup    : 1:wpa_supplicant-2.6-12.el7.x86_64                                              165/248
  Cleanup    : 1:mariadb-libs-5.5.65-1.el7.x86_64                                              166/248
  Cleanup    : gssproxy-0.7.0-28.el7.x86_64                                                    167/248
  Cleanup    : sudo-1.8.23-9.el7.x86_64                                                        168/248
  Cleanup    : file-5.11-36.el7.x86_64                                                         169/248
  Cleanup    : 32:bind-export-libs-9.11.4-16.P2.el7_8.2.x86_64                                 170/248
  Cleanup    : lshw-B.02.18-14.el7.x86_64                                                      171/248
  Cleanup    : xfsprogs-4.5.0-20.el7.x86_64                                                    172/248
  Cleanup    : binutils-2.27-43.base.el7.x86_64                                                173/248
  Cleanup    : teamd-1.29-1.el7.x86_64                                                         174/248
  Cleanup    : 1:grub2-tools-minimal-2.02-0.81.el7.centos.x86_64                               175/248
  Cleanup    : freetype-2.8-14.el7.x86_64                                                      176/248
  Cleanup    : libxslt-1.1.28-5.el7.x86_64                                                     177/248
  Cleanup    : python-perf-3.10.0-1127.el7.x86_64                                              178/248
  Cleanup    : libcroco-0.6.12-4.el7.x86_64                                                    179/248
  Cleanup    : glib2-2.56.1-5.el7.x86_64                                                       180/248
  Cleanup    : kernel-tools-3.10.0-1127.el7.x86_64                                             181/248
  Cleanup    : systemd-sysv-219-73.el7_8.5.x86_64                                              182/248
  Cleanup    : hwdata-0.252-9.5.el7.x86_64                                                     183/248
  Cleanup    : samba-common-4.10.4-10.el7.noarch                                               184/248
  Cleanup    : python-2.7.5-88.el7.x86_64                                                      185/248
  Cleanup    : python-libs-2.7.5-88.el7.x86_64                                                 186/248
  Cleanup    : libxml2-2.9.1-6.el7.4.x86_64                                                    187/248
  Cleanup    : 2:libpng-1.5.13-7.el7_2.x86_64                                                  188/248
  Cleanup    : libstdc++-4.8.5-39.el7.x86_64                                                   189/248
  Cleanup    : file-libs-5.11-36.el7.x86_64                                                    190/248
  Cleanup    : e2fsprogs-libs-1.42.9-17.el7.x86_64                                             191/248
  Cleanup    : libss-1.42.9-17.el7.x86_64                                                      192/248
  Cleanup    : kpartx-0.4.9-131.el7.x86_64                                                     193/248
  Cleanup    : 7:device-mapper-1.02.164-7.el7_8.1.x86_64                                       194/248
  Cleanup    : 7:device-mapper-libs-1.02.164-7.el7_8.1.x86_64                                  195/248
  Cleanup    : util-linux-2.23.2-63.el7.x86_64                                                 196/248
  Cleanup    : procps-ng-3.3.10-27.el7.x86_64                                                  197/248
  Cleanup    : 1:dbus-libs-1.10.24-13.el7_6.x86_64                                             198/248
  Cleanup    : systemd-libs-219-73.el7_8.5.x86_64                                              199/248
  Cleanup    : elfutils-libs-0.176-4.el7.x86_64                                                200/248
  Cleanup    : elfutils-default-yama-scope-0.176-4.el7.noarch                                  201/248
  Cleanup    : 1:dbus-1.10.24-13.el7_6.x86_64                                                  202/248
  Cleanup    : systemd-219-73.el7_8.5.x86_64                                                   203/248
  Cleanup    : curl-7.29.0-57.el7.x86_64                                                       204/248
  Cleanup    : libcurl-7.29.0-57.el7.x86_64                                                    205/248
  Cleanup    : openldap-2.4.44-21.el7_6.x86_64                                                 206/248
  Cleanup    : rpm-libs-4.11.3-43.el7.x86_64                                                   207/248
  Cleanup    : rpm-4.11.3-43.el7.x86_64                                                        208/248
  Cleanup    : nss-tools-3.44.0-7.el7_7.x86_64                                                 209/248
  Cleanup    : nss-sysinit-3.44.0-7.el7_7.x86_64                                               210/248
  Cleanup    : nss-3.44.0-7.el7_7.x86_64                                                       211/248
  Cleanup    : nss-softokn-3.44.0-8.el7_7.x86_64                                               212/248
  Cleanup    : libmount-2.23.2-63.el7.x86_64                                                   213/248
  Cleanup    : libblkid-2.23.2-63.el7.x86_64                                                   214/248
  Cleanup    : libssh2-1.8.0-3.el7.x86_64                                                      215/248
  Cleanup    : krb5-libs-1.15.1-46.el7.x86_64                                                  216/248
  Cleanup    : coreutils-8.22-24.el7.x86_64                                                    217/248
  Cleanup    : 1:openssl-libs-1.0.2k-19.el7.x86_64                                             218/248
  Cleanup    : elfutils-libelf-0.176-4.el7.x86_64                                              219/248
  Cleanup    : iproute-4.11.0-25.el7_7.2.x86_64                                                220/248
  Cleanup    : iptables-1.4.21-34.el7.x86_64                                                   221/248
  Cleanup    : zlib-1.2.7-18.el7.x86_64                                                        222/248
  Cleanup    : libcom_err-1.42.9-17.el7.x86_64                                                 223/248
  Cleanup    : sed-4.2.2-6.el7.x86_64                                                          224/248
  Cleanup    : libuuid-2.23.2-63.el7.x86_64                                                    225/248
  Cleanup    : chkconfig-1.7.4-1.el7.x86_64                                                    226/248
  Cleanup    : lz4-1.7.5-3.el7.x86_64                                                          227/248
  Cleanup    : expat-2.1.0-11.el7.x86_64                                                       228/248
  Cleanup    : libsmartcols-2.23.2-63.el7.x86_64                                               229/248
  Cleanup    : kernel-tools-libs-3.10.0-1127.el7.x86_64                                        230/248
  Cleanup    : libteam-1.29-1.el7.x86_64                                                       231/248
  Cleanup    : 2:vim-minimal-7.4.629-6.el7.x86_64                                              232/248
  Cleanup    : libldb-1.5.4-1.el7.x86_64                                                       233/248
  Cleanup    : cpio-2.11-27.el7.x86_64                                                         234/248
  Cleanup    : libmspack-0.5-0.7.alpha.el7.x86_64                                              235/248
  Cleanup    : libgomp-4.8.5-39.el7.x86_64                                                     236/248
  Cleanup    : nettle-2.7.1-8.el7.x86_64                                                       237/248
  Cleanup    : 1:dmidecode-3.2-3.el7.x86_64                                                    238/248
  Cleanup    : ca-certificates-2019.2.32-76.el7_7.noarch                                       239/248
  Cleanup    : centos-release-7-8.2003.0.el7.centos.x86_64                                     240/248
  Cleanup    : 1:grub2-common-2.02-0.81.el7.centos.noarch                                      241/248
  Cleanup    : glibc-common-2.17-307.el7.1.x86_64                                              242/248
  Cleanup    : nspr-4.21.0-1.el7.x86_64                                                        243/248
  Cleanup    : nss-util-3.44.0-4.el7_7.x86_64                                                  244/248
  Cleanup    : nss-softokn-freebl-3.44.0-8.el7_7.x86_64                                        245/248
  Cleanup    : glibc-2.17-307.el7.1.x86_64                                                     246/248
  Cleanup    : tzdata-2020a-1.el7.noarch                                                       247/248
  Cleanup    : libgcc-4.8.5-39.el7.x86_64                                                      248/248
  Verifying  : 1:grub2-2.02-0.87.el7.centos.6.x86_64                                             1/248
  Verifying  : libcurl-7.29.0-59.el7_9.1.x86_64                                                  2/248
  Verifying  : libblkid-2.23.2-65.el7_9.1.x86_64                                                 3/248
  Verifying  : linux-firmware-20200421-80.git78c0348.el7_9.noarch                                4/248
  Verifying  : nss-util-3.53.1-1.el7_9.x86_64                                                    5/248
  Verifying  : selinux-policy-targeted-3.13.1-268.el7_9.2.noarch                                 6/248
  Verifying  : samba-client-libs-4.10.16-15.el7_9.x86_64                                         7/248
  Verifying  : 32:bind-export-libs-9.11.4-26.P2.el7_9.5.x86_64                                   8/248
  Verifying  : libssh2-1.8.0-4.el7.x86_64                                                        9/248
  Verifying  : glibc-common-2.17-324.el7_9.x86_64                                               10/248
  Verifying  : 1:NetworkManager-tui-1.18.8-2.el7_9.x86_64                                       11/248
  Verifying  : centos-release-7-9.2009.1.el7.centos.x86_64                                      12/248
  Verifying  : libsmartcols-2.23.2-65.el7_9.1.x86_64                                            13/248
  Verifying  : firewalld-0.6.3-13.el7_9.noarch                                                  14/248
  Verifying  : 1:openssl-1.0.2k-21.el7_9.x86_64                                                 15/248
  Verifying  : 1:mariadb-libs-5.5.68-1.el7.x86_64                                               16/248
  Verifying  : libwbclient-4.10.16-15.el7_9.x86_64                                              17/248
  Verifying  : util-linux-2.23.2-65.el7_9.1.x86_64                                              18/248
  Verifying  : 1:NetworkManager-libnm-1.18.8-2.el7_9.x86_64                                     19/248
  Verifying  : samba-libs-4.10.16-15.el7_9.x86_64                                               20/248
  Verifying  : 1:NetworkManager-team-1.18.8-2.el7_9.x86_64                                      21/248
  Verifying  : 1:dmidecode-3.2-5.el7_9.1.x86_64                                                 22/248
  Verifying  : selinux-policy-3.13.1-268.el7_9.2.noarch                                         23/248
  Verifying  : kernel-tools-libs-3.10.0-1160.31.1.el7.x86_64                                    24/248
  Verifying  : 1:openssl-libs-1.0.2k-21.el7_9.x86_64                                            25/248
  Verifying  : python-libs-2.7.5-90.el7.x86_64                                                  26/248
  Verifying  : procps-ng-3.3.10-28.el7.x86_64                                                   27/248
  Verifying  : libxml2-python-2.9.1-6.el7.5.x86_64                                              28/248
  Verifying  : 1:grub2-tools-minimal-2.02-0.87.el7.centos.6.x86_64                              29/248
  Verifying  : 7:device-mapper-1.02.170-6.el7_9.5.x86_64                                        30/248
  Verifying  : ca-certificates-2020.2.41-70.0.el7_8.noarch                                      31/248
  Verifying  : freetype-2.8-14.el7_9.1.x86_64                                                   32/248
  Verifying  : libgcc-4.8.5-44.el7.x86_64                                                       33/248
  Verifying  : file-5.11-37.el7.x86_64                                                          34/248
  Verifying  : gssproxy-0.7.0-30.el7_9.x86_64                                                   35/248
  Verifying  : kernel-3.10.0-1160.31.1.el7.x86_64                                               36/248
  Verifying  : 1:grub2-pc-2.02-0.87.el7.centos.6.x86_64                                         37/248
  Verifying  : kpartx-0.4.9-134.el7_9.x86_64                                                    38/248
  Verifying  : chkconfig-1.7.6-1.el7.x86_64                                                     39/248
  Verifying  : e2fsprogs-1.42.9-19.el7.x86_64                                                   40/248
  Verifying  : e2fsprogs-libs-1.42.9-19.el7.x86_64                                              41/248
  Verifying  : elfutils-default-yama-scope-0.176-5.el7.noarch                                   42/248
  Verifying  : libmount-2.23.2-65.el7_9.1.x86_64                                                43/248
  Verifying  : dracut-033-572.el7.x86_64                                                        44/248
  Verifying  : 1:dbus-libs-1.10.24-15.el7.x86_64                                                45/248
  Verifying  : 1:cups-libs-1.6.3-51.el7.x86_64                                                  46/248
  Verifying  : kernel-tools-3.10.0-1160.31.1.el7.x86_64                                         47/248
  Verifying  : libldb-1.5.4-2.el7.x86_64                                                        48/248
  Verifying  : systemd-sysv-219-78.el7_9.3.x86_64                                               49/248
  Verifying  : expat-2.1.0-12.el7.x86_64                                                        50/248
  Verifying  : epel-release-7-13.noarch                                                         51/248
  Verifying  : open-vm-tools-11.0.5-3.el7_9.3.x86_64                                            52/248
  Verifying  : 12:dhcp-libs-4.2.5-83.el7.centos.1.x86_64                                        53/248
  Verifying  : rpm-4.11.3-45.el7.x86_64                                                         54/248
  Verifying  : nss-softokn-freebl-3.53.1-6.el7_9.x86_64                                         55/248
  Verifying  : nss-softokn-3.53.1-6.el7_9.x86_64                                                56/248
  Verifying  : 1:grub2-tools-extra-2.02-0.87.el7.centos.6.x86_64                                57/248
  Verifying  : rpm-python-4.11.3-45.el7.x86_64                                                  58/248
  Verifying  : curl-7.29.0-59.el7_9.1.x86_64                                                    59/248
  Verifying  : nettle-2.7.1-9.el7_9.x86_64                                                      60/248
  Verifying  : 2:vim-minimal-7.4.629-8.el7_9.x86_64                                             61/248
  Verifying  : krb5-libs-1.15.1-50.el7.x86_64                                                   62/248
  Verifying  : libuuid-2.23.2-65.el7_9.1.x86_64                                                 63/248
  Verifying  : teamd-1.29-3.el7.x86_64                                                          64/248
  Verifying  : zlib-1.2.7-19.el7_9.x86_64                                                       65/248
  Verifying  : rpm-build-libs-4.11.3-45.el7.x86_64                                              66/248
  Verifying  : python-2.7.5-90.el7.x86_64                                                       67/248
  Verifying  : glibc-2.17-324.el7_9.x86_64                                                      68/248
  Verifying  : binutils-2.27-44.base.el7.x86_64                                                 69/248
  Verifying  : 1:nfs-utils-1.3.0-0.68.el7.x86_64                                                70/248
  Verifying  : nspr-4.25.0-2.el7_9.x86_64                                                       71/248
  Verifying  : yum-plugin-fastestmirror-1.1.31-54.el7_8.noarch                                  72/248
  Verifying  : python-firewall-0.6.3-13.el7_9.noarch                                            73/248
  Verifying  : 7:device-mapper-libs-1.02.170-6.el7_9.5.x86_64                                   74/248
  Verifying  : bc-1.06.95-13.el7.x86_64                                                         75/248
  Verifying  : libxml2-2.9.1-6.el7.5.x86_64                                                     76/248
  Verifying  : libmspack-0.5-0.8.alpha.el7.x86_64                                               77/248
  Verifying  : 1:grub2-common-2.02-0.87.el7.centos.6.noarch                                     78/248
  Verifying  : nss-3.53.1-7.el7_9.x86_64                                                        79/248
  Verifying  : xfsprogs-4.5.0-22.el7.x86_64                                                     80/248
  Verifying  : openldap-2.4.44-23.el7_9.x86_64                                                  81/248
  Verifying  : file-libs-5.11-37.el7.x86_64                                                     82/248
  Verifying  : coreutils-8.22-24.el7_9.2.x86_64                                                 83/248
  Verifying  : 2:libpng-1.5.13-8.el7.x86_64                                                     84/248
  Verifying  : 1:wpa_supplicant-2.6-12.el7_9.2.x86_64                                           85/248
  Verifying  : pyldb-1.5.4-2.el7.x86_64                                                         86/248
  Verifying  : libstdc++-4.8.5-44.el7.x86_64                                                    87/248
  Verifying  : samba-common-libs-4.10.16-15.el7_9.x86_64                                        88/248
  Verifying  : samba-common-4.10.16-15.el7_9.noarch                                             89/248
  Verifying  : nss-tools-3.53.1-7.el7_9.x86_64                                                  90/248
  Verifying  : lz4-1.8.3-1.el7.x86_64                                                           91/248
  Verifying  : rsyslog-8.24.0-57.el7_9.1.x86_64                                                 92/248
  Verifying  : 12:dhclient-4.2.5-83.el7.centos.1.x86_64                                         93/248
  Verifying  : hwdata-0.252-9.7.el7.x86_64                                                      94/248
  Verifying  : 12:dhcp-common-4.2.5-83.el7.centos.1.x86_64                                      95/248
  Verifying  : glib2-2.56.1-9.el7_9.x86_64                                                      96/248
  Verifying  : systemd-libs-219-78.el7_9.3.x86_64                                               97/248
  Verifying  : 1:dbus-1.10.24-15.el7.x86_64                                                     98/248
  Verifying  : libcom_err-1.42.9-19.el7.x86_64                                                  99/248
  Verifying  : libcroco-0.6.12-6.el7_9.x86_64                                                  100/248
  Verifying  : libteam-1.29-3.el7.x86_64                                                       101/248
  Verifying  : systemd-219-78.el7_9.3.x86_64                                                   102/248
  Verifying  : sudo-1.8.23-10.el7_9.1.x86_64                                                   103/248
  Verifying  : iproute-4.11.0-30.el7.x86_64                                                    104/248
  Verifying  : firewalld-filesystem-0.6.3-13.el7_9.noarch                                      105/248
  Verifying  : nss-sysinit-3.53.1-7.el7_9.x86_64                                               106/248
  Verifying  : yum-utils-1.1.31-54.el7_8.noarch                                                107/248
  Verifying  : 1:NetworkManager-1.18.8-2.el7_9.x86_64                                          108/248
  Verifying  : 1:grub2-pc-modules-2.02-0.87.el7.centos.6.noarch                                109/248
  Verifying  : tuned-2.11.0-11.el7_9.noarch                                                    110/248
  Verifying  : rpm-libs-4.11.3-45.el7.x86_64                                                   111/248
  Verifying  : sed-4.2.2-7.el7.x86_64                                                          112/248
  Verifying  : python-perf-3.10.0-1160.31.1.el7.x86_64                                         113/248
  Verifying  : libss-1.42.9-19.el7.x86_64                                                      114/248
  Verifying  : cpio-2.11-28.el7.x86_64                                                         115/248
  Verifying  : 1:grub2-tools-2.02-0.87.el7.centos.6.x86_64                                     116/248
  Verifying  : initscripts-9.49.53-1.el7_9.1.x86_64                                            117/248
  Verifying  : yum-3.4.3-168.el7.centos.noarch                                                 118/248
  Verifying  : libgomp-4.8.5-44.el7.x86_64                                                     119/248
  Verifying  : libxslt-1.1.28-6.el7.x86_64                                                     120/248
  Verifying  : iptables-1.4.21-35.el7.x86_64                                                   121/248
  Verifying  : lshw-B.02.18-17.el7.x86_64                                                      122/248
  Verifying  : tzdata-2021a-1.el7.noarch                                                       123/248
  Verifying  : elfutils-libelf-0.176-5.el7.x86_64                                              124/248
  Verifying  : elfutils-libs-0.176-5.el7.x86_64                                                125/248
  Verifying  : 1:grub2-tools-2.02-0.81.el7.centos.x86_64                                       126/248
  Verifying  : kpartx-0.4.9-131.el7.x86_64                                                     127/248
  Verifying  : centos-release-7-8.2003.0.el7.centos.x86_64                                     128/248
  Verifying  : nss-3.44.0-7.el7_7.x86_64                                                       129/248
  Verifying  : libssh2-1.8.0-3.el7.x86_64                                                      130/248
  Verifying  : python-2.7.5-88.el7.x86_64                                                      131/248
  Verifying  : freetype-2.8-14.el7.x86_64                                                      132/248
  Verifying  : libxml2-python-2.9.1-6.el7.4.x86_64                                             133/248
  Verifying  : libmount-2.23.2-63.el7.x86_64                                                   134/248
  Verifying  : rpm-build-libs-4.11.3-43.el7.x86_64                                             135/248
  Verifying  : elfutils-libs-0.176-4.el7.x86_64                                                136/248
  Verifying  : epel-release-7-11.noarch                                                        137/248
  Verifying  : zlib-1.2.7-18.el7.x86_64                                                        138/248
  Verifying  : util-linux-2.23.2-63.el7.x86_64                                                 139/248
  Verifying  : 7:device-mapper-libs-1.02.164-7.el7_8.1.x86_64                                  140/248
  Verifying  : ca-certificates-2019.2.32-76.el7_7.noarch                                       141/248
  Verifying  : sed-4.2.2-6.el7.x86_64                                                          142/248
  Verifying  : selinux-policy-3.13.1-266.el7.noarch                                            143/248
  Verifying  : lz4-1.7.5-3.el7.x86_64                                                          144/248
  Verifying  : 12:dhcp-common-4.2.5-79.el7.centos.x86_64                                       145/248
  Verifying  : initscripts-9.49.49-1.el7.x86_64                                                146/248
  Verifying  : 1:openssl-libs-1.0.2k-19.el7.x86_64                                             147/248
  Verifying  : kernel-tools-libs-3.10.0-1127.el7.x86_64                                        148/248
  Verifying  : yum-utils-1.1.31-53.el7.noarch                                                  149/248
  Verifying  : python-perf-3.10.0-1127.el7.x86_64                                              150/248
  Verifying  : libsmartcols-2.23.2-63.el7.x86_64                                               151/248
  Verifying  : 1:grub2-tools-extra-2.02-0.81.el7.centos.x86_64                                 152/248
  Verifying  : chkconfig-1.7.4-1.el7.x86_64                                                    153/248
  Verifying  : libmspack-0.5-0.7.alpha.el7.x86_64                                              154/248
  Verifying  : 1:grub2-tools-minimal-2.02-0.81.el7.centos.x86_64                               155/248
  Verifying  : systemd-219-73.el7_8.5.x86_64                                                   156/248
  Verifying  : samba-common-4.10.4-10.el7.noarch                                               157/248
  Verifying  : 2:libpng-1.5.13-7.el7_2.x86_64                                                  158/248
  Verifying  : libldb-1.5.4-1.el7.x86_64                                                       159/248
  Verifying  : nss-tools-3.44.0-7.el7_7.x86_64                                                 160/248
  Verifying  : 1:cups-libs-1.6.3-43.el7.x86_64                                                 161/248
  Verifying  : systemd-libs-219-73.el7_8.5.x86_64                                              162/248
  Verifying  : 1:wpa_supplicant-2.6-12.el7.x86_64                                              163/248
  Verifying  : nettle-2.7.1-8.el7.x86_64                                                       164/248
  Verifying  : libstdc++-4.8.5-39.el7.x86_64                                                   165/248
  Verifying  : iproute-4.11.0-25.el7_7.2.x86_64                                                166/248
  Verifying  : glib2-2.56.1-5.el7.x86_64                                                       167/248
  Verifying  : dracut-033-568.el7.x86_64                                                       168/248
  Verifying  : yum-3.4.3-167.el7.centos.noarch                                                 169/248
  Verifying  : open-vm-tools-10.3.10-2.el7.x86_64                                              170/248
  Verifying  : 2:vim-minimal-7.4.629-6.el7.x86_64                                              171/248
  Verifying  : samba-common-libs-4.10.4-10.el7.x86_64                                          172/248
  Verifying  : libteam-1.29-1.el7.x86_64                                                       173/248
  Verifying  : libgcc-4.8.5-39.el7.x86_64                                                      174/248
  Verifying  : samba-client-libs-4.10.4-10.el7.x86_64                                          175/248
  Verifying  : nss-sysinit-3.44.0-7.el7_7.x86_64                                               176/248
  Verifying  : firewalld-0.6.3-8.el7_8.1.noarch                                                177/248
  Verifying  : 1:openssl-1.0.2k-19.el7.x86_64                                                  178/248
  Verifying  : 1:NetworkManager-libnm-1.18.4-3.el7.x86_64                                      179/248
  Verifying  : elfutils-libelf-0.176-4.el7.x86_64                                              180/248
  Verifying  : 7:device-mapper-1.02.164-7.el7_8.1.x86_64                                       181/248
  Verifying  : tzdata-2020a-1.el7.noarch                                                       182/248
  Verifying  : selinux-policy-targeted-3.13.1-266.el7.noarch                                   183/248
  Verifying  : rpm-python-4.11.3-43.el7.x86_64                                                 184/248
  Verifying  : file-5.11-36.el7.x86_64                                                         185/248
  Verifying  : firewalld-filesystem-0.6.3-8.el7_8.1.noarch                                     186/248
  Verifying  : python-libs-2.7.5-88.el7.x86_64                                                 187/248
  Verifying  : nspr-4.21.0-1.el7.x86_64                                                        188/248
  Verifying  : nss-softokn-freebl-3.44.0-8.el7_7.x86_64                                        189/248
  Verifying  : openldap-2.4.44-21.el7_6.x86_64                                                 190/248
  Verifying  : nss-softokn-3.44.0-8.el7_7.x86_64                                               191/248
  Verifying  : samba-libs-4.10.4-10.el7.x86_64                                                 192/248
  Verifying  : tuned-2.11.0-8.el7.noarch                                                       193/248
  Verifying  : rsyslog-8.24.0-52.el7.x86_64                                                    194/248
  Verifying  : 1:dmidecode-3.2-3.el7.x86_64                                                    195/248
  Verifying  : libcom_err-1.42.9-17.el7.x86_64                                                 196/248
  Verifying  : gssproxy-0.7.0-28.el7.x86_64                                                    197/248
  Verifying  : cpio-2.11-27.el7.x86_64                                                         198/248
  Verifying  : libcurl-7.29.0-57.el7.x86_64                                                    199/248
  Verifying  : file-libs-5.11-36.el7.x86_64                                                    200/248
  Verifying  : procps-ng-3.3.10-27.el7.x86_64                                                  201/248
  Verifying  : libcroco-0.6.12-4.el7.x86_64                                                    202/248
  Verifying  : iptables-1.4.21-34.el7.x86_64                                                   203/248
  Verifying  : libxml2-2.9.1-6.el7.4.x86_64                                                    204/248
  Verifying  : 1:grub2-2.02-0.81.el7.centos.x86_64                                             205/248
  Verifying  : e2fsprogs-1.42.9-17.el7.x86_64                                                  206/248
  Verifying  : glibc-common-2.17-307.el7.1.x86_64                                              207/248
  Verifying  : libgomp-4.8.5-39.el7.x86_64                                                     208/248
  Verifying  : 1:NetworkManager-tui-1.18.4-3.el7.x86_64                                        209/248
  Verifying  : 32:bind-export-libs-9.11.4-16.P2.el7_8.2.x86_64                                 210/248
  Verifying  : libblkid-2.23.2-63.el7.x86_64                                                   211/248
  Verifying  : glibc-2.17-307.el7.1.x86_64                                                     212/248
  Verifying  : e2fsprogs-libs-1.42.9-17.el7.x86_64                                             213/248
  Verifying  : 1:dbus-libs-1.10.24-13.el7_6.x86_64                                             214/248
  Verifying  : hwdata-0.252-9.5.el7.x86_64                                                     215/248
  Verifying  : 1:grub2-pc-modules-2.02-0.81.el7.centos.noarch                                  216/248
  Verifying  : 1:NetworkManager-1.18.4-3.el7.x86_64                                            217/248
  Verifying  : coreutils-8.22-24.el7.x86_64                                                    218/248
  Verifying  : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                               219/248
  Verifying  : python-firewall-0.6.3-8.el7_8.1.noarch                                          220/248
  Verifying  : 12:dhcp-libs-4.2.5-79.el7.centos.x86_64                                         221/248
  Verifying  : 1:mariadb-libs-5.5.65-1.el7.x86_64                                              222/248
  Verifying  : rpm-libs-4.11.3-43.el7.x86_64                                                   223/248
  Verifying  : yum-plugin-fastestmirror-1.1.31-53.el7.noarch                                   224/248
  Verifying  : 12:dhclient-4.2.5-79.el7.centos.x86_64                                          225/248
  Verifying  : 1:NetworkManager-team-1.18.4-3.el7.x86_64                                       226/248
  Verifying  : 1:grub2-pc-2.02-0.81.el7.centos.x86_64                                          227/248
  Verifying  : 1:grub2-common-2.02-0.81.el7.centos.noarch                                      228/248
  Verifying  : rpm-4.11.3-43.el7.x86_64                                                        229/248
  Verifying  : krb5-libs-1.15.1-46.el7.x86_64                                                  230/248
  Verifying  : curl-7.29.0-57.el7.x86_64                                                       231/248
  Verifying  : 1:dbus-1.10.24-13.el7_6.x86_64                                                  232/248
  Verifying  : linux-firmware-20191203-76.gite8a0f4c.el7.noarch                                233/248
  Verifying  : elfutils-default-yama-scope-0.176-4.el7.noarch                                  234/248
  Verifying  : libwbclient-4.10.4-10.el7.x86_64                                                235/248
  Verifying  : pyldb-1.5.4-1.el7.x86_64                                                        236/248
  Verifying  : binutils-2.27-43.base.el7.x86_64                                                237/248
  Verifying  : kernel-tools-3.10.0-1127.el7.x86_64                                             238/248
  Verifying  : libxslt-1.1.28-5.el7.x86_64                                                     239/248
  Verifying  : systemd-sysv-219-73.el7_8.5.x86_64                                              240/248
  Verifying  : libuuid-2.23.2-63.el7.x86_64                                                    241/248
  Verifying  : libss-1.42.9-17.el7.x86_64                                                      242/248
  Verifying  : sudo-1.8.23-9.el7.x86_64                                                        243/248
  Verifying  : lshw-B.02.18-14.el7.x86_64                                                      244/248
  Verifying  : expat-2.1.0-11.el7.x86_64                                                       245/248
  Verifying  : xfsprogs-4.5.0-20.el7.x86_64                                                    246/248
  Verifying  : nss-util-3.44.0-4.el7_7.x86_64                                                  247/248
  Verifying  : teamd-1.29-1.el7.x86_64                                                         248/248

Installed:
  kernel.x86_64 0:3.10.0-1160.31.1.el7

Dependency Installed:
  bc.x86_64 0:1.06.95-13.el7

Updated:
  NetworkManager.x86_64 1:1.18.8-2.el7_9
  NetworkManager-libnm.x86_64 1:1.18.8-2.el7_9
  NetworkManager-team.x86_64 1:1.18.8-2.el7_9
  NetworkManager-tui.x86_64 1:1.18.8-2.el7_9
  bind-export-libs.x86_64 32:9.11.4-26.P2.el7_9.5
  binutils.x86_64 0:2.27-44.base.el7
  ca-certificates.noarch 0:2020.2.41-70.0.el7_8
  centos-release.x86_64 0:7-9.2009.1.el7.centos
  chkconfig.x86_64 0:1.7.6-1.el7
  coreutils.x86_64 0:8.22-24.el7_9.2
  cpio.x86_64 0:2.11-28.el7
  cups-libs.x86_64 1:1.6.3-51.el7
  curl.x86_64 0:7.29.0-59.el7_9.1
  dbus.x86_64 1:1.10.24-15.el7
  dbus-libs.x86_64 1:1.10.24-15.el7
  device-mapper.x86_64 7:1.02.170-6.el7_9.5
  device-mapper-libs.x86_64 7:1.02.170-6.el7_9.5
  dhclient.x86_64 12:4.2.5-83.el7.centos.1
  dhcp-common.x86_64 12:4.2.5-83.el7.centos.1
  dhcp-libs.x86_64 12:4.2.5-83.el7.centos.1
  dmidecode.x86_64 1:3.2-5.el7_9.1
  dracut.x86_64 0:033-572.el7
  e2fsprogs.x86_64 0:1.42.9-19.el7
  e2fsprogs-libs.x86_64 0:1.42.9-19.el7
  elfutils-default-yama-scope.noarch 0:0.176-5.el7
  elfutils-libelf.x86_64 0:0.176-5.el7
  elfutils-libs.x86_64 0:0.176-5.el7
  epel-release.noarch 0:7-13
  expat.x86_64 0:2.1.0-12.el7
  file.x86_64 0:5.11-37.el7
  file-libs.x86_64 0:5.11-37.el7
  firewalld.noarch 0:0.6.3-13.el7_9
  firewalld-filesystem.noarch 0:0.6.3-13.el7_9
  freetype.x86_64 0:2.8-14.el7_9.1
  glib2.x86_64 0:2.56.1-9.el7_9
  glibc.x86_64 0:2.17-324.el7_9
  glibc-common.x86_64 0:2.17-324.el7_9
  grub2.x86_64 1:2.02-0.87.el7.centos.6
  grub2-common.noarch 1:2.02-0.87.el7.centos.6
  grub2-pc.x86_64 1:2.02-0.87.el7.centos.6
  grub2-pc-modules.noarch 1:2.02-0.87.el7.centos.6
  grub2-tools.x86_64 1:2.02-0.87.el7.centos.6
  grub2-tools-extra.x86_64 1:2.02-0.87.el7.centos.6
  grub2-tools-minimal.x86_64 1:2.02-0.87.el7.centos.6
  gssproxy.x86_64 0:0.7.0-30.el7_9
  hwdata.x86_64 0:0.252-9.7.el7
  initscripts.x86_64 0:9.49.53-1.el7_9.1
  iproute.x86_64 0:4.11.0-30.el7
  iptables.x86_64 0:1.4.21-35.el7
  kernel-tools.x86_64 0:3.10.0-1160.31.1.el7
  kernel-tools-libs.x86_64 0:3.10.0-1160.31.1.el7
  kpartx.x86_64 0:0.4.9-134.el7_9
  krb5-libs.x86_64 0:1.15.1-50.el7
  libblkid.x86_64 0:2.23.2-65.el7_9.1
  libcom_err.x86_64 0:1.42.9-19.el7
  libcroco.x86_64 0:0.6.12-6.el7_9
  libcurl.x86_64 0:7.29.0-59.el7_9.1
  libgcc.x86_64 0:4.8.5-44.el7
  libgomp.x86_64 0:4.8.5-44.el7
  libldb.x86_64 0:1.5.4-2.el7
  libmount.x86_64 0:2.23.2-65.el7_9.1
  libmspack.x86_64 0:0.5-0.8.alpha.el7
  libpng.x86_64 2:1.5.13-8.el7
  libsmartcols.x86_64 0:2.23.2-65.el7_9.1
  libss.x86_64 0:1.42.9-19.el7
  libssh2.x86_64 0:1.8.0-4.el7
  libstdc++.x86_64 0:4.8.5-44.el7
  libteam.x86_64 0:1.29-3.el7
  libuuid.x86_64 0:2.23.2-65.el7_9.1
  libwbclient.x86_64 0:4.10.16-15.el7_9
  libxml2.x86_64 0:2.9.1-6.el7.5
  libxml2-python.x86_64 0:2.9.1-6.el7.5
  libxslt.x86_64 0:1.1.28-6.el7
  linux-firmware.noarch 0:20200421-80.git78c0348.el7_9
  lshw.x86_64 0:B.02.18-17.el7
  lz4.x86_64 0:1.8.3-1.el7
  mariadb-libs.x86_64 1:5.5.68-1.el7
  nettle.x86_64 0:2.7.1-9.el7_9
  nfs-utils.x86_64 1:1.3.0-0.68.el7
  nspr.x86_64 0:4.25.0-2.el7_9
  nss.x86_64 0:3.53.1-7.el7_9
  nss-softokn.x86_64 0:3.53.1-6.el7_9
  nss-softokn-freebl.x86_64 0:3.53.1-6.el7_9
  nss-sysinit.x86_64 0:3.53.1-7.el7_9
  nss-tools.x86_64 0:3.53.1-7.el7_9
  nss-util.x86_64 0:3.53.1-1.el7_9
  open-vm-tools.x86_64 0:11.0.5-3.el7_9.3
  openldap.x86_64 0:2.4.44-23.el7_9
  openssl.x86_64 1:1.0.2k-21.el7_9
  openssl-libs.x86_64 1:1.0.2k-21.el7_9
  procps-ng.x86_64 0:3.3.10-28.el7
  pyldb.x86_64 0:1.5.4-2.el7
  python.x86_64 0:2.7.5-90.el7
  python-firewall.noarch 0:0.6.3-13.el7_9
  python-libs.x86_64 0:2.7.5-90.el7
  python-perf.x86_64 0:3.10.0-1160.31.1.el7
  rpm.x86_64 0:4.11.3-45.el7
  rpm-build-libs.x86_64 0:4.11.3-45.el7
  rpm-libs.x86_64 0:4.11.3-45.el7
  rpm-python.x86_64 0:4.11.3-45.el7
  rsyslog.x86_64 0:8.24.0-57.el7_9.1
  samba-client-libs.x86_64 0:4.10.16-15.el7_9
  samba-common.noarch 0:4.10.16-15.el7_9
  samba-common-libs.x86_64 0:4.10.16-15.el7_9
  samba-libs.x86_64 0:4.10.16-15.el7_9
  sed.x86_64 0:4.2.2-7.el7
  selinux-policy.noarch 0:3.13.1-268.el7_9.2
  selinux-policy-targeted.noarch 0:3.13.1-268.el7_9.2
  sudo.x86_64 0:1.8.23-10.el7_9.1
  systemd.x86_64 0:219-78.el7_9.3
  systemd-libs.x86_64 0:219-78.el7_9.3
  systemd-sysv.x86_64 0:219-78.el7_9.3
  teamd.x86_64 0:1.29-3.el7
  tuned.noarch 0:2.11.0-11.el7_9
  tzdata.noarch 0:2021a-1.el7
  util-linux.x86_64 0:2.23.2-65.el7_9.1
  vim-minimal.x86_64 2:7.4.629-8.el7_9
  wpa_supplicant.x86_64 1:2.6-12.el7_9.2
  xfsprogs.x86_64 0:4.5.0-22.el7
  yum.noarch 0:3.4.3-168.el7.centos
  yum-plugin-fastestmirror.noarch 0:1.1.31-54.el7_8
  yum-utils.noarch 0:1.1.31-54.el7_8
  zlib.x86_64 0:1.2.7-19.el7_9

Complete!
`````

>5. Ahora ya tenemos disponible el paquete nginx para su descarga e instalación, cosa que hacemos a continuación:

`````
[root@vm1 vagrant]# yum install -y nginx

Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.ufro.cl
 * epel: epel.mirror.constant.com
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
Resolving Dependencies
--> Running transaction check
---> Package nginx.x86_64 1:1.20.1-2.el7 will be installed
--> Processing Dependency: nginx-filesystem = 1:1.20.1-2.el7 for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libcrypto.so.1.1(OPENSSL_1_1_0)(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libssl.so.1.1(OPENSSL_1_1_0)(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libssl.so.1.1(OPENSSL_1_1_1)(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: nginx-filesystem for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: redhat-indexhtml for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: system-logos for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libcrypto.so.1.1()(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libprofiler.so.0()(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Processing Dependency: libssl.so.1.1()(64bit) for package: 1:nginx-1.20.1-2.el7.x86_64
--> Running transaction check
---> Package centos-indexhtml.noarch 0:7-9.el7.centos will be installed
---> Package centos-logos.noarch 0:70.0.6-3.el7.centos will be installed
---> Package gperftools-libs.x86_64 0:2.6.1-1.el7 will be installed
---> Package nginx-filesystem.noarch 1:1.20.1-2.el7 will be installed
---> Package openssl11-libs.x86_64 1:1.1.1g-3.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=======================================================================================================
 Package                     Arch              Version                           Repository       Size
=======================================================================================================
Installing:
 nginx                       x86_64            1:1.20.1-2.el7                    epel            586 k
Installing for dependencies:
 centos-indexhtml            noarch            7-9.el7.centos                    base             92 k
 centos-logos                noarch            70.0.6-3.el7.centos               base             21 M
 gperftools-libs             x86_64            2.6.1-1.el7                       base            272 k
 nginx-filesystem            noarch            1:1.20.1-2.el7                    epel             23 k
 openssl11-libs              x86_64            1:1.1.1g-3.el7                    epel            1.5 M

Transaction Summary
=======================================================================================================
Install  1 Package (+5 Dependent packages)

Total download size: 24 M
Installed size: 28 M
Downloading packages:
(1/6): centos-indexhtml-7-9.el7.centos.noarch.rpm                               |  92 kB  00:00:00
(2/6): nginx-1.20.1-2.el7.x86_64.rpm                                            | 586 kB  00:00:01
(3/6): gperftools-libs-2.6.1-1.el7.x86_64.rpm                                   | 272 kB  00:00:01
(4/6): nginx-filesystem-1.20.1-2.el7.noarch.rpm                                 |  23 kB  00:00:00
(5/6): openssl11-libs-1.1.1g-3.el7.x86_64.rpm                                   | 1.5 MB  00:00:00
(6/6): centos-logos-70.0.6-3.el7.centos.noarch.rpm                              |  21 MB  00:00:29
-------------------------------------------------------------------------------------------------------
Total                                                                  811 kB/s |  24 MB  00:00:29
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : centos-logos-70.0.6-3.el7.centos.noarch                                             1/6
  Installing : centos-indexhtml-7-9.el7.centos.noarch                                              2/6
  Installing : 1:nginx-filesystem-1.20.1-2.el7.noarch                                              3/6
  Installing : 1:openssl11-libs-1.1.1g-3.el7.x86_64                                                4/6
  Installing : gperftools-libs-2.6.1-1.el7.x86_64                                                  5/6
  Installing : 1:nginx-1.20.1-2.el7.x86_64                                                         6/6
  Verifying  : 1:nginx-1.20.1-2.el7.x86_64                                                         1/6
  Verifying  : gperftools-libs-2.6.1-1.el7.x86_64                                                  2/6
  Verifying  : 1:openssl11-libs-1.1.1g-3.el7.x86_64                                                3/6
  Verifying  : 1:nginx-filesystem-1.20.1-2.el7.noarch                                              4/6
  Verifying  : centos-indexhtml-7-9.el7.centos.noarch                                              5/6
  Verifying  : centos-logos-70.0.6-3.el7.centos.noarch                                             6/6

Installed:
  nginx.x86_64 1:1.20.1-2.el7

Dependency Installed:
  centos-indexhtml.noarch 0:7-9.el7.centos          centos-logos.noarch 0:70.0.6-3.el7.centos
  gperftools-libs.x86_64 0:2.6.1-1.el7              nginx-filesystem.noarch 1:1.20.1-2.el7
  openssl11-libs.x86_64 1:1.1.1g-3.el7

Complete!
`````

>6. Para iniciar por primera vez Nginx en CentOS 7 usaremos systemctl start:

`````
[root@vm1 vagrant]# systemctl start nginx

`````
>7. Y si queremos que Nginx arranque automáticamente junto con CentOS 7, es decir, en cada inicio del sistema, usaremos systemctl enable:

`````
[root@vm1 vagrant]# systemctl enable nginx

Created symlink from /etc/systemd/system/multi-user.target.wants/nginx.service to /usr/lib/systemd/system/nginx.service.

`````
>8. Ahora podremos comprobar que Nginx se encuentra en ejecución

`````
[root@vm1 vagrant]# systemctl status nginx

● nginx.service - The nginx HTTP and reverse proxy server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2021-06-24 22:33:45 UTC; 13s ago
  Process: 13754 ExecStart=/usr/sbin/nginx (code=exited, status=0/SUCCESS)
  Process: 13751 ExecStartPre=/usr/sbin/nginx -t (code=exited, status=0/SUCCESS)
  Process: 13749 ExecStartPre=/usr/bin/rm -f /run/nginx.pid (code=exited, status=0/SUCCESS)
 Main PID: 13756 (nginx)
   CGroup: /system.slice/nginx.service
           ├─13756 nginx: master process /usr/sbin/nginx
           ├─13757 nginx: worker process
           └─13758 nginx: worker process

Jun 24 22:33:44 vm1 systemd[1]: Starting The nginx HTTP and reverse proxy server...
Jun 24 22:33:45 vm1 nginx[13751]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
Jun 24 22:33:45 vm1 nginx[13751]: nginx: configuration file /etc/nginx/nginx.conf test is successful
Jun 24 22:33:45 vm1 systemd[1]: Started The nginx HTTP and reverse proxy server.

`````

>9. 

`````


`````

