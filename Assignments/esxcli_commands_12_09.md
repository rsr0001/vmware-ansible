ubuntukn@ubuntukn-VirtualBox:~$ ssh root@172.30.30.171
(root@172.30.30.171) Password: 
The time and date of this login have been sent to the system logs.

WARNING:
   All commands run on the ESXi shell are logged and may be included in
   support bundles. Do not provide passwords directly on the command line.
   Most tools can prompt for secrets or accept them from standard input.

VMware offers powerful and supported automation tools. Please
see https://developer.vmware.com for details.

The ESXi Shell can be disabled by an administrative user. See the
vSphere Security documentation for more information.
[root@esxi01nitya:~] esxcli system hostname get
   Domain Name: 
   Fully Qualified Domain Name: esxi01nitya
   Host Name: esxi01nitya
[root@esxi01nitya:~] esxcli system version get
   Product: VMware ESXi
   Version: 9.0.0
   Build: Releasebuild-24755229
   Update: 0
   Maintenance: 0
   Patch: 0

[root@esxi01nitya:~] esxcli hardware clock get
2025-12-21T14:21:33Z
[root@esxi01nitya:~] esxcli system version get
   Product: VMware ESXi
   Version: 9.0.0
   Build: Releasebuild-24755229
   Update: 0
   Maintenance: 0
   Patch: 0
