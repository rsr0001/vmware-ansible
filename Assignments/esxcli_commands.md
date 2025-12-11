ubuntukn@ubuntukn-VirtualBox:~$ ssh root@172.30.30.176
(root@172.30.30.176) Password: 
The time and date of this login have been sent to the system logs.

WARNING:
   All commands run on the ESXi shell are logged and may be included in
   support bundles. Do not provide passwords directly on the command line.
   Most tools can prompt for secrets or accept them from standard input.

VMware offers powerful and supported automation tools. Please
see https://developer.vmware.com for details.

The ESXi Shell can be disabled by an administrative user. See the
vSphere Security documentation for more information.
[root@esxinitya:~] esxcli system hostname get
   Domain Name: 
   Fully Qualified Domain Name: esxinitya
   Host Name: esxinitya
[root@esxinitya:~] uptime
 16:32:08 up 1 days, 02:59:48, load average: 0.06, 0.09, 0.08
[root@esxinitya:~] esxcli system version get
   Product: VMware ESXi
   Version: 9.0.0
   Build: Releasebuild-24755229
   Update: 0
   Maintenance: 0
   Patch: 0
[root@esxinitya:~] esxcli hardware cpu list
CPU:0
   Id: 0
   Package Id: 0
   Family: 26
   Model: 68
   Type: 0
   Stepping: 0
   Brand: AuthenticAMD
   Core Speed: 2495312365
   Bus Speed: 92418976
   APIC ID: 0x0
   Node: 0
   Microcode Revision: 0xb404024
   Extended Servicing: false
   L2 Cache Size: 1048576
   L2 Cache Associativity: 16
   L2 Cache Line Size: 64
   L2 Cache CPU Count: 1
   L3 Cache Size: 33554432
   L3 Cache Associativity: 16
   L3 Cache Line Size: 64
   L3 Cache CPU Count: 2

CPU:1
   Id: 1
   Package Id: 0
   Family: 26
   Model: 68
   Type: 0
   Stepping: 0
   Brand: AuthenticAMD
   Core Speed: 2495312365
   Bus Speed: 92418976
   APIC ID: 0x1
   Node: 0
   Microcode Revision: 0xb404024
   Extended Servicing: false
   L2 Cache Size: 1048576
   L2 Cache Associativity: 16
   L2 Cache Line Size: 64
   L2 Cache CPU Count: 1
   L3 Cache Size: 33554432
   L3 Cache Associativity: 16
   L3 Cache Line Size: 64
   L3 Cache CPU Count: 2
[root@esxinitya:~] esxcli hardware memory get
   Physical Memory: 8588824576 Bytes
   Reliable Memory: 0 Bytes
   NUMA Node Count: 1
[root@esxinitya:~] esxcli hardware platform get
Platform Information
   UUID: 0xff 0x0 0x33 0x42 0xdc 0xd6 0x71 0xba 0xa 0x6a 0xf9 0x1c 0x57 0x13 0x25 0x99
   Product Name: VMware20,1
   Vendor Name: VMware, Inc.
   Serial Number: VMware-42 33 00 ff d6 dc ba 71-0a 6a f9 1c 57 13 25 99
   Enclosure Serial Number: None
   BIOS Asset Tag: No Asset Tag
   IPMI Supported: false
[root@esxinitya:~] esxcli hardware clock get
2025-12-11T16:32:46Z
[root@esxinitya:~] /etc/init.d/SSH start
SSH login enabled
SSH sandbox is not enabled, SSH will run in superdom
[root@esxinitya:~] /etc/init.d/SSH stop
SSH login disabled
[root@esxinitya:~] /etc/init.d/SSH status
SSH login is stopped
[root@esxinitya:~] /etc/init.d/hostd restart
hostd stopped.
hostd started.
[root@esxinitya:~] /etc/init.d/vpxa restart
vpxa stopped.
vpxa started.
[root@esxinitya:~] /etc/init.d/SSH restart
SSH login disabled
SSH login enabled
SSH sandbox is not enabled, SSH will run in superdom
[root@esxinitya:~] esxcli network nic list
Name    PCI Device    Driver    Admin Status  Link Status  Speed  Duplex  MAC Address         MTU  Description
------  ------------  --------  ------------  -----------  -----  ------  -----------------  ----  -----------
vmnic0  0000:02:01.0  nvmxnet3  Up            Up           10000  Full    00:50:56:b3:b9:89  1500  VMware Inc. vmxnet3 Virtual Ethernet Controller
[root@esxinitya:~] esxcli network nic get -n vmnic0
   Advertised Auto Negotiation: false
   Advertised Link Modes: 10000None/Full
   Auto Negotiation: false
   Backing DPUId: N/A
   Cable Type: 
   Current Message Level: 153
   Driver Info: 
         Bus Info: 0000:02:01:0
         Driver: nvmxnet3
         Firmware Version: 7
         Version: 2.0.0.31
   Link Detected: true
   Link Status: Up 
   Name: vmnic0
   PHYAddress: 0
   Pause Autonegotiate: false
   Pause RX: false
   Pause TX: false
   Supported Ports: 
   Supports Auto Negotiation: false
   Supports Pause: false
   Supports Wakeon: false
   Transceiver: 
   Virtual Address: 00:50:56:5f:1b:e1
   Wakeon: None
