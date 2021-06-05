## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Images/ELK-network.png)

These files have been tested and used to generate a live ELK deployment with an Azure container network using ansible. The information included below can be used to either recreate the entire deployment pictured above or information included can be used to install specific portions of the project.

  - _TODO: Enter the playbook file._

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to utilize a load-balanced and monitor instances of DVWA, the D*mn Vulnerable Web Application.  DVWA is an intentionally exploitable website designed to allow the most common vulnerabilities. The network included in this repository provide redundancy from these attacks while monitoring the network traffic to expose these common exploits.

A load balancer ensure that the application will be highly available by distributing incoming network traffic across a backend server pool.  This ensures that the application will be highly accessible while to restricting inbound access to the network.

Including a Jump Box provisioner further restricts access to the backend pool by only allowing specific access to the network so that updates and changes can be made to the Azure network containers.

Integrating an ELK server allows users to easily monitor the vulnerable web application for changes to the file systems and system metrics.  Filebeat and Metricbeat are used for logging these changes to the ELK server and were installed using ansible playbooks detailed below.

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.1   | Linux            |
| WEb-1    | Web Server | 10.0.0.5   | Linux            |
| Web-2    | Web Server | 10.0.0.6   | Linux            |
| Web-3    | Web Server | 10.0.0.7   | Linux            |
| ELK      | Monitoring | 10.1.0.4   | Linux            |

### Access Policies