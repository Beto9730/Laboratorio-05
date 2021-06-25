## Laboratorio NFS

>Elementos necesarios para el desarrollo del Laboratorio NFS:

- Vagrant 2.2.16
- GIT Bash

Pasos a seguir para la creacion del Laboratio NFS:

>1. Ingresamos via SSH a  vm_lab_2 
`````
$ vagrant ssh vm_lab_2

`````
>2. Entramos como superusuarios
`````
[vagrant@vm2 ~]$ sudo su

`````
>4. Primero vamos a instalar el servidor de NFS y configurarlo. Los comandos los corremos como root.
`````
[root@vm2 vagrant]# yum install nfs-utils

Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: mirror.ufro.cl
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
base                                                                            | 3.6 kB  00:00:00
extras                                                                          | 2.9 kB  00:00:00
updates                                                                         | 2.9 kB  00:00:00
(1/4): base/7/x86_64/group_gz                                                   | 153 kB  00:00:00
(2/4): extras/7/x86_64/primary_db                                               | 242 kB  00:00:00
(3/4): updates/7/x86_64/primary_db                                              | 8.8 MB  00:00:02
(4/4): base/7/x86_64/primary_db                                                 | 6.1 MB  00:00:08
Resolving Dependencies
--> Running transaction check
---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

=======================================================================================================
 Package                 Arch                 Version                         Repository          Size
=======================================================================================================
Updating:
 nfs-utils               x86_64               1:1.3.0-0.68.el7                base               412 k

Transaction Summary
=======================================================================================================
Upgrade  1 Package

Total download size: 412 k
Is this ok [y/d/N]: y
Downloading packages:
No Presto metadata available for base
warning: /var/cache/yum/x86_64/7/base/packages/nfs-utils-1.3.0-0.68.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
Public key for nfs-utils-1.3.0-0.68.el7.x86_64.rpm is not installed
nfs-utils-1.3.0-0.68.el7.x86_64.rpm                                             | 412 kB  00:00:00
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-8.2003.0.el7.centos.x86_64 (@anaconda)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.x86_64                                                   1/2
  Cleanup    : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                   2/2
  Verifying  : 1:nfs-utils-1.3.0-0.68.el7.x86_64                                                   1/2
  Verifying  : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                   2/2

Updated:
  nfs-utils.x86_64 1:1.3.0-0.68.el7

Complete!

`````
>5. Creamos los directorios en donde se va a compartir la información y darle permisos, por ahora le daremos permisos 777, luego podemos configurarlos para que escriban ciertos usuarios o ciertos grupos.
`````
[root@vm2 vagrant]# mkdir /data 
[root@vm2 vagrant]# chmod 777 /data

`````
>6. Debido a que Centos 7 viene con SElinux activado que no deja que NFS comparta archivos, vamos a activar algunas banderas para que podamos compartir
`````
[root@vm2 vagrant]# setsebool -P nfs_export_all_ro=1 nfs_export_all_rw=1

`````
>7. Necesitamos agregar las reglas de firewall para que que no nos bloquee el acceso desde el cliente.
`````
[root@vm2 vagrant]# firewall-cmd --permanent --add-service nfs
FirewallD is not running
[root@vm2 vagrant]# firewall-cmd --reload
FirewallD is not running

`````
>8. Una vez que ya tenemos instalado y con el firewall listo, es necesario habilitar los servicios, si no, no podemos usarlos
`````
[root@server ~]# systemctl enable rpcbind 
[root@server ~]# systemctl enable nfs-server 
[root@server ~]# systemctl start rpcbind 
[root@server ~]# systemctl start nfs 

`````
>9. Por último reiniciamos los servicios para que tomen efecto los cambios que hicimos
`````
[root@server ~]# systemctl restart nfs 

`````
>10. Ahora podremos comprobar que Nginx se encuentra en ejecución
`````
 systemctl status nfs
● nfs-server.service - NFS server and services
   Loaded: loaded (/usr/lib/systemd/system/nfs-server.service; enabled; vendor preset: disabled)
   Active: active (exited) since Fri 2021-06-25 22:13:22 UTC; 11s ago
  Process: 3457 ExecStopPost=/usr/sbin/exportfs -f (code=exited, status=0/SUCCESS)
  Process: 3453 ExecStopPost=/usr/sbin/exportfs -au (code=exited, status=0/SUCCESS)
  Process: 3451 ExecStop=/usr/sbin/rpc.nfsd 0 (code=exited, status=0/SUCCESS)
  Process: 3485 ExecStartPost=/bin/sh -c if systemctl -q is-active gssproxy; then systemctl reload gssproxy ; fi (code=exited, status=0/SUCCESS)
  Process: 3468 ExecStart=/usr/sbin/rpc.nfsd $RPCNFSDARGS (code=exited, status=0/SUCCESS)
  Process: 3467 ExecStartPre=/usr/sbin/exportfs -r (code=exited, status=1/FAILURE)
 Main PID: 3468 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/nfs-server.service

Jun 25 22:13:22 vm2 systemd[1]: Starting NFS server and services...
Jun 25 22:13:22 vm2 exportfs[3467]: exportfs: Invalid IP address xxx.xxx.xx...24
Jun 25 22:13:22 vm2 exportfs[3467]: exportfs: Invalid IP address xxx.xxx.xx...24
Jun 25 22:13:22 vm2 systemd[1]: Started NFS server and services.
Hint: Some lines were ellipsized, use -l to show in full.

`````


