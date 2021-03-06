# Project1
Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(https://github.com/davebeiler/Project1/blob/main/Screen%20Shot%202021-06-10%20at%208.38.13%20PM.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the select file may be used to install only certain pieces of it, such as Filebeat.

  Enter the playbook file.while inside the docker container ansible: root# Ansible-playbook pentest.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting load balancing to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Allows only my computer access to my AWS network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system monitor.
- What does Filebeat watch for? monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
- What does Metricbeat record? takes the metrics and statistics that it collects and ships them to the output that you specify

The configuration details of each machine may be found below.

| Name     | Function              | IP Address | Operating System |
|----------|-----------------------|------------|------------------|
| Jump Box | Gateway               | 10.0.0.1   | Linux            |
| web1     | External Web server 1 | 10.1.0.7   | Linux            |
| web2     | External Web server 2 | 10.1.0.8   | Linux            |
| web3     | External Web server 3 | 10.2.0.1   | Linux            |
| elk      | Provides              | 10.4.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses:
  99.22.252.XX (home IP Address)

Machines within the network can only be accessed by Jumpbox.
- Which machine did you allow to access your ELK VM? What was its IP address? 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | my home IP.          |
| Elk      | No                  | my home IP.          |
| web1, web2, web3 | yes         | my home IP.          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  Allows you to edit many machines with just 1 file, not having to repeat yourself

The playbook implements the following tasks:
- Adds more memory
- Installs Dockerio
- installs pip3
- install docker python via pip
- installs elk stack and configures Ports

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
(https://github.com/davebeiler/Project1/blob/main/Screen%20Shot%202021-06-10%20at%208.55.42%20PM.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-  Monitoring 10.1.0.7/10.1.0.8 and 10.2.0.7 web servers

We have installed the following Beats on these machines:
- webserver 1, 2, and 3

These Beats allow us to collect the following information from each machine:
- log files for web server 1, 2, and 3
- provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config and filebeat-playbook file to /etc/ansible/files after starting the docker containing and being root.
- Update the host files file to include your web servers for the [webserver] group and the [elk servers] group
- Run the playbook, and navigate to elk server to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? filebeat-playbook.yml gets copied to the ansible directory, /etc/ansible
- Which file do you update to make Ansible run the playbook on a specific machine? hosts file
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- see above 
- _Which URL do you navigate to in order to check that the ELK server is running?
- the ip address of the server :5601/ followed afterwards