[root@esxinitya:~] esxcli network ip interface ipv4 get
Name  IPv4 Address   IPv4 Netmask   IPv4 Broadcast  Address Type  Gateway      DHCP DNS
----  -------------  -------------  --------------  ------------  -----------  --------
vmk0  172.30.30.176  255.255.255.0  172.30.30.255   STATIC        172.30.30.1     false
[root@esxinitya:~] esxcli network ip route ipv4 list
Network      Netmask        Gateway      Interface  Source
-----------  -------------  -----------  ---------  ------
default      0.0.0.0        172.30.30.1  vmk0       MANUAL
172.30.30.0  255.255.255.0  0.0.0.0      vmk0       MANUAL
[root@esxinitya:~] ping 172.30.30.176
PING 172.30.30.176 (172.30.30.176): 56 data bytes
64 bytes from 172.30.30.176: icmp_seq=0 ttl=64 time=0.282 ms
64 bytes from 172.30.30.176: icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from 172.30.30.176: icmp_seq=2 ttl=64 time=0.058 ms

--- 172.30.30.176 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.052/0.131/0.282 ms

[root@esxinitya:~] ping esxinitya.vt9labs.local

[root@esxinitya:~] ping esxinitya
PING esxinitya (172.30.30.176): 56 data bytes
64 bytes from 172.30.30.176: icmp_seq=0 ttl=64 time=0.112 ms
64 bytes from 172.30.30.176: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 172.30.30.176: icmp_seq=2 ttl=64 time=0.046 ms

--- esxinitya ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.026/0.061/0.112 ms

[root@esxinitya:~] esxcli storage core adapter list
HBA Name  Driver  Link State  UID           Capabilities  Description
--------  ------  ----------  ------------  ------------  -----------
vmhba0    pvscsi  link-n/a    pscsi.vmhba0                (0000:02:00.0) VMware Inc. PVSCSI SCSI Controller
[root@esxinitya:~] esxcli storage core device list
mpx.vmhba0:C0:T0:L0
   Display Name: Local VMware Disk (mpx.vmhba0:C0:T0:L0)
   Has Settable Display Name: false
   Size: 40960
   Device Type: Direct-Access 
   Multipath Plugin: HPP
   Devfs Path: /vmfs/devices/disks/mpx.vmhba0:C0:T0:L0
   Vendor: VMware  
   Model: Virtual disk    
   Revision: 2.0 
   SCSI Level: 6
   Is Pseudo: false
   Status: on
   Is RDM Capable: false
   Is Local: true
   Is Removable: false
   Is SSD: false
   Is VVOL PE: false
   Is Offline: false
   Is Perennially Reserved: false
   Queue Full Sample Size: 0
   Queue Full Threshold: 0
   Thin Provisioning Status: yes
   Attached Filters: 
   VAAI Status: unsupported
   Other UIDs: vml.0000000000766d686261303a303a30
   Is Shared Clusterwide: false
   Is SAS: false
   Is USB: false
   Is Boot Device: true
   Device Max Queue Depth: 1024
   No of outstanding IOs with competing worlds: 32
   Drive Type: unknown
   RAID Level: unknown
   Number of Physical Drives: unknown
   Protection Enabled: false
   PI Activated: false
   PI Type: 0
   PI Protection Mask: NO PROTECTION
   Supported Guard Types: NO GUARD SUPPORT
   DIX Enabled: false
   DIX Guard Type: NO GUARD SUPPORT
   Emulated DIX/DIF Enabled: false
