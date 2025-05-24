# Info

Configure oidc config for rke2.

## Steps
Get the CA cert and copy the last certificate in the chain to the `oidc-ca.crt` file.
```shell
openssl s_client -showcerts -partial_chain -connect keycloak.example.com:443 < /dev/null
```

Update the rke2-config-update file with the correct values for your environment. 


Run the playbook to update the oidc config for rke2.
```shell
ansible-playbook -i inventory setup.yaml --ask-vault-pass
```
