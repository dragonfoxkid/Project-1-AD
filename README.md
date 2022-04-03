# Project-1-AD
Project 1 for UTSA-VIRT-CYB-PT-12-2021-U-LOL 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![The ELK Diagram](https://github.com/dragonfoxkid/Project-1-AD/blob/670525d2e4474acb941f21c778ed43796573d5b2/ELK%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

- _[install-elk.yml](https://github.com/dragonfoxkid/Project-1-AD/blob/ca320b18d57d5d887d07355a9906900e96e943b3/install-elk.yml%20%5BTEXT%20FILE%5D)_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use (Filebeat and Metricbeat)
  - Machines Being Monitored (Web-1 and Web-2)
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load balancers will protect the system from DDOS attacks by constantly shifting attack traffic. The advantage to having a jump box is giving access to a single secured node to the user.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
Filebeat searches for information from the file system that has been altered and when it was altered.
Metricbeat will collect the metrics and statistics and will ship them out to whatever output you specify.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| ELK      | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 99.26.205.1

Machines within the network can only be accessed by Jump-Box_Provisioner, IP: 13.89.56.241.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible |    Allowed IP Addresses    |
|----------|---------------------|----------------------------|
| Jump Box | Yes                 | Home IP Address            |
| Web-1    | No                  | 52.165.26.179 (RedTeam-LB) |
| Web-2    | No                  | 52.165.26.179 (RedTeam-LB) |
| ELK      | Yes                 | Home IP Address            |

### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _You can repeat this process for any server that you need without having to provide much input._

The playbook implements the following tasks:
- _install docker.io_
- install pip3
- install python
- increase virtual memory
- download and launch a docker elk docker_container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps -a output](https://github.com/dragonfoxkid/Project-1-AD/blob/926378f4db75b090d12b985f7888fcbd16b7e563/docker%20ps%20-a%20output.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1: 10.0.0.5_
- Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- _Filebeat_
- Metricbeat

These Beats allow us to collect the following information from each machine: Filebeat will perform system log management and collect data like sudo commands, ssh logins, and the creation of new users and groups. Metricbeat will be connected to DVWA and tracks CPU usage, memory, and the number of containers in the system.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to the control node.
- Update the host file to include the ip addresses on the network,
- Run the playbook, and navigate to http://[ELK ip address]:5601/app/kibana to check that the installation worked as expected.