[root@esxinitya:~] esxcli storage filesystem list
Mount Point                                        Volume Name                                 UUID                                 Mounted  Type           Size         Free
-------------------------------------------------  ------------------------------------------  -----------------------------------  -------  ------  -----------  -----------
/vmfs/volumes/693975f2-9139b258-8620-005056b3b989  OSDATA-693975f2-9139b258-8620-005056b3b989  693975f2-9139b258-8620-005056b3b989     true  VMFSOS  34091302912  32238469120
/vmfs/volumes/5f8b4c97-234dcc30-d982-54ea7418ec3f  BOOTBANK1                                   5f8b4c97-234dcc30-d982-54ea7418ec3f     true  vfat     4293591040   3975413760
/vmfs/volumes/b0d2f180-db4e3ca9-89bd-55f15a49be2a  BOOTBANK2                                   b0d2f180-db4e3ca9-89bd-55f15a49be2a     true  vfat     4293591040   4293525504
[root@esxinitya:~] 
[root@esxinitya:~] esxcli storage core adapter rescan --all
[root@esxinitya:~] vim-cmd vmsvc/getallvms
Vmid   Name   File   Guest OS   Version   Annotation
[root@esxinitya:~] esxcli storage filesystem list
Mount Point                                        Volume Name                                 UUID                                 Mounted  Type           Size         Free
-------------------------------------------------  ------------------------------------------  -----------------------------------  -------  ------  -----------  -----------
/vmfs/volumes/693975f2-9139b258-8620-005056b3b989  OSDATA-693975f2-9139b258-8620-005056b3b989  693975f2-9139b258-8620-005056b3b989     true  VMFSOS  34091302912  32238469120
/vmfs/volumes/5f8b4c97-234dcc30-d982-54ea7418ec3f  BOOTBANK1                                   5f8b4c97-234dcc30-d982-54ea7418ec3f     true  vfat     4293591040   3975413760
/vmfs/volumes/b0d2f180-db4e3ca9-89bd-55f15a49be2a  BOOTBANK2                                   b0d2f180-db4e3ca9-89bd-55f15a49be2a     true  vfat     4293591040   4293525504
[root@esxinitya:~] esxcli storage vmfs extent list
Volume Name                                 VMFS UUID                            Extent Number  Device Name          Partition
------------------------------------------  -----------------------------------  -------------  -------------------  ---------
OSDATA-693975f2-9139b258-8620-005056b3b989  693975f2-9139b258-8620-005056b3b989              0  mpx.vmhba0:C0:T0:L0          7
[root@esxinitya:~] 
[root@esxinitya:~] esxcli storage core device list
mpx.vmhba0:C0:T0:L0
   Display Name: Local VMware Disk (mpx.vmhba0:C0:T0:L0)
   Has Settable Display Name: false
   Size: 40960
   Device Type: Direct-Access 
   Multipath Plugin: HPP
   Devfs Path: /vmfs/devices/disks/mpx.vmhba0:C0:T0:L0
   Vendor: VMware  
   Model: Virtual disk    
   Revision: 2.0 
   SCSI Level: 6
   Is Pseudo: false
   Status: on
   Is RDM Capable: false
   Is Local: true
   Is Removable: false
   Is SSD: false
   Is VVOL PE: false
   Is Offline: false
   Is Perennially Reserved: false
   Queue Full Sample Size: 0
   Queue Full Threshold: 0
   Thin Provisioning Status: yes
   Attached Filters: 
   VAAI Status: unsupported
   Other UIDs: vml.0000000000766d686261303a303a30
   Is Shared Clusterwide: false
   Is SAS: false
   Is USB: false
   Is Boot Device: true
   Device Max Queue Depth: 1024
   No of outstanding IOs with competing worlds: 32
   Drive Type: unknown
   RAID Level: unknown
   Number of Physical Drives: unknown
   Protection Enabled: false
   PI Activated: false
   PI Type: 0
   PI Protection Mask: NO PROTECTION
   Supported Guard Types: NO GUARD SUPPORT
   DIX Enabled: false
   DIX Guard Type: NO GUARD SUPPORT
   Emulated DIX/DIF Enabled: false
