# tiki-bah
Accumulation of BootCamp Activities

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(second_diagram.drawio.pdf)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on the network and system metrics.

- Filebeat monitors and collects logs to be examined by either Elasticsearch or Logstash. 

- Metricbeat records metrics and statistics from the operating system and other services on the server and sends them to Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | Web Server | 10.0.0.5   | Linux            |
| Web-2    | Web Server | 10.0.0.6   | Linux            |
| ELK      | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
   75.16.131.36

Machines within the network can only be accessed by each other.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |   75.16.131.36       |
| ELK      | No                  |   10.0.0.4           |
| Web-1    | No                  |   10.0.0.4           |
| Web-2    | No                  |   10.0.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It eliminates IT personnel from having to manually enter all the data.

The playbook implements the following tasks:
- The playbook consists of several requests. For example:       Increasing memory, installing services like docker and python.
- There is ports you can specify for use. (ex 5601:5601)
- It downloads and launches a docker elk container. 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/sudo_docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 and Web-2, 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect information from each machine.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible directory.
- Update the hosts file to include our vm's. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
   
	install-elk.yml is the playbook and it is in the ansible directory. 

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

	The hosts file in the ansible directory needs to be updated to run on a specific machine. To specify which machine to install, change the "hosts" option in the playbook.   

- _Which URL do you navigate to in order to check that the ELK server is running?

	http://13.91.253.16:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