[root@esxi01nitya:~] esxcli network nic list
Name    PCI Device    Driver    Admin Status  Link Status  Speed  Duplex  MAC Address         MTU  Description
------  ------------  --------  ------------  -----------  -----  ------  -----------------  ----  -----------
vmnic0  0000:02:01.0  nvmxnet3  Up            Up           10000  Full    00:50:56:b3:6c:01  1500  VMware Inc. vmxnet3 Virtual Ethernet Controller
[root@esxi01nitya:~] esxcli network ip interface ipv4 get
Name  IPv4 Address   IPv4 Netmask   IPv4 Broadcast  Address Type  Gateway      DHCP DNS
----  -------------  -------------  --------------  ------------  -----------  --------
vmk0  172.30.30.171  255.255.255.0  172.30.30.255   STATIC        172.30.30.1     false
[root@esxi01nitya:~] esxcli storage core device list
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
   Is SSD: true
   Is VVOL PE: false
   Is Offline: false
   Is Perennially Reserved: false
   Queue Full Sample Size: 0
   Queue Full Threshold: 0
   Thin Provisioning Status: unknown
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
[root@esxi01nitya:~] esxcli storage core adapter rescan --all
[root@esxi01nitya:~] esxcli software vib list
Name                           Version                               Vendor  Acceptance Level  Install Date  Platforms
-----------------------------  ------------------------------------  ------  ----------------  ------------  ---------
atlantic                       1.0.3.0-15vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
bcm-mpi3                       8.11.6.0.0.0-1vmw.900.0.24755229      VMW     VMwareCertified   2025-12-06    host
bnxtnet                        226.0.30.0-40vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
bnxtroce                       226.0.30.0-40vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
cndi-igc                       1.2.11.0-1vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
dwi2c                          0.1-7vmw.900.0.24755229               VMW     VMwareCertified   2025-12-06    host
elxnet                         12.0.1251.0-8vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
i40en                          2.6.0.31-1vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
iavmd                          9.0.0.1100-3vmw.900.0.24755229        VMW     VMwareCertified   2025-12-06    host
icen                           1.14.0.21-1vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
igbn                           1.4.11.9-2vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
intelgpio                      0.1-1vmw.900.0.24755229               VMW     VMwareCertified   2025-12-06    host
ionic-cloud                    24.9.0-11vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
ionic-en                       24.9.0-11vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
irdman                         1.4.0.3-1vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
iser                           1.1.0.3-1vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
ixgben                         1.7.1.47-1vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
lpfc                           900.14.4.390.14-36vmw.900.0.24755229  VMW     VMwareCertified   2025-12-06    host
lpnic                          11.4.62.0-1vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
lsi-mr3                        7.732.03.00-1vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
lsi-msgpt35                    34.00.00.00-1vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
lsi-msgpt3                     17.00.13.00-3vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
ne1000                         0.9.3-1vmw.900.0.24755229             VMW     VMwareCertified   2025-12-06    host
nenic-ens                      1.0.9.2-1vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
nenic                          1.0.35.0-8vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
nfnic                          5.0.0.44-2vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
nhpsa                          70.0051.0.100-5vmw.900.0.24755229     VMW     VMwareCertified   2025-12-06    host
nipmi                          1.0-1vmw.900.0.24755229               VMW     VMwareCertified   2025-12-06    host
nmlx5-cc                       4.24.0.7-16vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
nmlx5-core                     4.24.0.7-16vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
nmlx5-rdma                     4.24.0.7-16vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
ntg3                           4.1.15.0-4vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
nvme-pcie                      1.4.0.2-1vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
nvmerdma                       1.0.3.10-1vmw.900.0.24755229          VMW     VMwareCertified   2025-12-06    host
nvmetcp                        2.0.0.1-1vmw.900.0.24755229           VMW     VMwareCertified   2025-12-06    host
nvmxnet3-ens                   2.0.0.23-24vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
nvmxnet3                       2.0.0.31-16vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
pvscsi                         0.1-7vmw.900.0.24755229               VMW     VMwareCertified   2025-12-06    host
qcnic                          1.0.15.0-23vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
qedentv                        3.40.5.75-11vmw.900.0.24755229        VMW     VMwareCertified   2025-12-06    host
qedrntv                        3.40.5.75-11vmw.900.0.24755229        VMW     VMwareCertified   2025-12-06    host
qfle3                          1.0.67.0-37vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
qfle3f                         1.0.51.0-34vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
qfle3i                         1.0.15.0-21vmw.900.0.24755229         VMW     VMwareCertified   2025-12-06    host
rdmahl                         1.0.0-1vmw.900.0.24755229             VMW     VMwareCertified   2025-12-06    host
rshim-net                      0.1.0-1vmw.900.0.24755229             VMW     VMwareCertified   2025-12-06    host
rshim                          0.1-13vmw.900.0.24755229              VMW     VMwareCertified   2025-12-06    host
sfvmk                          2.4.0.2010-19vmw.900.0.24755229       VMW     VMwareCertified   2025-12-06    host
smartpqi                       90.4800.0.5000-2vmw.900.0.24755229    VMW     VMwareCertified   2025-12-06    host
vmkata                         0.1-1vmw.900.0.24755229               VMW     VMwareCertified   2025-12-06    host
vmksdhci                       1.0.3-7vmw.900.0.24755229             VMW     VMwareCertified   2025-12-06    host
vmkusb                         0.1-28vmw.900.0.24755229              VMW     VMwareCertified   2025-12-06    host
vmw-ahci                       2.0.17-1vmw.900.0.24755229            VMW     VMwareCertified   2025-12-06    host
bmcal                          9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
clusterstore                   9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
cpu-microcode                  9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
crx                            9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
drivervm-gpu-base              9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
esx-base                       9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
esx-dvfilter-generic-fastpath  9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
esx-ui                         9.0.0.0-24645992                      VMware  VMwareCertified   2025-12-06    host
esx-update                     9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
esx-xserver                    9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
esxio-combiner                 9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
gc                             9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
infravisor                     9.0.0-24524131                        VMware  VMwareCertified   2025-12-06    host
loadesx                        9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
lsuv2-hpv2-hpsa-plugin         1.0.0-5vmw.900.0.24755229             VMware  VMwareCertified   2025-12-06    host
lsuv2-intelv2-nvme-vmd-plugin  2.7.2173-2vmw.900.0.24755229          VMware  VMwareCertified   2025-12-06    host
lsuv2-lsiv2-drivers-plugin     1.0.4-3vmw.900.0.24755229             VMware  VMwareCertified   2025-12-06    host
lsuv2-nvme-pcie-plugin         1.0.0-2vmw.900.0.24755229             VMware  VMwareCertified   2025-12-06    host
lsuv2-oem-dell-plugin          1.1.0-3vmw.900.0.24755229             VMware  VMwareCertified   2025-12-06    host
lsuv2-oem-lenovo-plugin        1.0.0-3vmw.900.0.24755229             VMware  VMwareCertified   2025-12-06    host
lsuv2-smartpqiv2-plugin        1.0.0-12vmw.900.0.24755229            VMware  VMwareCertified   2025-12-06    host
native-misc-drivers            9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
nsx-adf                        9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-cfgagent                   9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-context-mux                9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-cpp-libs                   9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-esx-datapath               9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-exporter                   9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-host                       9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-ids                        9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-monitoring                 9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-mpa                        9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-nestdb                     9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-netopa                     9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-opsagent                   9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-platform-client            9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-proto2-libs                9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-proxy                      9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-python-logging             9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-python-protobuf            9.0.0.0-9.0.24499934                  VMware  VMwareCertified   2025-12-06    host
nsx-python-utils               9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-sfhc                       9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-shared-libs                9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-snproxy                    9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsx-vdpi                       9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
nsxcli                         9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
podvm-router                   9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
qlnativefc                     5.4.82.0-3vmw.900.0.24755229          VMware  VMwareCertified   2025-12-06    host
trx                            9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vcls-pod-crx                   9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vdfs                           9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vds-vsip                       9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vmware-esx-esxcli-nvme-plugin  1.4.0.2-1vmw.900.0.24755229           VMware  VMwareCertified   2025-12-06    host
vmware-fdm                     9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vmware-hbrsrv                  9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vsan                           9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vsanhealth                     9.0.0-0.24755229                      VMware  VMwareCertified   2025-12-06    host
vsipfwlib                      9.0.0.0-9.0.24733064                  VMware  VMwareCertified   2025-12-06    host
tools-light                    13.0.0-0.24755229                     VMware  VMwareCertified   2025-12-06    host
[root@esxi01nitya:~] esxcli software vib install -v /vmfs/volumes/datastore1/vibf
ile.vib
[root@esxi01nitya:~] # List all VMs
[root@esxi01nitya:~] vim-cmd vmsvc/getallvms
Vmid                     Name                                                                          File                                                          Guest OS     Version   Annotation
1698   vCLS-6b723342-8292-1962-f970-0422f48bc6ea   [] /var/run/crx/infra/vCLS-6b723342-8292-1962-f970-0422f48bc6ea/vCLS-6b723342-8292-1962-f970-0422f48bc6ea.vmx   crxSys1Guest   vmx-21              
[root@esxi01nitya:~] # Get power state
[root@esxi01nitya:~] vim-cmd vmsvc/power.getstate 1698
Retrieved runtime info
Powered off
[root@esxi01nitya:~] # Power on
[root@esxi01nitya:~] vim-cmd vmsvc/power.on 1698
Powering on VM:
Power on failed: (vim.fault.GenericVmConfigFault) {
   faultCause = (vmodl.MethodFault) null, 
   faultMessage = (vmodl.LocalizableMessage) [
      (vmodl.LocalizableMessage) {
         key = "msg.hvuser.NoSVM", 
         arg = <unset>, 
         message = "This host does not support AMD-V."
      }, 
      (vmodl.LocalizableMessage) {
         key = "msg.cpuid.legacyCPU.noVHV", 
         arg = <unset>, 
         message = "This host appears to be running in a virtual machine with VHV disabled. Ensure that VHV is enabled in the virtual machine configuration file."
      }, 
      (vmodl.LocalizableMessage) {
         key = "msg.moduletable.powerOnFailed", 
         arg = (vmodl.KeyAnyValue) [
            (vmodl.KeyAnyValue) {
               key = "1", 
               value = "MonitorMode"
            }
         ], 
         message = "Module 'MonitorMode' power on failed.
"
      }, 
      (vmodl.LocalizableMessage) {
         key = "msg.vmx.poweron.failed", 
         arg = <unset>, 
         message = "Failed to start the virtual machine."
      }
   ], 
   reason = "This host does not support AMD-V."
   msg = "This host does not support AMD-V."
}
[root@esxi01nitya:~] # Reset VM
[root@esxi01nitya:~] vim-cmd vmsvc/power.reset 1698
Reset VM:
Reset failed: (vim.fault.InvalidPowerState) {
   faultCause = (vmodl.MethodFault) null, 
   faultMessage = <unset>, 
   requestedState = "poweredOn", 
   existingState = "poweredOff"
   msg = "The attempted operation cannot be performed in the current state (Powered off)."
}
[root@esxi01nitya:~] exit
Connection to 172.30.30.171 closed.
ubuntukn@ubuntukn-VirtualBox:~$ 
