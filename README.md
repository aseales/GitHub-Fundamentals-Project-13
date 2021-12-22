# GitHub Fundamentals Project 13
ELK Stack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
https://github.com/aseales/GitHub-Fundamentals-Project-13/blob/53d5c861603527c3a220cd6200fd68df1f33c3e9/Images/Azure%20Resource%20Group%20Diagram%201.4.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

ansible-playbook /etc/ansible/pentest.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly scalable, in addition to restricting traffic to the network.

Load balancers play a roll in protecting against DDOS attacks
A jump box provides a segregation layer that sits between a network and the user. Managing and distributing traffic into a network preventing failure due to spikes and overloads in traffic.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- Moniotors log events
- Collects statistics and metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK VM   | Monitor  | 10.0.0.4   | Linux            |
| Web-1    |Container | 10.1.0.5   | Linux            |
| Web-2    |Container | 10.1.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
ELK: 10.0.0.4
Web-1: 10.1.0.5
Web-2: 10.1.0.6


Machines within the network can only be accessed by Jump-Box.
Jump-Box
Public: 52.142.44.90
Private: 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| Web-1    | No                  | 10.1.0.5                     |
| Web-2    | No                  | 10.1.0.6                     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
  Removes human error and reduces configuration time

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
... install docker
... install python3-pip
... download and run the sebp/elk:761 container
... SSH from your Ansible container to your ELK machine to verify the connection
... SSH to your container and double check that your elk-docker container is running

- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/aseales/Boot-Camp/blob/main/Images/Screenshot%20ELK%208.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  Web-1: Private IP: 10.1.0.5
         Public IP:  52.188.66.3
  Web-2: Private IP: 10.1.0.6
         Public IP:  52.188.66.3

We have installed the following Beats on these machines:
  Metricbeat
  Filebeat

These Beats allow us to collect the following information from each machine:
  Metricbeat collects metrics and statistics from services running on the server and from the operating system. CPU usage, memory, file system, disk and network IO statistics     are all monitored. Filebeat centralizes and forwards log data. It logs information about the system as to which flis have been changed and when. Both metricbeat and filebeat     are considered lightweight shippers.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible file.
- Update the ansible file to include...
- Run the playbook, and navigate to DVWA to check that the installation worked as expected.

- Which file is the playbook? 
  -   /etc/ansible/ansible.cfg 
- Where do you copy it?
  -   /etc/ansible/hosts
- Which file do you update to make Ansible run the playbook on a specific machine? 
  -   /etc/ansible/pentest.yml
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- Which URL do you navigate to in order to check that the ELK server is running?
  -   http://40.86.225.220:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
    ansible-playbook /etc/ansible/pentest.yml
    nano /etc/ansible/pentest.yml
