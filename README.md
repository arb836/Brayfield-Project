# Brayfield-Project
Included is a detailed description and supporting documents concerning the network and virtual machines created for the in class project.
The files in this repository were used to configure the network depicted below.

![Project_Diagram_Final](https://user-images.githubusercontent.com/90295832/147312596-2c86f6e8-2284-428d-95c1-e0ddee06c2ae.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

 
  

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
- Load balancers balance traffic between servers and and protect against DDoS attacks by channeling DDoS traffic. A jump box allows access to multiple machines on separate security zone from a single machine and essentially acts as bridge between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
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

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My public home IP address

Machines within the network can only be accessed by the jumpbox.
- Jump box vm public ip address is 13.78.206.239, and private ip is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | My public home IP    |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elkvm    | yes                 | 10.0.0.4 my public ip|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can use a single playbook to send commands to multiple servers automatically. 

The playbook implements the following tasks:
- Install: docker.io
- Install: python-pip
- Increase virtual memory
- Command: sysctl -w vm.max_map_count=262144
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Capture_docker_ps](https://user-images.githubusercontent.com/90295832/147299191-45c014aa-881b-4f82-897f-db26660ebb86.PNG)


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
- Copy the install-elk.yml file to /etc/ansible/roles/elk_install.yml.
- Update the hosts file to include the IPs of each group so Ansible can determine which machines need to be run on a which playbook
- Run the playbook, and navigate to http://20.127.85.246:5601/app/kibana



