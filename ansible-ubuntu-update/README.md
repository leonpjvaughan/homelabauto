# Ansible Ubuntu Update

This project provides an Ansible playbook to update Ubuntu machines. It automates the process of updating the package list, upgrading installed packages, and cleaning up unnecessary packages.

## Prerequisites

- Ansible installed on your control machine.
- Access to the target Ubuntu machines via SSH.
- The target machines should have Python installed, as Ansible requires it to execute tasks.

## Usage

1. Run the playbook using the following command:

   ```
   ansible-playbook -i inventory playbooks/update-ubuntu.yml --ask-vault-pass
   ```

2. Monitor the output for any errors or issues during the update process.
