# CyberSecurity_Consultant
This repository depicts the archictecture and deployment tools leveraged to setup MS Azure based virtual network, virtual machines, web applications, and ELK-Stack monitoring function.

## Automated ELK Stack Deployment

The following represents the complete MS Azure based virtual network created as part of this projec:

![Diagram of the Network](https://github.com/jhkgeneral/CyberSecurity_Consultant/blob/main/1-Diagrams/VirtualNetworkArchitecture_Mar2022.drawio.png)

(Images/VirtualNetworkArchitecture_Mar2022.drawio.png)

The summary below may be used to either recreate the entire deployment on MS Azure.  Alternatively, select portions of the configuration and playbook files may be used to install only certain components, such as 'FILEBEAT' or 'METRICBEAT'.

The files referenced have been tested and used to generate a live [ELK Stack](https://www.elastic.co/) deployment on MS Azure. 

<details>
  <summary>This document contains the following sections:</summary>
  <br>

- **Section 1:** Description of the Topology
- **Section 2:** Access Policies
- **Section 3:** ELK Stack Configuration
  - Beats in Use
  - Machines Being Monitored
- **Section 4:** Using Ansible Build & Playbooks
- **Section 5:** FAQ

### Section 1: Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                | Function                         | IP Address | Operating System |
|---------------------|----------------------------------|------------|------------------|
| JumpboxProvisioner  | Gateway                          | 10.0.0.4   | Linux-Ubuntu     |
| Web-1               | Web-App Server                   | 10.0.0.5   | Linux-Ubuntu     |
| Web-2               | Web-App Server                   | 10.0.0.6   | Linux-Ubuntu     |
| ELK-Stack           | Log Analytics & Alerting         | 10.1.0.4   | Linux-Ubuntu     |

### Section 2: Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Section 3: ELK Stack Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- **Accuracy:** Leveraging Ansible to automate the setup of ELK machine helps ensure the accurate configuration of settings and flags, helping to eliminate human error.
- **Completeness:** Leveraging Ansible to automate the setup of ELK machine helps ensure the complete setup of a single machine or many machines, helping to eliminate machines from being missed.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

<details>
  <summary>Click here to view details of target machines & beats:</summary>
  <br>

- **Target Machines:** _The ELK Stack server is configured to monitor the following machines_

  - Web-1
    - Private IP: 10.0.0.5
    - Applications: DVWA
  - Web-2
    - Private IP: 10.0.0.6
    - Applications: DVWA 

- **Beats Installed:** _The following Beats installed on the aforementioned machines_

  - 'FILEBEAT'
    - See URL for more details [Filebeat](https://www.elastic.co/beats/filebeat?msclkid=14613ae2ab6c11ecb5c6c574a3483e0d)
  - 'METRICBEAT'
    - See URL for more details [Metricbeat](https://www.elastic.co/beats/metricbeat?msclkid=5485be4aab6c11eca81543bc3775ed66)

- **Information Collected:** These Beats allow us to collect the following information from each machine

  - 'BEATS': Beats are special-purpose data collection modules.
    - Rather than collecting all a machine's log data, Beats allow you to collect only the very specific pieces of information you are interested in.
    - Beats generate and send log file data to either Logstash and Elasticsearch for indexing. Kilbana is then used to visualize the data collected in user friendly depictions.
    - Since 'FILEBEAT' and 'METRICBEAT' collect data about specific files on remote machines, they must be installed on the machines targeted for monitoring.
  - 'FILEBEAT': _Collects data about file system_
    - This beat collects and parses logs from various components of the machines.  Logs targed include the _var/log/*.log_ folder and can be further refined in configuration file if desired.
    - The beat outputs data to the _elasticsearch_ and _Kibana_ modules of ELK Stack.
    - Logs collected and parsed in the project configuration include for example:
      - **nginx**: Records events like visitors to your site and issues it encountered to log files. 
      - **osquery**: Records events like user logins, installed programs, running processes, network connections, or system log collection. 
  - 'METRICBEAT': _Collects machine metrics_
    - This beat collects and parses data/statistics from various system/hardware components of the machines or containers where installed and configured.
    - The beat outputs data the _elasticsearch_ and _Kibana_ modules of ELK Stack.
    - Example statistics collected and parsed include for example:
      - CPU usage, memory, file system, disk IO, and network IO statistics, as well as processes running on your systems.

### Using Ansible Build and Playbooks
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
