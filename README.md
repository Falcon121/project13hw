## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(project13hw/Images/Diagrams/network_diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.
/etc/ansible/ansible.cfg- configure file for ansible
/etc/ansible/roles/my-playbook.yml - downloads webservers 
/etc/ansible/roles/elk.yml - downloads elk server
/etc/ansible/roles/metricbeat-playbook.yml - installs metricbeat
/etc/anisble/roles/filebeat-playbook.yml - installs filebeat
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting access to the network.
-It off loads a server to keep data flow and protects against DDos attacks. A Jumpbox allows you to securly connect to a computer before launchng any task.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics.
- Filebeat watches log files and other locations on a  that you choose to specify.
- _Metricbeat takes metric and statistic data that it collects from your server and outputs to where you choose.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System   |
|----------|----------|------------|--------------------|
| Jump Box | Gateway  | 10.0.0.10  | Linux |Ubuntu 20.04|         |
|----------|----------|------------|-------|------------|
| Web1 VM  | Web server | 10.0.0.8 | Linux |Ubuntu 20.04|
| Web2 VM  | Web server | 10.0.0.9 | Linux |Ubuntu 20.04|
| Elk      | Elk server | 10.1.0.4 | Linux |Ubuntu 20.04|

### Access Policies

The machines on the internal network are not exposed to the public Internet.
Web2 10.0.0.9
Web1 10.0.0.8
Elk  10.1.0.4

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My personal IP address

Machines within the network can only be accessed by azureuser.
- Jump Box 10.0.0.10 can access the elk server.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | My IP                | 
| Web1     | No                  | 10.0.0.10            |
| Web2     | No                  | 10.0.0.10            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it cuts down on repetitive tasks. 
What is the main advantage of automating configuration with Ansible? It cuts down on repetitive tasks. Its human readable and easy to use. 

The playbook implements the following tasks: The playbook records and execute ansible configurations deployment and control functions.
- It installs Docker and downloads images that gives instructions to build the docker container.
- Python3;Docker modules; increases virtual memory;use more memory; downloads and launches a docker elk container and enables service docker on boot.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-: List the IP addresses of the machines you are monitoring_
Web1 server 10.0.0.8
Web2 server 10.0.0.9
We have installed the following Beats on these machines:
-Filelbeat and Metricbeat

These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat - collects and ships log files, which is used to track things like audit logs. 
Metricbeat - collects reports on system metrics, for example it can track a systems cpu or memory data.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the /etc/ansible/ansible.config file to /etc/ansible directory.
- Update the ansible.config file to include new remote_user
- Run the playbook, and navigate to /etc/ansible/ansible.cfg to check that the installation worked as expected.

_Answer the following questions to fill in the blanks:_
- The playbook are yml(YAML) files and is copyed to /etc/ansible/roles
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?You have to update the ansible.cfg and playbook.yml to specify which machine gets the install. To determine which machine to have a elk and the other filebeat installed on you will have to edit the yml file and specify which machine gets that file under the name and hosts. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://40.83.7.121:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ssh azureuser@JumpboxIP
sudo docker pull cybersecurity/ansible
sudo docker container list -a
sudo docker run mystifying_euler
sudo docker start mystifying_euler
sudo docker attach mystifying_euler
cd /etc/ansible
ansible all -m ping
ansible-playbook your-playbook.yml

