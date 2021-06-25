## Laboratorio LVM

>Elementos necesarios para el desarrollo del Laboratorio LVM:

- Vagrant 2.2.16
- GIT Bash

Pasos a seguir para la creacion del Laboratio LVM:

>1. Primero actualice el caché del repositorio de paquetes con el siguiente comando
`````
[root@vm1 vagrant]# yum makecache

Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
epel/x86_64/metalink                                                             |  56 kB  00:00:00
 * base: mirror.ufro.cl
 * epel: mirror.math.princeton.edu
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
base                                                                             | 3.6 kB  00:00:00
epel                                                                             | 4.7 kB  00:00:00
extras                                                                           | 2.9 kB  00:00:00
updates                                                                          | 2.9 kB  00:00:00
(1/11): base/7/x86_64/other_db                                                   | 2.6 MB  00:00:01
(2/11): base/7/x86_64/filelists_db                                               | 7.2 MB  00:00:02
(3/11): epel/x86_64/filelists_db                                                 |  12 MB  00:00:04
(4/11): epel/x86_64/updateinfo                                                   | 1.0 MB  00:00:00
(5/11): epel/x86_64/prestodelta                                                  |  336 B  00:00:00
(6/11): epel/x86_64/primary_db                                                   | 6.9 MB  00:00:01
(7/11): extras/7/x86_64/other_db                                                 | 143 kB  00:00:00
(8/11): extras/7/x86_64/filelists_db                                             | 235 kB  00:00:00
(9/11): epel/x86_64/other_db                                                     | 3.4 MB  00:00:00
(10/11): updates/7/x86_64/other_db                                               | 680 kB  00:00:01
(11/11): updates/7/x86_64/filelists_db                                           | 5.1 MB  00:00:05
Metadata Cache Created

`````
>3. Ejecute el siguiente comando para instalar LVM 
`````
[root@vm1 vagrant]# sudo yum install lvm2
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.ufro.cl
 * epel: mirrors.upr.edu
 * extras: mirror.ufro.cl
 * updates: mirror.ufro.cl
Resolving Dependencies
--> Running transaction check
---> Package lvm2.x86_64 7:2.02.187-6.el7_9.5 will be installed
--> Processing Dependency: lvm2-libs = 7:2.02.187-6.el7_9.5 for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: device-mapper-persistent-data >= 0.7.0-0.1.rc6 for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: liblvm2app.so.2.2(Base)(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: libdevmapper-event.so.1.02(Base)(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.4)(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.1)(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: liblvm2app.so.2.2()(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: libdevmapper-event.so.1.02()(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Processing Dependency: libaio.so.1()(64bit) for package: 7:lvm2-2.02.187-6.el7_9.5.x86_64
--> Running transaction check
---> Package device-mapper-event-libs.x86_64 7:1.02.170-6.el7_9.5 will be installed
---> Package device-mapper-persistent-data.x86_64 0:0.8.5-3.el7_9.2 will be installed
---> Package libaio.x86_64 0:0.3.109-13.el7 will be installed
---> Package lvm2-libs.x86_64 7:2.02.187-6.el7_9.5 will be installed
--> Processing Dependency: device-mapper-event = 7:1.02.170-6.el7_9.5 for package: 7:lvm2-libs-2.02.187-6.el7_9.5.x86_64
--> Running transaction check
---> Package device-mapper-event.x86_64 7:1.02.170-6.el7_9.5 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================
 Package                              Arch          Version                        Repository      Size
========================================================================================================
Installing:
 lvm2                                 x86_64        7:2.02.187-6.el7_9.5           updates        1.3 M
Installing for dependencies:
 device-mapper-event                  x86_64        7:1.02.170-6.el7_9.5           updates        192 k
 device-mapper-event-libs             x86_64        7:1.02.170-6.el7_9.5           updates        192 k
 device-mapper-persistent-data        x86_64        0.8.5-3.el7_9.2                updates        423 k
 libaio                               x86_64        0.3.109-13.el7                 base            24 k
 lvm2-libs                            x86_64        7:2.02.187-6.el7_9.5           updates        1.1 M

Transaction Summary
========================================================================================================
Install  1 Package (+5 Dependent packages)

Total download size: 3.2 M
Installed size: 8.1 M
Is this ok [y/d/N]: y
Downloading packages:
(1/6): device-mapper-event-1.02.170-6.el7_9.5.x86_64.rpm                         | 192 kB  00:00:00
(2/6): libaio-0.3.109-13.el7.x86_64.rpm                                          |  24 kB  00:00:00
(3/6): device-mapper-event-libs-1.02.170-6.el7_9.5.x86_64.rpm                    | 192 kB  00:00:00
(4/6): lvm2-libs-2.02.187-6.el7_9.5.x86_64.rpm                                   | 1.1 MB  00:00:00
(5/6): lvm2-2.02.187-6.el7_9.5.x86_64.rpm                                        | 1.3 MB  00:00:00
(6/6): device-mapper-persistent-data-0.8.5-3.el7_9.2.x86_64.rpm                  | 423 kB  00:00:01
--------------------------------------------------------------------------------------------------------
Total                                                                   1.5 MB/s | 3.2 MB  00:00:02
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : 7:device-mapper-event-libs-1.02.170-6.el7_9.5.x86_64                                 1/6
  Installing : libaio-0.3.109-13.el7.x86_64                                                         2/6
  Installing : device-mapper-persistent-data-0.8.5-3.el7_9.2.x86_64                                 3/6
  Installing : 7:device-mapper-event-1.02.170-6.el7_9.5.x86_64                                      4/6
  Installing : 7:lvm2-libs-2.02.187-6.el7_9.5.x86_64                                                5/6
  Installing : 7:lvm2-2.02.187-6.el7_9.5.x86_64                                                     6/6
  Verifying  : 7:device-mapper-event-1.02.170-6.el7_9.5.x86_64                                      1/6
  Verifying  : 7:lvm2-libs-2.02.187-6.el7_9.5.x86_64                                                2/6
  Verifying  : device-mapper-persistent-data-0.8.5-3.el7_9.2.x86_64                                 3/6
  Verifying  : libaio-0.3.109-13.el7.x86_64                                                         4/6
  Verifying  : 7:lvm2-2.02.187-6.el7_9.5.x86_64                                                     5/6
  Verifying  : 7:device-mapper-event-libs-1.02.170-6.el7_9.5.x86_64                                 6/6

Installed:
  lvm2.x86_64 7:2.02.187-6.el7_9.5

Dependency Installed:
  device-mapper-event.x86_64 7:1.02.170-6.el7_9.5
  device-mapper-event-libs.x86_64 7:1.02.170-6.el7_9.5
  device-mapper-persistent-data.x86_64 0:0.8.5-3.el7_9.2
  libaio.x86_64 0:0.3.109-13.el7
  lvm2-libs.x86_64 7:2.02.187-6.el7_9.5

Complete!
`````
>4.  
`````


`````
>5.  
`````


`````
>6.  
`````


`````