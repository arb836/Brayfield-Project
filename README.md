# Brayfield-Project
Included is a detailed description and supporting documents concerning the network and virtual machines created for the in class project.
The files in this repository were used to configure the network depicted below.

![Images/Project_Diagram.drawio.png](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/install-elk.yml
  

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- Load balancers balance traffic between servers and and protect against DDoS attacks by channeling DDoS traffic. A jump box allows access to multiple machines on separate security zone from a single machine and essentially acts as bridge between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat monitors and collects log data from a server
- Metricbeat collects metrics and statistics and moves them to a specified output.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | server   | 10.0.0.7   | Linux            |
| Web-2    | server   | 10.0.0.8   | Linux            |
| Elkvm    | server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.87.144.86

Machines within the network can only be accessed by _____.
- Jump box vm, ip 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 75.87.144.86         |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elkvm    | yes                 | 10.0.0.4 75.87.144.86|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- You can use a single playbook to send commands to multiple servers

The playbook implements the following tasks:
- Install: docker.io
- Install: python-pip
- Increase virtual memory
- Command: sysctl -w vm.max_map_count=262144
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Images/Capture_docker_ps.png](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.7 and Web-2 10.0.0.8

We have installed the following Beats on these machines:
- Web-1 10.0.0.7 and Web-2 10.0.0.8

These Beats allow us to collect the following information from each machine:
- Filebeat collects and audits log data and sets log events to understand how the files on the systems are changing. Metricbeat collects statistics and metrics, for instance, it can be used to compile statistical data concerning traffic coming to and from a server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.


- filebeat-config.yml, /etc/ansible/file/filebeat-configuration.yml
- edit the /etc/ansible/host file to specify webserver and elkserver ip addresses
- http://20.127.44.205:5601/app/kibana

