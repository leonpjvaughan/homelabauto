# Setup ansible playbook to install RKE2

```shell
ansible-playbook -i inventory setup.yaml --ask-vault-pass
```

# Post install (Reminder of next steps)

1. Copy the kubeconfig file to your local machine. I just dowloaded it using vscode ssh file browser. The default location is ~/.kube/config
2. Verify the install. nodes should be in a Ready state and pods should be running or completed.
```shell
kubectl get nodes
kubectl get pods -A
```


# Credits

This playbook is based on https://github.com/JamesTurland/JimsGarage/tree/main/Ansible/Playbooks/RKE2