# Elk-Stack-Azure-Cloud-
Elk Stack deployed on the Azure Cloud
+ Linux and Ansible scripts

------------------------------------------------------------------------------------------

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Folder: mperina11/Elk-Stack-Azure-Cloud

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.
Folder: mperina11/Elk-Stack-Azure-Cloud/Container_Files

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly persistent, in addition to restricting access to the network.
-Load Ba balancers protect against DOS attacks, distribute network traffic, and can be configured with 
 a health probe to monitor the state of different machines behind the load balancer.
-The advantage of a Jump Box is to create a single controllable access point to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system configurations.
-Filebeat collects information about the filesystem.
-Metricbeat collects information about machine metrics such as up time 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux Ubuntu     |
| DVWA     | Filebeat | 10.0.0.6   | Linux Ubuntu     |
| ELK      | Elk Stack| 10.0.0.7   | Linux Ubuntu     |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Personal IP

Machines within the network can only be accessed by the Jump Box.
- The DVWA reports its finding from Filebeat to the ELK VM.
The Jump Box has SSH access to the ELK VM

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Personal IP          |
| DVWA     | No                  | 10.0.0.1, 10.0.0.7   |
| ELK      | No                  | 10.0.0.1, 10.0.0.6   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The ansible playbook (once set up correctly) will execute its commands perfectly every time, eliminating human error.
-Also, a playbook can easily be edited, exported, and used to configure multiple machines.

The playbook implements the following tasks:
-Installs docker.io
-Installs pip (python)
-Installs docker python module
-Increases virtual memory
-Downloads and launches a docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
mperina11/Elk-Stack-Azure-Cloud/ScreenShots/ELF_docker_ps.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.1, 10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
-Filebeat and Metricbeat on DVWA

These Beats allow us to collect the following information from each machine:
-Filebeat: data about the filesystem (ex. changes to filesystem)
-Metricbeat: data about the machine metrics (ex. how long the machine is on)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
-Edit ~/ansible/hosts
-Edit ~/ansible/ansible.cfg
-Copy the 'install-elk.yml' file (may need to edit hosts and remote_user)
-Run the playbook with 'ansible-playbook <filename>'

-URL to view Kibana page for ELK Stack ' http://<ELK VM IP HERE>:5601 '

*To see ELK Stack statistics
Folder: mperina11/Elk-Stack-Azure-Cloud/ELK_Stats
-folder inlcudes screenshots of map and logs of failed SSH logins, SSH logs, SYSLogs, new users and groups