[root@esxinitya:~] esxcli network nic list
Name    PCI Device    Driver    Admin Status  Link Status  Speed  Duplex  MAC Address         MTU  Description
------  ------------  --------  ------------  -----------  -----  ------  -----------------  ----  -----------
vmnic0  0000:02:01.0  nvmxnet3  Up            Up           10000  Full    00:50:56:b3:b9:89  1500  VMware Inc. vmxnet3 Virtual Ethernet Controller
[root@esxinitya:~] esxcli network ip interface ipv4 get
Name  IPv4 Address   IPv4 Netmask   IPv4 Broadcast  Address Type  Gateway      DHCP DNS
----  -------------  -------------  --------------  ------------  -----------  --------
vmk0  172.30.30.176  255.255.255.0  172.30.30.255   STATIC        172.30.30.1     false
[root@esxinitya:~] /etc/init.d/networking restart
-sh: /etc/init.d/networking: not found
[root@esxinitya:~] esxcli network vswitch dvs vmware list
VDS-Prod
   Name: VDS-Prod
   VDS ID: 50 33 8c 87 5f 05 cd 73-bc 4f 7c 4f 55 23 fc f8
   Class: cswitch
   Num Ports: 1590
   Used Ports: 1
   Configured Ports: 512
   MTU: 1500
   CDP Status: listen
   Beacon Timeout: -1
   Uplinks: 
   VMware Branded: true
   DVPort: 
         Client: 
         DVPortgroup ID: dvportgroup-4024
         In Use: false
         Port ID: 0
      
         Client: 
         DVPortgroup ID: dvportgroup-4024
         In Use: false
         Port ID: 1
[root@esxinitya:~] tail -f /var/log/vmkernel.log
2025-12-11T16:41:48.486Z In(182) vmkernel: cpu1:131211)NRandomHwrng: 500: Out of entropy, refreshing.
2025-12-11T16:42:01.169Z In(182) vmkernel: cpu0:170428)Config: 727: "TrackMigrations" = 1, Old Value: 0, (Status: 0x0)
2025-12-11T16:42:01.171Z In(182) vmkernel: cpu0:170428)Uplink: 537: vmnic0: Driver claims supporting 0 RX queues, and 0 queues are accepted.
2025-12-11T16:42:01.171Z In(182) vmkernel: cpu0:170428)Uplink: 537: vmnic0: Driver claims supporting 0 RX queues, and 0 queues are accepted.
2025-12-11T16:42:31.174Z In(182) vmkernel: cpu0:170428)Config: 727: "TrackHistos" = 0, Old Value: 0, (Status: 0x0)
2025-12-11T16:42:31.174Z In(182) vmkernel: cpu0:170428)Config: 727: "TrackAdvancedStats" = 0, Old Value: 0, (Status: 0x0)
2025-12-11T16:42:31.174Z In(182) vmkernel: cpu0:170428)Config: 727: "TrackMigrations" = 0, Old Value: 1, (Status: 0x0)
2025-12-11T16:42:36.314Z In(182) vmkernel: cpu0:131211)NRandomHwrng: 500: Out of entropy, refreshing.
2025-12-11T16:42:36.562Z In(182) vmkernel: cpu0:131211)NRandomHwrng: 500: Out of entropy, refreshing.
2025-12-11T16:42:36.845Z In(182) vmkernel: cpu0:131211)NRandomHwrng: 500: Out of entropy, refreshing.
2025-12-11T16:43:26.651Z In(182) vmkernel: cpu1:131211)NRandomHwrng: 500: Out of entropy, refreshing.
2025-12-11T16:43:26.917Z In(182) vmkernel: cpu1:131211)NRandomHwrng: 500: Out of entropy, refreshing.

