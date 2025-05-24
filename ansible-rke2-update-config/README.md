# Info

I dont have any need for the nginx ingress controller (I plan to use the gateway api), so I am removing it from the rke2 config. 

This playbook will remove the nginx ingress controller from the rke2 config. The simplest approach was to add a new config to the config.yaml.d directory rather than update the existing config.yaml. 

I plan to modify this in the future to deploy other config updates. For example, adding OIDC authentication.
