Marvin - COMP350 Intro to DevOps Project 2
This repository contains the second project for COMP350 - Introduction to DevOps. The project involves setting up and managing infrastructure using Ansible, Docker, and related DevOps tools.

Project Structure
The project is structured as follows:

ansible_project/
managed-node/: Configuration files for the managed nodes.
control-node/: Configuration and scripts for the control node, responsible for executing Ansible playbooks.
docker-compose.yml: A Docker Compose file used to set up the required environment for the Ansible project.
Setup Instructions
To run this project on your local machine, follow these steps:

Prerequisites
Docker
Docker Compose
Ansible
Steps
Clone the repository:

bash
Kodu kopyala
git clone https://github.com/yourusername/marvin-devops-project2.git
cd marvin-devops-project2/ansible_project
Run Docker Compose to set up the environment:

bash
Kodu kopyala
docker-compose up
Access the control node and execute Ansible commands:

bash
Kodu kopyala
docker exec -it control-node /bin/bash
ansible-playbook playbook.yml
Project Details
Control Node: Acts as the main machine responsible for running Ansible playbooks.
Managed Node: The target nodes managed by Ansible configurations.
Docker Compose: Used to orchestrate the control and managed nodes.
