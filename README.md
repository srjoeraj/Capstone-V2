
<div align="center">

# Capstone-V2


<br>
This project is an improved version of the capstone project I had done during my final semester in the CSN program at Seneca College. 🚀.
<br><br>

[Description](#description) [Features](#features) [Requirements](#requirements) [Project Structure](#project-structure) [Installation](#installation) [Results](#end-results)
<br>
<br>
<img src="img/output-monokai-2.5">
<div>
<img src="img/cisco-logo-transparent.png" width="65" height="50" alt="cisco-logo" style="float: left; padding: 3px 3px 0px 5px;" />
<img src="img/ubuntu-logo.png" width="50" height="50" alt="ubuntu-logo"  style="float: left; padding: 3px 3px 0px 5px;" />
<img src="img/rocky-logo.png" width="50" height="50" alt="rocky-logo"  style="float: left; padding: 3px 3px 0px 5px;"/>
<img src="img/ansible-logo.png" width="50" height="50" alt="ansible-logo"  style="float: left; padding: 3px 3px 0px 5px;"/>

</div>


</div>


## Description

This project is divided into two parts: the network (along with device configurations) and the second part involves automating the end machines running various services using Ansible. 🌐🤖



## Features

1. 🌐 Security-optimized network topology.
2. ⚙️ Seamless management of end services.
3. 🧩 Modular and easily understandable code.
4. 🔄 Replicable on multiple devices simultaneously.
5. 🐧🎩 Compatible with Debian and RedHat based distributions.


## Requirements

- Real Cisco Switches and Routers. If you wish to implement it on a real network.

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer). Simulation files have been provided in the repository.

- A minimum of 4 end-user machines running Linux belonging to [Debian Family](https://en.wikipedia.org/wiki/Category:Debian-based_distributions) or [RedHat Family](https://en.wikipedia.org/wiki/Red_Hat_Enterprise_Linux_derivatives).
    - I recommend using Rocky/Alma Linux instead of RHEL to avoid issues with the subscription manager.


## Project Structure
```
$PROJECT_ROOT
│   # Ansible Configuration
├── capstone-automation
│   # Network topology and device configurations
└── Network Configuration

```

## Installation
- Clone the repository to access the files.
- Packet Tracer can be installed [here](https://www.netacad.com/courses/packet-tracer). You need to have a Cisco Networking Academy account to be able to install Packet Tracer. 🌐🔧
    - Packet Tracer simulations, along with the configurations, are located at [Network Configuration/Packet-Tracer](https://github.com/srjoeraj/Capstone-V2/tree/main/Network%20Configuration/Packet-Tracer).
- For real Cisco Switches and Routers, you can use [PuTTY](https://putty.org/) to console into the respective device and paste the configuration. 🖥️🔗
  - The complete configuration for each device is located inside [Network Configuration/Real-Devices](https://github.com/srjoeraj/Capstone-V2/tree/main/Network%20Configuration/Real-Devices). 🛠️📄

### For Automating with Ansible

- Install `ssh` if not already installed on the machines.
- Choose one of the machines to act as your Ansible controller.
- Install `python` and `pip3` from your respective package manager.
  - The packages might be named differently based on your distribution.
- Install Ansible using pip: `pip3 install ansible`.
- Edit `capstone-automation/inventory` with the hostnames of all the machines you want to run the playbook.
- On the controller's `/etc/hosts`, add hostnames and IP addresses of all machines that you previously entered in the inventory. 🛠️🔧

- Now, if you've configured everything properly, you can simply run the playbook:
```bash
cd capstone-automation
ansible-playbook main.yaml -b -k -K
```

## End Results
### Network Topology:

#### Layer 2 Configurations:
- **VLAN Configurations:**
  - VLAN 15, 30, 45, 60 for production use.
  - VLAN 250 for management purposes.
  - VLAN 99 for assigning it to unused ports.

- **Protocol Configurations:**
  - VTP (VLAN Trunking Protocol) for dynamic VLAN management.
  - Spanning Tree Protocol for loop prevention.
  - BPDU Guard and Portfast on access ports for enhanced network stability.
  - Etherchannel via LACP for link aggregation.
  - Port Security for access port security.
  - Dynamic ARP Inspection for preventing ARP spoofing attacks.
  - DHCP Snooping for DHCP security.

#### Layer 3 Configurations:
- **Routing and Access Control:**
  - OSPF (Open Shortest Path First) for dynamic routing.
  - ACLs (Access Control Lists) to limit and control network traffic.
  - Port Address Translation (PAT) for network address translation.
  - HSRP (Hot Standby Router Protocol) for high availability.
  - DHCP for dynamic IP address assignment.

- **Management:**
  - SSH configured at port 22225 for secure remote access.

### Playbook Execution Features:

- **User Management:**
  - Users `cp-user`, `cp-admin`, `cp-guest` created.
  - All created users granted root escalation privileges.

- **SSH Configuration:**
  - SSH key-based authentication configured for user `cp-guest` on all hosts.

- **Web Server and Database:**
  - Host-specific `/var/www/html/index.html` created.
  - [Apache web server](https://httpd.apache.org/) hosted on port `8089`.
  - MariaDB installed and partially configured, running on port `6612`.

- **Security Configurations:**
  - [firewalld](https://firewalld.org/) installed and configured to allow only necessary traffic.
  - [SELinux](https://www.redhat.com/en/topics/linux/what-is-selinux) configured where necessary on RedHat family distributions.

- **Development Tools:**
  - [Vim](https://github.com/vim/vim) installed to edit text.

## Author

This project has been made by [Rohan Rajguru](https://srjoeraj.github.io/site/). You can view my other repos [here](https://github.com/srjoeraj/). 🚀🌐
