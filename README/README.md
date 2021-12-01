## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

ElkStackDeployment/README/Images/Screenshot 2021-12-01 152958.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the roles directory may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.


The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | DVWA Host| 10.0.0.5   | Ubuntu 18.04     |
| Web 2    | DVWA Host| 10.0.0.6   | Ubuntu 18.04     |
| Elk      | Kibana Host|          |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box and Elk machines can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.242.66.79

Machines within the network can only be accessed by Local Host.

A summary of the access policies in place can be found in the table below.

| Name              | Publicly Accessible | Allowed IP Addresses |
|-------------------|---------------------|----------------------|
| Local to Jump Box | Yes                 | 24.242.66.79         |
| Local to HTTP     | Yes                 | 24.242.66.79         |
| Local to ELK      | Yes                 | 24.242.66.79         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it
gives you more control and time to focus on other tasks and still manage to spin up multiple VMS

The playbook implements the following tasks:
- Installs the Docker apt package
- Installs the python3-pip package
- Sets the vm.max_map_count option in the sysctl.conf fiel to 262144
- Downloads and launches a docker Elk container

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeats purpose is to forward and centralize log data to kibana
-Metricbeat Monitors and collects data form the host os and background services running on the server
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the roles directory and the playbook.yml file to /etc/ansible
- Update the /etc/ansible/hosts file to include the IP addresses of the targe Elk serve and webservers.
- Run the playbook, and navigate to http://[elk_ip_addr]:5601/app/kibana to check that the installation worked as expected.


