# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK%20Network](ELK%20Network.png)

These files have been tested and used to generate a live ELK deployment with an Azure container network using ansible. The information provided in this repository can be used to either recreate the entire deployment pictured above or install specific portions of the project.

- ansible

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Filebeat
  - Metricbeat
- How to Use the Ansible Build

## Description of the Topology

The main purpose of this network is to utilize a load-balanced and monitored instances of DVWA, the D*mn Vulnerable Web Application.  DVWA is an intentionally exploitable website designed to allow for the most common vulnerabilities. The network included in this repository provides redundancy from these attacks while monitoring the network traffic to expose these common exploits.

A Load Balancer establishes an external IP address for which all web applications can be accessed by the internet. This ensures that the application will be highly accessible by distributing incoming network traffic uniformly across a backend server pool. In this instance the Load Balancer is also used to limit access to the web application to a single IP address for reasearch purposes of the user.

Including a Jump Box provisioner further restricts network exposure to the backend pool by only allowing SSH access and public key authentication to the network so that updates to the congfiguration files can be made to the Docker containers only by the user.  Rules were established through the Network Security Group to limit external access and a virtual network was deployed to include the web servers.

Integrating an ELK server allows users to easily monitor the vulnerable web application for changes to the file systems and system metrics.  Important information is collected and analyzed by Kabana through the Elasticsearch engine where Filebeat and Metricbeat are used for logging changes to the ELK server.  Configuration and YAML files were installed using ansible playbooks that are included in this reporsitory.

Configuration details of each machine:

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.1   | Linux            |
| DVWA-1   | Web Server | 10.0.0.5   | Linux            |
| DVWA-2   | Web Server | 10.0.0.6   | Linux            |
| DVWA-3   | Web Server | 10.0.0.7   | Linux            |
| ELK      | Monitoring | 10.1.0.4   | Linux            |

## Access Policies

The machines on the internal network are not exposed to the public Internet.  Access to the internal network was established through SSH:22 and public key authentication to the Jump Box from the local host.  Instructions to upload RSA public key to the Jump Box provisoner from your local host are below:

- Open Git Bash on you local host and type the following command:

  - cat ~/.ssh/id_rsa.pub

- Copy your public RSA key string

- Paste to the Administrator Account section:

  - ![pub%20key](pub%20key.png)

Only the Jump Box machine can accept connections from the Internet. Access to Jump Box has now been restricted to you local IP.

A summary of the access policies within the network can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 172.58.99.163        |
| DVWA-1   | No                  | 10.0.0.0/24          |
| DVWA-2   | No                  | 10.0.0.0/24          |
| DVWA-3   | No                  | 10.0.0.0/24          |
| ELK      | No                  | 10.0.0.0/16          |

## Elk Configuration

Ansible was used to automate configuration of the ELK server, no configurations were performed manually.  Automating configurations with Ansible allows for the repeated and immediate deployment of base configurations.  This also allows for improvements to be made in an immediately deployable instance and updating multiple containers instantaniously.

The playbooks exicuted are included below:

- Ansible

- ELK

- Filbeat

- Metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

## Target Machines & Beats

This ELK server is configured to monitor the following machines:

- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

I have installed the following Beats on these machines:

- Filebeat
- Metricbeat

Filebeat is a tool that can be used in collecting and transferring specific log files to the Elasticsearch engine.  The purpose of this concept is to take all log information specific to a user defined application and creating a clear report for analysis.

With Metricbeat information about the system or service monitored can be collected and sent to Elasticsearch to be included in the analysis.

- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

## Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
