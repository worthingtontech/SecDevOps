## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(https://drive.google.com/file/d/1ciffFO5dLbRw0yI2Oe80gnYD5gC5_xJn/view?usp=sharing)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK_Stack.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting Privileged-access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system stats.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| VM-1     | DVWA     | 10.0.0.5   | Linux            |
| VM-2     | DVWA     | 10.0.0.6   | Linux            |
| VM-3     | DVWA     | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 136.57.161.132
Machines within the network can only be accessed by the JumpBox (10.0.0.1) or public IP:
- 136.57.161.132 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses          |
|----------|---------------------|-------------------------------|
| Jump Box | Yes                 | 136.57.161.132, Any from VNET |
| VM 1-3   | No                  | VNET                          |
| ELK Stack| Yes                 | VNET, 136.57.161.132          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for extremely low downtime for redeployments when necessary. 

The playbook implements the following tasks:
- download and install Docker
- download and install Python
- download and run DVWA container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 21a0f55d4e30   775349758637     "bash"     14 weeks ago     Up 3 seconds   hardcore_brown

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.1,5-7 

We have installed the following Beats on these machines:
- filebeats, metric beats

These Beats allow us to collect the following information from each machine:
- Monitor Windows and Linux logs that include system logons, executables run, modified files, system start/stop, etc. These logs are categorized and visualized in Kibana. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk_Stack.yml file to your ELK server.
- Update the /etc/ansible/hosts file to include your ELK server IP (10.1.0.4)
- Run the playbook, and navigate to http://http://20.98.220.205:5601/app/kibana to check that the installation worked as expected.
