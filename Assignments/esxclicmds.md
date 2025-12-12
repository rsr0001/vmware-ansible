pooja@gouds:~$ ssh root@172.30.30.151
(root@172.30.30.151) Password:
The time and date of this login have been sent to the system logs.

WARNING:
   All commands run on the ESXi shell are logged and may be included in
   support bundles. Do not provide passwords directly on the command line.
   Most tools can prompt for secrets or accept them from standard input.

VMware offers powerful and supported automation tools. Please
see https://developer.vmware.com for details.

The ESXi Shell can be disabled by an administrative user. See the
vSphere Security documentation for more information.
[root@esxi01pooja:~] esxcli storage filesystem list
Mount Point                                        Volume Name                                 UUID                                 Mounted  Type           Size         Free
-------------------------------------------------  ------------------------------------------  -----------------------------------  -------  ------  -----------  -----------
/vmfs/volumes/6935c9aa-fa46047b-2596-005056b36949  OSDATA-6935c9aa-fa46047b-2596-005056b36949  6935c9aa-fa46047b-2596-005056b36949     true  VMFSOS  34091302912  32088522752
/vmfs/volumes/bce53c44-7c409452-6d9c-54f415677c86  BOOTBANK1                                   bce53c44-7c409452-6d9c-54f415677c86     true  vfat     4293591040   3975413760
/vmfs/volumes/6250e3f8-944fc3bd-ee94-ccd1286a4e05  BOOTBANK2                                   6250e3f8-944fc3bd-ee94-ccd1286a4e05     true  vfat     4293591040   4293525504
[root@esxi01pooja:~] esxcli storage core device list
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
[root@esxi01pooja:~] /etc/init.d/hostd restart
hostd stopped.
hostd started.
[root@esxi01pooja:~] /etc/init.d/vpxa restart
vpxa stopped.
vpxa started.
[root@esxi01pooja:~] services.sh restart
2025-12-12T16:37:30.136Z Using VMware ESXi syslog APIs
2025-12-12T16:37:30.143Z executing stop for daemon nsxcli.
2025-12-12T16:37:30.143Z executing stop for daemon xorg.
2025-12-12T16:37:30.143Z executing stop for daemon nsx-host.
2025-12-12T16:37:30.143Z executing stop for daemon drivervm-init.
2025-12-12T16:37:30.153Z xorg stopped.
2025-12-12T16:37:30.153Z executing stop for daemon gpuManager.
2025-12-12T16:37:30.154Z nsx-host stopped.
2025-12-12T16:37:30.154Z executing stop for daemon vmtoolsd.
2025-12-12T16:37:30.164Z drivervm-init stopped.
2025-12-12T16:37:30.164Z executing stop for daemon vaai-nasd.
2025-12-12T16:37:30.166Z nsxcli stopped.
2025-12-12T16:37:30.166Z executing stop for daemon lsud.
2025-12-12T16:37:30.174Z vaai-nasd stopped.
2025-12-12T16:37:30.176Z lsud stopped.
2025-12-12T16:37:30.268Z gpuManager stopped.
2025-12-12T16:37:30.350Z vmtoolsd stopped.
2025-12-12T16:37:30.350Z executing stop for daemon snmpd.
2025-12-12T16:37:30.600Z snmpd stopped.
2025-12-12T16:37:30.601Z executing stop for daemon health.
2025-12-12T16:37:30.613Z health stopped.
2025-12-12T16:37:30.614Z executing stop for daemon vpxa.
2025-12-12T16:37:30.624Z vpxa stopped.
2025-12-12T16:37:30.624Z executing stop for daemon settingsd.
2025-12-12T16:37:30.635Z settingsd stopped.
2025-12-12T16:37:30.635Z executing stop for daemon pmemGarbageCollection.
2025-12-12T16:37:30.635Z executing stop for daemon nscd.
2025-12-12T16:37:30.635Z executing stop for daemon nicmgmtd.
2025-12-12T16:37:30.637Z executing stop for daemon dcbd.
2025-12-12T16:37:30.649Z dcbd stopped.
2025-12-12T16:37:30.649Z executing stop for daemon cdp.
2025-12-12T16:37:30.655Z pmemGarbageCollection stopped.
2025-12-12T16:37:30.655Z executing stop for daemon smartd.
2025-12-12T16:37:30.656Z nscd stopped.
2025-12-12T16:37:30.656Z executing stop for daemon lacp.
2025-12-12T16:37:30.670Z cdp stopped.
2025-12-12T16:37:30.676Z smartd stopped.
2025-12-12T16:37:30.766Z nicmgmtd stopped.
2025-12-12T16:37:31.519Z lacp stopped.
2025-12-12T16:37:31.519Z executing stop for daemon infravisor.
2025-12-12T16:37:31.519Z executing stop for daemon clusterAgent.
2025-12-12T16:37:31.641Z infravisor stopped.
2025-12-12T16:37:31.820Z clusterAgent stopped.
2025-12-12T16:37:31.820Z executing stop for daemon vvold.
2025-12-12T16:37:31.820Z executing stop for daemon rhttpproxy.
2025-12-12T16:37:31.820Z executing stop for daemon hostdCgiServer.
2025-12-12T16:37:31.820Z executing stop for daemon hostd.
2025-12-12T16:37:31.851Z hostdCgiServer stopped.
2025-12-12T16:37:31.851Z executing stop for daemon esxTokenCPS.
2025-12-12T16:37:31.861Z vvold stopped.
2025-12-12T16:37:31.861Z executing stop for daemon apiForwarder.
2025-12-12T16:37:31.877Z rhttpproxy stopped.
2025-12-12T16:37:31.877Z executing stop for daemon sensord.
2025-12-12T16:37:31.881Z apiForwarder stopped.
2025-12-12T16:37:31.882Z executing stop for daemon nfcd.
2025-12-12T16:37:31.882Z hostd stopped.
2025-12-12T16:37:31.882Z executing stop for daemon lbtd.
2025-12-12T16:37:31.892Z nfcd stopped.
2025-12-12T16:37:31.892Z executing stop for daemon esx-datapath-ctrs.
2025-12-12T16:37:31.893Z lbtd stopped.
2025-12-12T16:37:31.893Z executing stop for daemon vmfstraced.
2025-12-12T16:37:31.978Z esxTokenCPS stopped.
2025-12-12T16:37:32.032Z sensord stopped.
2025-12-12T16:37:32.074Z vmfstraced stopped.
2025-12-12T16:37:32.235Z esx-datapath-ctrs stopped.
2025-12-12T16:37:32.235Z executing stop for daemon esxui.
2025-12-12T16:37:32.235Z executing stop for daemon sandboxd.
2025-12-12T16:37:32.235Z executing stop for daemon esxgdpd.
2025-12-12T16:37:32.236Z executing stop for daemon envoy.
2025-12-12T16:37:32.245Z esxui stopped.
2025-12-12T16:37:32.245Z executing stop for daemon usbarbitrator.
2025-12-12T16:37:32.246Z sandboxd stopped.
2025-12-12T16:37:32.246Z executing stop for daemon vdtc.
2025-12-12T16:37:32.256Z usbarbitrator stopped.
2025-12-12T16:37:32.256Z executing stop for daemon swapobjd.
2025-12-12T16:37:32.270Z esxgdpd stopped.
2025-12-12T16:37:32.270Z executing stop for daemon iofilterd-vmwarevmcrypt.
2025-12-12T16:37:32.300Z vdtc stopped.
2025-12-12T16:37:32.300Z executing stop for daemon iofilterd-spm.
2025-12-12T16:37:32.323Z envoy stopped.
2025-12-12T16:37:32.404Z swapobjd stopped.
2025-12-12T16:37:32.406Z iofilterd-spm stopped.
2025-12-12T16:37:32.406Z iofilterd-vmwarevmcrypt stopped.
2025-12-12T16:37:32.406Z executing stop for daemon SSH.
2025-12-12T16:37:32.406Z executing stop for daemon ESXShell.
2025-12-12T16:37:32.407Z executing stop for daemon DCUI.
2025-12-12T16:37:32.437Z DCUI stopped.
2025-12-12T16:37:32.437Z SSH stopped.
2025-12-12T16:37:32.469Z ESXShell stopped.
Errors:
Invalid operation requested: This ruleset is required and cannot be disabled
2025-12-12T16:37:33.136Z Using VMware ESXi syslog APIs
2025-12-12T16:37:33.147Z executing start plugin: ESXShell
2025-12-12T16:37:33.147Z executing start plugin: DCUI
2025-12-12T16:37:33.148Z executing start plugin: SSH
2025-12-12T16:37:33.203Z SSH started.
2025-12-12T16:37:33.208Z DCUI started.
2025-12-12T16:37:33.237Z ESXShell started.
2025-12-12T16:37:33.237Z executing start plugin: sandboxd
2025-12-12T16:37:33.237Z executing start plugin: esxui
2025-12-12T16:37:33.238Z executing start plugin: esxgdpd
2025-12-12T16:37:33.238Z executing start plugin: envoy
2025-12-12T16:37:33.258Z sandboxd started.
2025-12-12T16:37:33.258Z executing start plugin: usbarbitrator
2025-12-12T16:37:33.302Z esxgdpd started.
2025-12-12T16:37:33.302Z executing start plugin: vdtc
2025-12-12T16:37:33.323Z vdtc started.
2025-12-12T16:37:33.323Z executing start plugin: swapobjd
2025-12-12T16:37:33.525Z envoy started.
2025-12-12T16:37:33.525Z executing start plugin: iofilterd-vmwarevmcrypt
2025-12-12T16:37:33.650Z swapobjd started.
2025-12-12T16:37:33.651Z executing start plugin: iofilterd-spm
2025-12-12T16:37:33.711Z iofilterd-vmwarevmcrypt started.
2025-12-12T16:37:33.823Z iofilterd-spm started.
2025-12-12T16:37:33.943Z esxui started.
2025-12-12T16:37:34.568Z usbarbitrator started.
2025-12-12T16:37:34.568Z executing start plugin: vvold
2025-12-12T16:37:34.568Z executing start plugin: rhttpproxy
2025-12-12T16:37:34.568Z executing start plugin: hostdCgiServer
2025-12-12T16:37:34.568Z executing start plugin: hostd
2025-12-12T16:37:34.669Z hostdCgiServer started.
2025-12-12T16:37:34.669Z executing start plugin: esxTokenCPS
2025-12-12T16:37:34.701Z rhttpproxy started.
2025-12-12T16:37:34.701Z executing start plugin: apiForwarder
2025-12-12T16:37:34.712Z esxTokenCPS started.
2025-12-12T16:37:34.712Z executing start plugin: sensord
2025-12-12T16:37:35.084Z sensord started.
2025-12-12T16:37:35.084Z executing start plugin: nfcd
2025-12-12T16:37:35.129Z nfcd started.
2025-12-12T16:37:35.130Z executing start plugin: lbtd
2025-12-12T16:37:35.162Z lbtd started.
2025-12-12T16:37:35.162Z executing start plugin: esx-datapath-ctrs
2025-12-12T16:37:35.443Z esx-datapath-ctrs started.
2025-12-12T16:37:35.443Z executing start plugin: vmfstraced
2025-12-12T16:37:35.475Z apiForwarder started.
2025-12-12T16:37:35.493Z vmfstraced started.
2025-12-12T16:37:36.122Z hostd started.
2025-12-12T16:37:37.241Z vvold started.
2025-12-12T16:37:37.241Z executing start plugin: infravisor
2025-12-12T16:37:37.241Z executing start plugin: clusterAgent
2025-12-12T16:37:37.735Z infravisor started.
2025-12-12T16:37:40.185Z clusterAgent started.
2025-12-12T16:37:40.185Z executing start plugin: pmemGarbageCollection
2025-12-12T16:37:40.185Z executing start plugin: nscd
2025-12-12T16:37:40.185Z executing start plugin: nicmgmtd
2025-12-12T16:37:40.187Z executing start plugin: dcbd
2025-12-12T16:37:40.195Z nscd started.
2025-12-12T16:37:40.195Z executing start plugin: cdp
2025-12-12T16:37:40.217Z dcbd started.
2025-12-12T16:37:40.217Z executing start plugin: smartd
2025-12-12T16:37:40.266Z pmemGarbageCollection started.
2025-12-12T16:37:40.266Z executing start plugin: lacp
2025-12-12T16:37:40.267Z cdp started.
2025-12-12T16:37:40.288Z lacp started.
2025-12-12T16:37:40.298Z nicmgmtd started.
2025-12-12T16:37:40.349Z smartd started.
2025-12-12T16:37:40.349Z executing start plugin: settingsd
2025-12-12T16:37:40.597Z settingsd started.
2025-12-12T16:37:40.597Z executing start plugin: vpxa
2025-12-12T16:37:40.618Z vpxa started.
2025-12-12T16:37:40.618Z executing start plugin: health
2025-12-12T16:37:40.680Z health started.
2025-12-12T16:37:40.680Z executing start plugin: snmpd
2025-12-12T16:37:41.978Z snmpd started.
2025-12-12T16:37:41.978Z executing start plugin: nsxcli
2025-12-12T16:37:41.978Z executing start plugin: nsx-host
2025-12-12T16:37:41.978Z executing start plugin: xorg
2025-12-12T16:37:41.980Z executing start plugin: drivervm-init
2025-12-12T16:37:41.988Z nsxcli started.
2025-12-12T16:37:41.988Z executing start plugin: gpuManager
2025-12-12T16:37:41.988Z nsx-host started.
2025-12-12T16:37:41.988Z executing start plugin: vmtoolsd
2025-12-12T16:37:41.989Z xorg started.
2025-12-12T16:37:41.989Z executing start plugin: vaai-nasd
2025-12-12T16:37:41.991Z drivervm-init started.
2025-12-12T16:37:41.992Z executing start plugin: lsud
2025-12-12T16:37:42.002Z lsud started.
2025-12-12T16:37:42.009Z vaai-nasd started.
2025-12-12T16:37:42.610Z gpuManager started.
2025-12-12T16:37:42.871Z vmtoolsd started.
[root@esxi01pooja:~] cat vmware.log
cat: can't open 'vmware.log': No such file or directory
[root@esxi01pooja:~] esxcli network firewall get
   Default Action: DROP
   Enabled: true
   Loaded: true
