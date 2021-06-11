# ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK%20Network](ELK%20Network.png)

These files have been tested and used to generate a live ELK deployment with an Azure container network using ansible. The information provided in this repository can be used to either recreate the entire deployment or install specific portions of the project.

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Filebeat
  - Metricbeat
- How to Use the Ansible Build

## Description of the Topology

The main purpose of this network is to utilize a load-balanced and monitored instances of DVWA, the D*mn Vulnerable Web Application.  DVWA is an intentionally exploitable website designed to allow for the most common vulnerabilities. The network included in this repository provides redundancy from these attacks while monitoring the network traffic to expose these common exploits.

A Load Balancer acts as a router by distributing incoming network traffic uniformily across the backend server pool. This ensures that the application will be highly accessible should a server go down. In this instance the Load Balancer is also used to limit access to the web application to our localhost for reasearch purposes.

Implementing a Jump Box further restricts ineternal network exposure to the backend pool by only allowing SSH access with public key authentication to the network by the administrator.  This forces all network traffic to a single node which can be further hardened and monitored for security.

Integrating an ELK server allows users to easily monitor the vulnerable web application for changes to the file systems and system metrics.  Information is collected and analyzed by Kabana through the Elasticsearch engine, Filebeat and Metricbeat are used for logging changes on the web servers to the ELK engine.  

All server configuration files were installed using ansible playbooks and are included in this repository.

Configuration details of each machine:

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| DVWA-1   | Web Server | 10.0.0.5   | Linux            |
| DVWA-2   | Web Server | 10.0.0.6   | Linux            |
| DVWA-3   | Web Server | 10.0.0.7   | Linux            |
| ELK      | Monitoring | 10.1.0.4   | Linux            |

## Access Policies

In this deployment only the Jump Box can accept connections from the internet.  Access to the internal network was established through SSH with public key authentication to the Jump Box from the local host.  Internally, all servers can access one another.  

Using Network Security Groups further limited acccess to the web application by restricting accessability to TCP network traffic only from the localhost IP.

A summary of the access policies can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 172.58.99.163        |
| DVWA-1   | No                  | 10.0.0.0/24          |
| DVWA-2   | No                  | 10.0.0.0/24          |
| DVWA-3   | No                  | 10.0.0.0/24          |
| ELK      | No                  | 10.0.0.0/24          |

## Elk Configuration

Ansible was used to automate configuration of the ELK server, no configurations were performed manually.  Automating configurations with Ansible allows for the repeated and immediate deployment of base configurations.  This also allows for improvements to be made in an immediately deployable instance and updating multiple containers simultaneously.

The ELK playbook implements the following tasks:

- Installs the Docker

- Installs Python 3

- Installs pyhton module

- Increases virtual memory required to run an ELK container

- Downloads and launches the docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker_ps_output](Images/docker_ps_output.png)

## Target Machines & Beats

This ELK server is configured to monitor the following machines:

- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

The Beats installed on the web servers allow us to collect the following information:

### Filebeat

- Filebeat Installation Playbook

Filebeat is used to collect and transfer specific log files to the ELK engine.  The configuration file can be changed to harvest various log files and tailored to a user defined application.

The modules enabled in the Filebeat configuration .yml file enable logs to be imported from the DVWA web servers to Elasticsearch.

### Metricbeat

- Metricbeat Installation Playbook

With Metricbeat, information can be periodically collected about the system or service monitored and sent to ELK for analysis.  Information such as CPU usage, SSH login attempts, failed sudo escalations, and CPU/RAM statistics are a few system metrics that can give an insight on what is occuring on the target server.  Metricbeat can also be used to monitor database activity and status on MySQL, PostgreSQL, and MongoDB.

## Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured.  The jump box in this deployment was used for this purpose.

SSH into the control node and follow the steps below:
