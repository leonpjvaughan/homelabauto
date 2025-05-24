# Ansible Ubuntu Update

This project provides an Ansible playbook to update Ubuntu machines. It automates the process of updating the package list, upgrading installed packages, and cleaning up unnecessary packages.

## Usage

1. Run the playbook using the following command:

   ```shell
   ansible-playbook -i inventory playbooks/update-ubuntu.yml --ask-vault-pass
   ```

   Note the use of "--ask-vault-pass". I have non-tracked vault files storing passwords. these are stored relative to the inventory files in group_vars and host_vars. The playbook will prompt you for the vault password to decrypt these files.

2. Monitor the output for any errors or issues during the update process.
