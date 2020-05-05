### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

### URL to my diagram
[https://github.com/PrincePaulTheTurnt/ElkStackProject/blob/master/ProjectElkNetworkDiagram.PNG](ProjectElkNetworkDiagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  - _https://drive.google.com/file/d/1HHNoViOPdZZIv56YXmVH5Sx459xihaPK/view?usp=sharing_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting connectivity to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system operations.


The configuration details of each machine may be found below.


| Name        | Function | IP Address | Operating System | Public IP
|----------   |----------|------------|------------------|---------------
| Jump Box    | Gateway  | 10.0.0.4   |      Linux       | 137.135.8.235
| DVWA-1      |    VM    | 10.0.0.5   |      Linux       |
| DVWA-2      |    VM    | 10.0.0.6   |      Linux       |
| ElkProjectA |    VM    | 10.0.0.8   |      Linux       | 40.112.134.111

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

137.135.8.235

Machines within the network can only be accessed by SSH through JumpBox.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |        Yes          |    24.235.243.197    |
|  DVWA-1  |         No          |      10.0.0.4        |
|  DVWA-2  |         No          |      10.0.0.4        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this ensures all configurations are performed exactly the same.

The playbook implements the following tasks:
- Defines host and user as root
- Installs docker
- Installs pip- Install
- Installs Python
- Increases virtual memory
- Downloads and launches container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[https://drive.google.com/file/d/1vA6O3fLfi5b9uNfaYE38An3K4j81RkS7/view?usp=sharing](dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA-1        10.0.0.5
- ElkProjectA   10.0.0.8  

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log data, it monitors log files and their locations, log events and log times.
- Metricbeat monitors the machines by collecting metrics from the system and services running, such as MySQL, Apache and Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the  /etc/filebeat/filebeat-configuration.yml file 
  to        /etc/ansible/files/filebeat-configuration.yml
- Update the filebeat-playbook.yml file to include user and IPs
- Run the playbook, and navigate to the Filebeat installation page on the ELK server GUI to check that the installation worked as expected. 
(In this case the URL is  http://40.112.134.111:5601)

**Bonus** Run the command: ansible-playbook filebeat-playbook.yml
to download the playbook, update the files, etc.
