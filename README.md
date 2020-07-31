# ELK cluster setup using Ansible

This codebase contains Ansible script to setup ELK cluster. 

  - Setup Elasticsearch cluster on provided nodes.
  - Servers from 'master-node' will be considerd as Masters and servers from 'data-node' group will be considerd as Data nodes.
  - Kibana will be installed on first master node.
  - Used zen discovery method for Elasticsearch cluster management. 

# Deployment Steps

  - Create instances for data-node, master-node with 15G of memory
  - Setup passwordless ssh from your system to all the nodes for user ansible
  -  Configure inventory/inventory.txt with appropriate node details. 
  -  Execute ansible command as below,
  
  ```sh
$ ansible-playbook-2 site.yml -i inventory/inventory.txt
```