[root@esxinitya:~] tail -f /var/log/hostd.log
2025-12-11T16:43:23.314Z In(166) Hostd[169827]: [Originator@6876 sub=Vimsvc.HTTPService.HttpConnection] HTTP Connection has timed out while waiting for further requests; <io_obj t:N7Vmacore6System21LocalSocketObjectAsioE, h:-1, <UNIX 'hostdEntitlementVapi.sock'>, <UNIX 'hostdEntitlementVapi.sock'>>, N7Vmacore16TimeoutExceptionE(Operation timed out: Stream: <io_obj t:N7Vmacore6System21LocalSocketObjectAsioE, h:-1, <UNIX 'hostdEntitlementVapi.sock'>, <UNIX 'hostdEntitlementVapi.sock'>>, duration: 00:00:46.257054 (hh:mm:ss.us))
2025-12-11T16:43:23.314Z In(166) Hostd[169797]: --> [context]zKq7AVICAgAAAB28eQEIaG9zdGQAAF5oNWxpYnZtYWNvcmUuc28AAHtnJADEaCQAbhMlAGA4JQC7iEoBXl8IbGliYy5zby42AAEwXBA=[/context]
2025-12-11T16:43:25.003Z Er(163) Hostd[169828]: [Originator@6876 sub=VMkernelStatsProvider(000000a67b5238a0)] GetKernelStatValues: Detected error while retrieving stats: VSINode(2810): Not found (status=195887107)
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 19
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 20
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 21
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 22
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 23
2025-12-11T16:43:28.795Z Wa(164) Hostd[169823]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 24
2025-12-11T16:43:45.004Z Er(163) Hostd[169809]: [Originator@6876 sub=VMkernelStatsProvider(000000a67b5238a0)] GetKernelStatValues: Detected error while retrieving stats: VSINode(2810): Not found (status=195887107)
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 19
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 20
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 21
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 22
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 23
2025-12-11T16:43:48.812Z Wa(164) Hostd[169830]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 24

[root@esxinitya:~] tail -f /var/log/vpxa.log
2025-12-11T16:43:03.077Z In(166) Vpxa[170012]: [Originator@6876 sub=vpxLro opID=PollQuickStatsLoop-27bd305b-fb] [VpxLRO] -- BEGIN lro-47 -- vpxa -- vpxapi.VpxaService.fetchQuickStats -- 52bb5d24-2497-10d0-569c-3ec666d27030
2025-12-11T16:43:03.078Z In(166) Vpxa[170012]: [Originator@6876 sub=vpxLro opID=PollQuickStatsLoop-27bd305b-fb] [VpxLRO] -- FINISH lro-47
2025-12-11T16:43:22.998Z In(166) Vpxa[169993]: [Originator@6876 sub=vpxaInvtHost opID=resourcePoolImpl.cpp:1737-25c61c82] Increment master gen. no to (101): ResourcePool:VpxaInvtHostResPoolListener::ConfigChanged
2025-12-11T16:43:26.181Z In(166) Vpxa[169980]: [Originator@6876 sub=vpxLro opID=HB-host-4018@101-32779840-2d] [VpxLRO] -- BEGIN lro-48 -- vpxa -- vpxapi.VpxaService.getChanges -- 52bb5d24-2497-10d0-569c-3ec666d27030
2025-12-11T16:43:26.181Z In(166) Vpxa[169980]: [Originator@6876 sub=vpxLro opID=HB-host-4018@101-32779840-2d] [VpxLRO] -- FINISH lro-48
2025-12-11T16:43:27.113Z In(166) Vpxa[170123]: [Originator@6876 sub=Http2ServerSession-4] Starting Http2Session (server): <io_obj t:N7Vmacore6System19TCPSocketObjectAsioE, h:25, <TCP '127.0.0.1 : 8089'>, <TCP '127.0.0.1 : 49584'>>
2025-12-11T16:43:27.114Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=5d8e4bd2] [VpxLRO] -- BEGIN lro-49 -- vpxa -- vpxapi.VpxaService.getVpxaInfo -- 521943a6-1f2b-96b0-78a1-9024ad6feb82
2025-12-11T16:43:27.114Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=5d8e4bd2] [VpxLRO] -- FINISH lro-49
2025-12-11T16:43:27.117Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=2913f7fa] [VpxLRO] -- BEGIN lro-50 -- vpxa -- vpxapi.VpxaService.queryVpxaStatus -- 52cae26a-9a9d-3d1a-601c-5e0ed161c6e4
2025-12-11T16:43:27.117Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=2913f7fa] [VpxLRO] -- FINISH lro-50

