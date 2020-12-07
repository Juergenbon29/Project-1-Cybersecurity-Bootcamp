# Project-1-Cybersecurity-Bootcamp
Unit 13 project from cybersecurity bootcamp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Juergenbon29/Project-1-Cybersecurity-Bootcamp/Diagrams

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - Config web VM with docker.odt
  - Configure ELK VM with docker.odt
  - Install and launch filebeat.odt
  - Install and launch metric beat.odt

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
- Load balnacers protect the availabitly aspect of security. The advantage of a jump box is a single point of access into the virtual network, so connections to
other boxes in the virtual network only need to be configured to access from that one box instead of every different IP to every single VM
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat watches for log data
- Metricbeat records periodic metrics from the operating systems on a network

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELK      | ELK stack| 10.1.0.5   | Linux            |
| Web 1    | Server   | 10.0.0.5   | Linux            |
| Web 2    | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 67.177.7.138

Machines within the network can only be accessed by SSH from the jump box or ansible container.
- Jump box with ansible container IP address is 104.40.81.101

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 67.177.7.138         |
| ELK      | No                  | 10.0.0.4             |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage of automating configuration is only needing to run a playbook once for all the machines instead of going into each machine to configure them one by one

The playbook implements the following tasks:
- Install docker
- Install pip3
- Install python docker module
- Increase virtual memory
- Use the increased memory
- Download and launch docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Juergenbon29/Project-1-Cybersecurity-Bootcamp/Images/docker ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat, which is used to forward and centralize log data from specifies VM's in my network, and Metricbeat which periodically measures system metrics of specified VM's

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/filebeat/filebeat.yml
- Update the filebeat-config.yml file to include ELK IP and port, username, password
- Run the playbook, and navigate to http://[your.ip]:[port]/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ - filebeat-playbook.yml, /etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ - hosts file, in the playbook specify the resource group in the hosts file
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ip]:[port]/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
