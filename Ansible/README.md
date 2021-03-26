## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](~/Chris/ELK_Stack_Project/Diagrams/CML_Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

- _TODO: Enter the playbook file: filebeat-playbook.yml (both filebeat and metricbeat playbooks are stored within this file)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly DYNAMIC_, in addition to restricting ACCESS to the network.
# _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

-  Load balancers protect unwanted trafficfrom entering the network. They can help protect from DDOS attacks, SQL 
 injection, and XSS (cross-site scripting). 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the CONFIGURATION and system FILES.

# _TODO: What does Filebeat watch for?_

- Filebeat monitors log files, specified locations, collects & logs events, and them forwards them to Kibana for record keeping.

# _TODO: What does Metricbeat record?_

- It collects metrics on the operating system and from running services. It outputs the data (metrics and statistics)
and can also send them to Kibana or the output of your choosing.
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Elk-VM2  |Web Server| 10.2.0.4   |  "               |
| WEB-1    |    "     | 10.0.0.6   |  "               |
| WEB-2    |    "     | 10.0.0.9   |  "               |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMPBOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 172.10.129.37

Machines within the network can only be accessed by the Jumpbox provisioner

#_TODO: Which machine did you allow to access your ELK VM? What was its IP address?
- My Jumpbox Provisioner had access to the ELK VM, the IP address was 138.91.227.208

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
| WEB-1    | No                  | 172.10.129.37        |
| WEB-2    | No                  | 172.10.129.37        |
| ELK-VM2  | SSH-No HTTP-Yes     | 172.10.129.37        |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

# _TODO: What is the main advantage of automating configuration with Ansible?
- It is advantageous to use Ansible for multiple reasons, within the ansible configuration file you can set specific goups to configure routers, switches, machines, and more. 
  You can call on these groups and run the playbook and apply your specific settings. Another reason this is advantageous is because if you had chosen to update a certain program
  throughout your machines and one out of lets say 5 was previously updated, ansible will not make any changes to that machine. If you choose to write your own script to make these 
  changes, there is a good chance that the script will not check to see if those changes have been made previously and could potentially cause problems by forcing whatever is in
  the script. Automation is the key word that makes ansible advantageous. 

The playbook implements the following tasks:
# In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker.io onto the system
- Install python-3 pip
- install python package docker
- Sownload ELK image and open ports for kibana to use.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Jumpbox: 138.91.227.208
- Web-1: 137.135.9.59 10.0.0.6
- Web-2: 137.135.9.59 10.0.0.9

We have installed the following Beats on these machines:
- filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors changes made withion the system 
- Metricbeat is set to monitor metrics such as RAM and other resources.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to etc/ansible/roles.
- Update the /etc/ansible/hosts file to include...
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

# Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
 My file fore the playbook is labed filebeat-playbook.yml and it was copied to /etc/ansible/rules
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
 You have to update the asible configuration file. You have to add the correct IP inside of the configuration to call on the ELK server.
- _Which URL do you navigate to in order to check that the ELK server is running?
Http://172.10.129.37:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
