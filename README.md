# Homelab automation

This repo is a collection of scripts which automate tasks in my homelab.

# Ansible setup

Install Ansible on your control node (I am using a ubuntu vm). I like to use a virtual environment for this. You can install Ansible using the following methods:
   * You can install Ansible using pip:
      ```shell
     sudo apt update
     sudo apt install python3-pip python3-venv
     # create a virtual environment
     python3 -m venv ~/ansible-venv
     source ~/ansible-venv/bin/activate
     pip install ansible ansible-lint
     # set the virtual environment to activate on login
     echo "source ~/ansible-venv/bin/activate" >> ~/.bashrc
     
     ```
- Access to the target nodes via SSH.
   * This can be set up by creating an ssh key on the control machine by:
      1. Generating an SSH key pair using `ssh-keygen`.
      2. Adding the public key to the target machines' `~/.ssh/authorized_keys` file. or using `ssh-copy-id` command.
      3. Updating the ssh config file on the control machine to use the new key for the target machines.

      **Alternatively, I am using proxmox with a cloud-init image. This allows me to set the ssh keys on the target machines at creation time.**
- The target machines should have Python installed, as Ansible requires it to execute tasks.


# Repository structure
This repository contains the following directories:
- `ansible-ubuntu-update`: Ansible playbook to update Ubuntu machines.
- `ansible-rke2-setup`: Ansible playbook to set up RKE2 on a cluster of machines.
- `ansible-rke2-update-config`: Ansible playbook to update the RKE2 configuration on the manager/server (i.e. the kubernetes manager) node.
- `inventory`: Contains the inventory files for the Ansible playbooks. I have multiple inventory files for different scenarios. 
- `roles`: Contains the Ansible roles used in the playbooks. These roles are reusable components that can be shared across different playbooks.

To reuse the inventory and roles directories, I am using symlinks in my playbook directories. This allows me to keep the inventory and roles directories in a central location, while still being able to use them in different playbooks.

# DISCLAIMER

see [DISCLAIMER.md](DISCLAIMER.md)