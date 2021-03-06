## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/network_diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [install-elk.yml] file may be used to install only certain pieces of it, such as Filebeat.

  - [install-elk.yml]

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly [available], in addition to restricting [traffic] to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?[availability]

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the [logs] and system [traffic].
- _TODO: What does Filebeat watch for? [log files and log events]
- _TODO: What does Metricbeat record?  [metrics and statistics]
[Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.]

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name            | Function     | IP Address             | Operating System |
|-----------------|--------------|------------------------|------------------|
| Jump-Box        | Gateway      | 10.0.0.4               | Linux            |
| Web-1           | UbuntuServer | 10.0.0.5               | Linux            |
| Web-2           | UbuntuServer | 10.0.0.6               | Linux            |
| ELKVM           | UbuntuServer | 10.1.0.4               | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the [Jump-Box-Provisioner] machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_[108.2.209.120]

Machines within the network can only be accessed by [Jump-Box-Provisioner through SSH].
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Jump-Box-Provisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly | Allowed IP Addresses |
|----------|----------|----------------------|
| Jump-Box | Yes      | 52.191.85.16         |
| Web-1    | No       | 10.0.0.5             |
| Web-2    | No       | 10.0.0.6             |
| ELKVM    | NO       | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can put one command from multiple servers into a single playbook.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... [install docker IO]
- ... [install python pip]
- ... [install docker]
- ... [systemctl -w vm.max_map_counts=26144]
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_[Web-1 10.0.0.5]
[Web-2 10.0.0.6]

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed [Filebeat]

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc. [Filebeat collects the changes done.]

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below: 
- Copy the [yml] file to [ansible].
- Update the [config] file to include...
- Run the playbook, and navigate to [kibana] to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_[filebeat-playbook.yml] [/etc/ansible/hosts]
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ [edit etc host file to webservers/elk server ip addresses.]
- _Which URL do you navigate to in order to check that the ELK server is running? [http://13.64.176.16:5601/app/kibana#/home]