[root@esxinitya:~] tail -f /var/log/hostd.log
2025-12-11T16:44:00.665Z In(166) Hostd[169840]: [Originator@6876 sub=Libs] SOCKET creating new socket, connecting to /var/run/vmware/usbarbitrator-socket
2025-12-11T16:44:00.665Z In(166) Hostd[169840]: [Originator@6876 sub=Libs] SOCKET connect failed, error 2: No such file or directory
2025-12-11T16:44:00.665Z Wa(164) Hostd[169840]: [Originator@6876 sub=Libs] USBArbLib: Failed to connect to USB Arbitrator, arbSocketname(/var/run/vmware/usbarbitrator-socket). Error(0x6): Connection error.
2025-12-11T16:44:05.003Z Er(163) Hostd[169818]: [Originator@6876 sub=VMkernelStatsProvider(000000a67b5238a0)] GetKernelStatValues: Detected error while retrieving stats: VSINode(2810): Not found (status=195887107)
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 19
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 20
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 21
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 22
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 23
2025-12-11T16:44:08.820Z Wa(164) Hostd[169826]: [Originator@6876 sub=deviceStatsProvider(000000a67b8eb2f0)] FillVirtualDeviceStats: Unable to locate sample for stat ID 24

[root@esxinitya:~] ^C
[root@esxinitya:~] ^C
[root@esxinitya:~] ^C
[root@esxinitya:~] ^C
[root@esxinitya:~] tail -f /var/log/vpxa.log
2025-12-11T16:43:27.114Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=5d8e4bd2] [VpxLRO] -- FINISH lro-49
2025-12-11T16:43:27.117Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=2913f7fa] [VpxLRO] -- BEGIN lro-50 -- vpxa -- vpxapi.VpxaService.queryVpxaStatus -- 52cae26a-9a9d-3d1a-601c-5e0ed161c6e4
2025-12-11T16:43:27.117Z In(166) Vpxa[169982]: [Originator@6876 sub=vpxLro opID=2913f7fa] [VpxLRO] -- FINISH lro-50
2025-12-11T16:44:03.076Z In(166) Vpxa[169995]: [Originator@6876 sub=vpxLro opID=PollQuickStatsLoop-27bd305b-a6] [VpxLRO] -- BEGIN lro-51 -- vpxa -- vpxapi.VpxaService.fetchQuickStats -- 52bb5d24-2497-10d0-569c-3ec666d27030
2025-12-11T16:44:03.076Z In(166) Vpxa[169995]: [Originator@6876 sub=vpxLro opID=PollQuickStatsLoop-27bd305b-a6] [VpxLRO] -- FINISH lro-51
2025-12-11T16:44:23.001Z In(166) Vpxa[169992]: [Originator@6876 sub=vpxaInvtHost opID=resourcePoolImpl.cpp:1737-377f8d85] Increment master gen. no to (102): ResourcePool:VpxaInvtHostResPoolListener::ConfigChanged
2025-12-11T16:44:23.732Z In(166) Vpxa[169980]: [Originator@6876 sub=vpxLro opID=7b9d4753-3a] [VpxLRO] -- BEGIN lro-52 -- networkSystem -- vim.host.NetworkSystem.queryNetworkHint -- 52bb5d24-2497-10d0-569c-3ec666d27030
2025-12-11T16:44:23.735Z In(166) Vpxa[169980]: [Originator@6876 sub=vpxLro opID=7b9d4753-3a] [VpxLRO] -- FINISH lro-52
2025-12-11T16:44:26.192Z In(166) Vpxa[169995]: [Originator@6876 sub=vpxLro opID=HB-host-4018@102-30b88c4e-b4] [VpxLRO] -- BEGIN lro-53 -- vpxa -- vpxapi.VpxaService.getChanges -- 52bb5d24-2497-10d0-569c-3ec666d27030
2025-12-11T16:44:26.193Z In(166) Vpxa[169995]: [Originator@6876 sub=vpxLro opID=HB-host-4018@102-30b88c4e-b4] [VpxLRO] -- FINISH lro-53

[root@esxinitya:~] 

ESXi Command Reference
1. System Information Commands
a) Get Hostname
esxcli system hostname get


Output Explanation:

Host Name: The ESXi host’s hostname.

Fully Qualified Domain Name (FQDN): Hostname with domain.

Domain Name: DNS domain configured on the host.

b) Get ESXi Version
esxcli system version get


Output Explanation:

Product: VMware ESXi

Version: ESXi version installed

Build: Build number

Update, Maintenance, Patch: Current update/patch level

c) Host Uptime
uptime


Output Explanation:

Shows host uptime, load average, and system start time.

2. Hardware Information
a) CPU Information
esxcli hardware cpu list


Output Explanation:

Id & Package Id: CPU identifiers

Brand: CPU model

