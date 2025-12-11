
# VMware + Ansible Lab

This repository contains **Ansible playbooks and configuration files** for learning how to automate VMware vCenter, ESXi hosts, and virtual machines. The lab demonstrates tasks such as:

- Testing vCenter connectivity  
- Gathering ESXi host facts  
- Creating and managing vSphere Distributed Switches (VDS)  
- Adding ESXi hosts to a VDS  
- Automating VMware tasks for practice and learning  


## Prerequisites

Before starting, make sure you have:

- Ubuntu (22.04 LTS recommended)  
- Ansible installed  
- Python 3 and pip  
- VMware vCenter Server and ESXi hosts accessible from your lab environment  
- VS Code (optional) for editing playbooks and viewing outputs  


## Step 1: Clone the Repository

Open a terminal and run:

```bash
cd ~
git clone https://github.com/srinithyareddysn/vmware-ansible.git
cd vmware-ansible


## Step 2: Install VS Code (Optional)

```bash
sudo snap install code --classic
code --version


You can open the repository in VS Code:

```bash
code ~/vmware-ansible


## Step 3: Install Required Packages

Install Ansible, Git, Python, and pip:

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y ansible git python3-pip

Install the VMware Python SDK (`pyvmomi`) for Ansible to communicate with vCenter:

```bash
python3 -m pip install --user "pyvmomi>=8.0.0" --break-system-packages


Install the VMware Ansible collection:

```bash
ansible-galaxy collection install community.vmware
ansible-galaxy collection list | grep vmware

## Step 4: Configure Inventory

Edit `inventory.yml` to define your vCenter and ESXi hosts:

```yaml
all:
  hosts:
    localhost:
      ansible_connection: local

  children:
    vcenter:
      hosts:
        vcenter1:
          ansible_host: "vcenter.yourlab.local"  # Replace with your vCenter hostname or IP
          ansible_connection: local


## Step 5: Configure vCenter Variables

For sensitive information (username/password), **do not hardcode in playbooks**. Instead, use `group_vars/all.yml`:

```yaml
# group_vars/all.yml
primary_esxi_hostname: "esxinitya.yourlab.local"
vcenter_hostname: "vcenter.yourlab.local"
vcenter_username: "administrator@vsphere.local"
vcenter_password: "<YOUR_PASSWORD>"
validate_certs: false
esxi_facts_output_dir: "/home/<username>/vmware-ansible/artifacts/session2"


> Replace `<YOUR_PASSWORD>` with your actual vCenter password.
> Replace `<username>` with your Ubuntu username.


## Step 6: Update /etc/hosts (Optional)

If your lab environment does not have DNS configured, add vCenter and ESXi host IPs to `/etc/hosts`:

```bash
sudo nano /etc/hosts


Example:


172.30.30.13  vcenter.yourlab.local
172.30.30.176 esxinitya.yourlab.local


Test connectivity:

```bash
ping -c 4 vcenter.yourlab.local
ping -c 4 esxinitya.yourlab.local


## Step 7: Run Playbooks

### 1. Test vCenter Connectivity

```bash
ansible-playbook -i inventory.yml playbooks/vcenter_about.yml


This checks connectivity and basic info from vCenter.

### 2. Gather ESXi Host Facts

```bash
ansible-playbook -i inventory.yml playbooks/get_esxi_host_facts.yml


* The playbook collects facts about the ESXi host and saves them to a JSON file:

~/vmware-ansible/artifacts/session2/<esxi_ip>_facts.json


* Open the JSON file in VS Code:

```bash
code ~/vmware-ansible/artifacts/session2/<esxi_ip>_facts.json


## Step 8: Create a vSphere Distributed Switch (VDS) and Add Host

* The playbook can create a VDS in vCenter and add ESXi hosts.
* Ensure that the ESXi host is **not already part of another VDS** and has free uplinks (vmnics).
* After running the playbook, verify in the vCenter Web Client.

## Step 9: Check Outputs

* **Artifacts folder:** Contains JSON facts for each ESXi host.
* **VS Code:** Open `.json` files or the playbook output logs for easy reading.
* Optional: Add a task in the playbook to generate a **short summary report**.

## Notes

* Always avoid storing passwords in the repository. Use `group_vars` or Ansible Vault for security.
* Make sure ESXi hosts are reachable and SSH/ESXi Shell is enabled if required.
* If you encounter connection issues, verify network, firewall, and vCenter certificates.

## Author

Srinithya Reddy
Email: [srinithyareddysn@gmail.com](mailto:srinithyareddysn@gmail.com)

