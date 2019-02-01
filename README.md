elasticsearch.yml

This playbook will setup,
1.Three node elasticsearch cluster (1 Master and 2 Data nodes) 
2.Install Kibana
2.Install x-pack plugin for elasticsearch and kibana

Prereuisite

1.ansible 2.7.1 should be installed and ansible connection is working for all target nodes.
1.Following rpms and .zip should be present at src/elasticsearch. They are included in this repo for now.

elasticsearch-5.6.14.rpm
jdk-8u201-linux-x64.rpm
kibana-5.6.14-x86_64.rpm
x-pack-5.6.14.zip

2.Create inventory file as below. Servers from 'master-node' will be used as Master and from 'data-node' will be used for data nodes.

[master-node]
wipro-e0.devops.digitalreasoning.com

[data-node]
wipro-e1.devops.digitalreasoning.com
wipro-e2.devops.digitalreasoning.com


Steps

1.Clone or download repo on Ansible workstation box.
2.Go to cluster-es and execute below command,

 ansible-playbook elasticsearch.yml -i inventory/inventory.txt  

3.Check for any errors in execution.


Verification

1.Login to kibana with http://[master-node-hostname]:5601 
2.From command line execute command,  
curl -u elastic http://[master-node-hostname]:9200/_cluster/health
3.Use elastic/changeme as credentials for both urls.

app-server.yml
 
This playbook will setup,

1.Copy required elasticsearch files
2.Create synthesys user.
3.Extarct synthesys-compliance-4.6.0.tar.gz 
4.Update synthesys-env.sh and synthesys.yaml

Prereuisite

1.Application code synthesys-compliance-4.6.0.tar.gz should be copied at src/app/
2.Inventory files should have details,

[app-node]
wipro-c0.devops.digitalreasoning.com

[oozie-node]
wipro-c0.devops.digitalreasoning.com

[app_db-node]
wipro-c0.devops.digitalreasoning.com


Steps

1.Clone or download repo on Ansible workstation box.
2.Go to cluster-es and execute below command,

 ansible-playbook app-server.yml -i inventory/inventory.txt  

3.Check for any errors in execution.

Verification

1.Login to synthesys app server system and execute below command,

/mnt/synthesys-compliance-4.6.0/bin/synth diag validate

This should not show any errors for Elasticsearch.