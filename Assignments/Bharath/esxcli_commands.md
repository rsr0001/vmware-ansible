# VMware ESXi Command Line commands (ESXCLI)

This is a cleaned, organized, structured version of all commands found in the PDF.

---

## 1. General System & Host Management

### System Information
- `esxcli system version get`
- `esxcli system hostname get`
- `esxcli system stats installtime get`
### Maintenance Mode
- `esxcli system maintenanceMode get`
- `esxcli system maintenanceMode set --enable true`
- `vim-cmd hostsvc/maintenance_mode_enter`
- `vim-cmd hostsvc/maintenance_mode_exit`

### Reboot / Shutdown
- `esxcli system shutdown reboot -r "message"`
- `esxcli system shutdown reboot -d 10 -r "Patch Updates"`

### Hardware
- `esxcli hardware cpu list`
- `esxcli hardware memory get`

### Syslog
- `esxcli system syslog`

### Support Bundle
- `vm-support`

---

## 2. User Accounts

- `esxcli system account list`
- `esxcli system account add -d="Description" -i="username" -p="password" -c="password"`

---

## 3. ESXCLI Help
- `esxcli command getdetails`
- `esxcli esxcli command list`

---

## 4. Virtual Machine Operations

### List VMs
- `vim-cmd vmsvc/getallvms`
- `esxcli vm process list`

### Power Options
- Soft shutdown: `vim-cmd vmsvc/power.off <vmid>`
- Hard kill: `esxcli vm process kill -w <worldID> -t [soft|hard|force]`
- Power on: `vim-cmd vmsvc/power.on <vmid>`
- Reset: `vim-cmd vmsvc/power.reset <vmid>`
- Reboot: `vim-cmd vmsvc/power.reboot <vmid>`
- Shutdown: `vim-cmd vmsvc/power.shutdown <vmid>`

### Suspend & Resume
- `vim-cmd vmsvc/power.suspend <vmid>`
- `vim-cmd vmsvc/power.suspendResume <vmid>`

### VM Summary
- `vim-cmd vmsvc/get.summary <vmid>`

### VM Performance
- `esxtop`

---

## 5. Snapshot Management

### View Snapshots
- `vim-cmd vmsvc/snapshot.get <vmid>`

### Create Snapshot
- `vim-cmd vmsvc/snapshot.create <vmid> "Name" "Description"`
- `vim-cmd vmsvc/snapshot.create <vmid> "Name" "Description" includeMemory`
- `vmware-cmd vmsvc/snapshot createsnapshot "Name" "Description" <vmid> <snapshotid>`

### Remove Snapshot
- `vim-cmd vmsvc/snapshot.remove <vmid> <snapshotid>`
- `vmware-cmd /vmfs/volumes/.../VM.vmx removesnapshots`

### Snapshot Tasks
- `vim-cmd vimsvc/task_list`
- `vim-cmd vimsvc/task_info <taskID>`

---

## 6. Network Commands

### VM Network
- `esxcli network vm list`

### IP Configuration
- `esxcli network ip interface ipv4 get`
- `esxcli network ip interface list`

### NICs
- `esxcli network nic list`
- `esxcli network nic down -n <vmnicid>`

### Routing
- `esxcli network ip route ipv4 list`
- `esxcli network ip route ipv4 add --gateway X.X.X.X --network X.X.X.X/XX`
- `esxcfg-route -a default X.X.X.X`

### ARP
- `esxcli network ip neighbor list`
- `esxcli network ip neighbor remove -a <ip> -v <version>`

### Firewall
- `esxcli network firewall get`
- `esxcli network firewall set --enabled true|false`
- `esxcli network firewall ruleset list`
- `esxcli network firewall ruleset set --ruleset-id=sshClient --enabled=true`
- `esxcli network firewall ruleset allowedip add --ruleset-id sshServer --ip-address X.X.X.X/XX`

### vSwitches
- `esxcli network vswitch standard list`
- `esxcli network vswitch standard uplink remove -u <vmnic> -v <vswitch>`
- `esxcli network vswitch standard uplink add -u <vmnic> -v <vswitch>`

### Portgroups
- `esxcli network vswitch standard portgroup list`
- `esxcli network vswitch standard portgroup add -p "Name" -v <vswitch>`
- `esxcli network vswitch standard portgroup set --vlan-id <id> -p "Name"`

### VMkernel Interfaces
- Create:
  - `esxcfg-vmknic -a -i <IP> -n <MASK> -M <MAC> -p <portgroup>`
- Enable:
  - `esxcfg-vmknic -p <portgroup> -e true`
- Delete:
  - `esxcfg-vmknic -d -p <portgroup>`

### Packet Capture
- `pktcap-uw --uplink <vmnic>`

### Connectivity Tools
- `vmkping -D`
- `vmkping -I <vmk> <ip>`
- `nc -z <ip> <port>`

---

## 7. Storage Commands

### Storage Devices
- `esxcli storage core device list`

### Filesystems
- `esxcli storage filesystem list`

### Storage Paths
- `esxcli storage core path list`
- `esxcli storage core path list -d <device>`
- `esxcli storage vmfs extent list`

### HBA Commands
- `esxcfg-scsidevs -a`
- `esxcli storage san fc list`
- `esxcli storage san fc reset -A <hbaid>`

### VAAI
- `esxcli storage core device vaai status get`

### VMFS Tools
- `vdf`
- `vdu`

---

## 8. Disk Operations

### Extend Disk
- `vmkfstools -X <size> <vmdk>`

### Rename Disk
- `mv <file>.vmdk <new>.vmdk`

### Clone Disk
- `vmkfstools -i <src>.vmdk -d zeroedthick <dest>.vmdk`

### Delete Disk
- `rm <file>.vmdk`

### Convert Thick → Thin
- `vmkfstools -i <disk>.vmdk -d thin <disk-thin>.vmdk`

### Check Sizes
- `ls -lh <disk>.vmdk`
- `du -h <disk>.vmdk`

---

## 9. iSCSI Commands

- `esxcli iscsi software set --enabled true`
- `esxcli iscsi software get`
- `esxcli iscsi sessions`
- `esxcli iscsi adapter param get -A <vmhba>`

---

## 10. SNMP Commands

- `esxcli system snmp set --communities "COMMUNITY"`
- `esxcli system snmp set --targets X.X.X.X/COMMUNITY`
- `esxcli system snmp test`
- `esxcli system snmp get`
- `esxcli system snmp set --hwsrc sensors`
- `esxcli system snmp set --hwsrc indications`
- `esxcli system snmp set --enable true`

---

## 11. Host Services

### ESXi Shell
- `vim-cmd hostsvc/enable_esx_shell`
- `vim-cmd hostsvc/disable_esx_shell`
- `vim-cmd hostsvc/start_esx_shell`

### SSH
- `vim-cmd hostsvc/enable_ssh`
- `vim-cmd hostsvc/disable_ssh`
- `vim-cmd hostsvc/start_ssh`

---

## 12. Advanced Kernel Parameters

- List: `esxcli system settings advanced list -d`
- Set: `esxcli system settings advanced set -o /UserVars/Example -i 0`
