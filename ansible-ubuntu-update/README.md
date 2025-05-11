# Ansible Ubuntu Update

This project provides an Ansible playbook to update Ubuntu machines. It automates the process of updating the package list, upgrading installed packages, and cleaning up unnecessary packages.

## Prerequisites

- Ansible installed on your control machine. I like to use a virtual environment for this. You can install Ansible using the following methods:
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
- Access to the target Ubuntu machines via SSH.
   * This can be set up by creating an ssh key on the control machine by:
      1. Generating an SSH key pair using `ssh-keygen`.
      2. Adding the public key to the target machines' `~/.ssh/authorized_keys` file. or using `ssh-copy-id` command.
      3. Updating the ssh config file on the control machine to use the new key for the target machines.

      Alternatively, I am using proxmox with a cloud-init image. This allows me to set the ssh keys on the target machines at creation time.
- The target machines should have Python installed, as Ansible requires it to execute tasks.

## Usage

1. Run the playbook using the following command:

   ```shell
   ansible-playbook -i inventory playbooks/update-ubuntu.yml --ask-vault-pass
   ```

   Note the use of "--ask-vault-pass". I have non-tracked vault files storing passwords. these are stored relative to the inventory files in group_vars and host_vars. The playbook will prompt you for the vault password to decrypt these files.

2. Monitor the output for any errors or issues during the update process.