Core Speed & Bus Speed: Operating frequency

Cache Sizes (L2/L3): Cache memory info

Microcode Revision: CPU microcode version

b) Memory Information
esxcli hardware memory get


Output Explanation:

Physical Memory: Total RAM in bytes

Reliable Memory: Fault-tolerant memory

NUMA Node Count: Number of NUMA nodes

c) Platform Information
esxcli hardware platform get


Output Explanation:

UUID: Unique identifier of the host

Product Name & Vendor: Host model and manufacturer

Serial Number: Hardware serial

IPMI Supported: Indicates if remote management is supported

d) Hardware Clock
esxcli hardware clock get


Output Explanation:

Shows the ESXi host’s system clock in UTC.

3. VM Management Commands
a) List All VMs
vim-cmd vmsvc/getallvms


Output Explanation:

Vmid: VM ID, used in power operations

Name: VM name

File: VMX configuration path

Guest OS: OS type installed in VM

Version: VM hardware version

b) Get VM Summary
vim-cmd vmsvc/get.summary <VMID>


Output Explanation:

Shows VM status, memory, CPU, power state, and datastore location.

c) Power Operations on VM
vim-cmd vmsvc/power.on <VMID>
vim-cmd vmsvc/power.off <VMID>
vim-cmd vmsvc/power.reboot <VMID>
vim-cmd vmsvc/power.reset <VMID>


Output Explanation:

power.on: Starts VM

power.off: Shuts down VM

power.reboot: Graceful reboot

power.reset: Hard reset (similar to power cycle)

4. Storage Commands
a) List Filesystems
esxcli storage filesystem list


Output Explanation:

Mount Point: Path where datastore is mounted

Volume Name: Datastore label

UUID: Unique identifier for datastore

Mounted: true/false

Type: VMFS, vfat, etc.

Size & Free: Total and free space

b) Rescan Storage Adapters
esxcli storage core adapter rescan --all


Output Explanation:

Rescans all HBAs to detect new devices or LUNs.

c) List VMFS Extents
esxcli storage vmfs extent list


Output Explanation:

Volume Name & VMFS UUID

Extent Number: Physical extent index

Device Name & Partition: Device backing the VMFS datastore

d) List Storage Devices
esxcli storage core device list


Output Explanation:

Display Name: Device name

Size: Capacity in GB

Device Type: Direct-access, CD-ROM, etc.

Thin Provisioning Status

Boot Device, Local/Shared

RAID Level, SSD status

e) List Storage Adapters
esxcli storage core adapter list


Output Explanation:

HBA Name: Adapter ID

Driver: Driver used for HBA

Link State: Up/Down

Capabilities & Description

5. Network Commands
a) List NICs
esxcli network nic list


Output Explanation:

Name: vmnic identifier

Driver: NIC driver

Admin Status: Up/Down

Link Status: Connected/disconnected

Speed & Duplex

MAC Address & MTU

b) Get NIC Details
esxcli network nic get -n <NIC>


Output Explanation:

Full details about a specific NIC, including link detection, auto-negotiation, firmware, and driver version.

c) Get IP Configuration
esxcli network ip interface ipv4 get


Output Explanation:

IP, netmask, gateway, DHCP, and DNS settings for each VMkernel interface.

d) List IP Routes
esxcli network ip route ipv4 list


Output Explanation:

Displays static and default routes for the host network.

e) List vSwitches
esxcli network vswitch standard list


Output Explanation:

Lists standard virtual switches and configuration (ports, MTU, uplinks, etc.)

f) List Distributed vSwitches
esxcli network vswitch dvs vmware list


Output Explanation:

Lists distributed vSwitches (VDS) and associated ports.

6. Service Management
a) Manage SSH
/etc/init.d/SSH start
/etc/init.d/SSH stop
/etc/init.d/SSH restart
/etc/init.d/SSH status


Output Explanation:

Enable, disable, restart, or check SSH service status.

b) Manage Host Services
/etc/init.d/hostd restart
/etc/init.d/vpxa restart


Output Explanation:

hostd: Manages host agent, required for vSphere client.

vpxa: Manages communication between vCenter and ESXi host.

c) View Logs
tail -f /var/log/vmkernel.log
tail -f /var/log/hostd.log
tail -f /var/log/vpxa.log


Output Explanation:

Monitors real-time logs for kernel, host agent, and vCenter agent activity.
