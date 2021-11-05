** Automated ELK Stack Deployment**

The files in this repository were used to configure the network depicted below.

Microsoft_Azure_Project/Diagrams/Network_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select$

  - configure_elk_yml.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting traffic to the network.
- Load balancers can defend an organization against denial-of-service (DDos) attacks. The advantage of having a jumpbox is to be able to use a virtual machine that have hardened$

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic
-Filebeat monitors the log files or locations that you specify.
-Metricbeat records the metrics and statistics from the operation system and from services running on the server.

The configuration details of each machine may be found below.

| Name     | Function       | IP Address | Operating System |
|----------|----------------|------------|------------------|
| Jump Box | Gateway        | 10.0.0.7   | Linux            |
| Web-1    | Webserver      | 10.0.0.12  | Linux            |
| Web-2    | Webserver      | 10.0.0.13  | Linux            |
| ELK      | Webserver      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox virtual machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-68.53.136.115
Machines within the network can only be accessed by;
- JumpBoxProvisioner, public IP: 137.135.118.238 | private IP: 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 68.53.136.115        |
| Web-1    | No                  | 10.0.0.7             |
| Web-2    | No                  | 10.0.0.7             |
| ELK      | No                  | 10.0.0.7             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because manual configuration can be tedious and time consuming, especially if there are multiple machines to be configured. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ≈Installed Docker and Ansible on the Jumpbox machine, enabling playbook automation to push software services to other machines
- Added ELK VM to Hosts file under a separate Group header (elk)
- Run Playbook file via ansible-playbook command, therefore pushing tasks to all machines assigned/configured to receive

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
(Images/docker_ps_output.png)
<img width="1439" alt="docker_ps_output" src="https://user-images.githubusercontent.com/56059854/140459724-320ac258-d264-436e-aad9-c425cd4b9962.png">


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1(10.0.0.12), Web-2(10.0.0.13)

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors files being accessed, authorized or unauthorized e.g passwd, shadow
- Metricbeat monitors metrics such as memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the elk_install.yml file to the yml file
- Update the host file to include the I.P of the ELK 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_  
- /etc/ansible/roles/filebeat-playbook.yml
 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to 
- Install Filebeat $ edit the hosts file [elk] and [webservers]

- _Which URL do you navigate to in order to check that the ELK server is running? 
- http://40.83.148.17:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- Sudo docker start [container name]
- sudo docker attach [container name]
- sudo ansible-playbook [.yml file to run]