[root@esxi01pooja:~] esxcli system time get
2025-12-12T16:39:45Z
[root@esxi01pooja:~] /etc/init.d/ntpd restart
ntpd is not running
Starting ntpd
[root@esxi01pooja:~] vim-cmd vimsvc/license --show
[200] Sending request for installed licenses...[200] Complete, result is:
   serial: 00000-00000-00000-00000-00000
   vmodl key: esx.eval.entitlement.cpuCoreMin
   name: VMware ESX Server
   total: 1
   used: 1
   unit: host
   Properties:
     [system_time] = 2025-12-12T16:40:29.093875Z
     [startDate] = 2025-12-07T02:40:52Z
     [expirationDate] = 2026-03-07T18:40:52Z
     [expirationHours] = 2042
     [expirationMinutes] = 122520
     [ProductName] = VMware ESX Server
     [ComponentFamily] = VMware ESX Server
     [ProductVersion] = 9.0
     [FileVersion] = 9.0.0.1
     [Localized] = <Not supported type for value: [N5Vmomi9DataArrayINS_11KeyAnyValueEEE]>

[200] End of report.
[root@esxi01pooja:~] history
   0 esxcli storage filesystem list
   1 esxcli storage core device list
   2 /etc/init.d/hostd restart
   3 /etc/init.d/vpxa restart
   4 services.sh restart
   5 cat vmware.log
   6 esxcli network firewall get
   7 esxcli system time get
   8 /etc/init.d/ntpd restart
   9 vim-cmd vimsvc/license --show
  10 history
[root@esxi01pooja:~] history
   0 esxcli storage filesystem list
   1 esxcli storage core device list
   2 /etc/init.d/hostd restart
   3 /etc/init.d/vpxa restart
   4 services.sh restart
   5 cat vmware.log
   6 esxcli network firewall get
   7 esxcli system time get
   8 /etc/init.d/ntpd restart
   9 vim-cmd vimsvc/license --show
  10 history
[root@esxi01pooja:~] exit

