## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting external access to the network.
- A load balancer helps defends against distributed denial of service attacks (DDoS)
- The advantage of using a jumpbox is that it allows management of all devices on the network

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

- Filebeat collects log events and forwards them to Elasticsearch for indexing. Metricbeat then takes the metrics and statistics that collects and ships thyem to the output that you specify, such as elasticsearch.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.8   | Linux            |
| Web-1    | Webserver| 10.0.0.9   | Linux            |
| Web-2    | Webserver| 10.0.0.10  | Linux            |
| Elk      | Log Server| 10.1.0.4  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 209.172.18.101

Machines within the network can only be accessed by Jump Box with ansible and docker container.
- 10.0.0.8

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              	 | 209.172.18.101       |
| Web-1    | No                  | 10.0.0.8             |
| Web-2    | No                  | 10.0.0.8             |
| Elk      | Yes		 | 209.172.18.101

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because ansible streamlines and simplifies cloud provisioning, configuration management, and application deployment.

The playbook implements the following tasks:
- Install docker.io
- Install Python3-pip
- Install Python Docker Module
- Increase the virtual memory for the container
- Download and Launch the elk container and set the ports that the container runs on

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.9
- 10.0.0.10

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Collects log events and forwards them to Elasticsearch for indexing. Then takes the metrics and statistics that collects and ships thyem to the output that you specify, such as elasticsearch.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config file to `/etc/ansible/roles/' directory.
- Update the hosts file to include the elk IP.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ filebeat-configuration.yml > /etc/filebeat/.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ filebeat-playbook > /hosts/ [elk]
- http://[Elk.IP]:5601/app/kibana#/home
