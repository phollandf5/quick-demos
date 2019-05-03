 # F5 Public Cloud Demo Environments
 
 ## Overview

 These playbooks are provided to spin up a quick demo environment up in Azure or AWS, and also to easily destroy the demo when done.  The configuration builds and destroys the following:

 - VNET or VPC
 - Subnets (Management and Dataplane)
 - Internet Gateway
 - Routing
 - A pair of BIG-IPs deployed with 2 NICs in HA 

 In AWS, the playbook will login to the deployed BIG-IPs and change/enable password authentication.  In Azure, passwords are enabled by default.

 What these playbooks don't provide (yet):

 - Any test application server (I plan to automate a microservices app)
 - AS3 configuration to create a virtual server and pool
 - Automated TLS certs/keys
 - F5 Cloud Services GSLBaaS
 - F5 Silverline WAFaaS


## IMPORTANT!

DO NOT put credentials in any file of folder contained in this repo!


## Configuration Notes

To allow Ansible to SSH to BIG-IPs in AWS (to change initial password and enable password authentication), you might need to disable host_key_checking in the Ansible config file:

 - create /etc/ansible directory if it doesn't exist.
 - create /etc/ansible/ansible.cfg if it doesn't exist and add the following three lines:

```
[defaults]
private_key_file =
host_key_checking = False
```

If you have ansible installed, you can run the playbooks with: 
 
 ```ansible-playbook playbook-name```

 e.g. 

```ansible-playbook CREATE-azure-arm-ha-api-exist-payg-UDR.yaml```


There are instructions contained within each playbook, and within the vars files.  The instructions in the playbook tell you how to declare your credentials.