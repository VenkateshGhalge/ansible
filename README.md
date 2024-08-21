# ansible

Ansible is a software tool that provides simple but powerful automation for cross-platform computer support. It is primarily intended for IT professionals, who use it for application deployment, updates on workstations and servers, cloud provisioning, configuration management, intra-service orchestration, and nearly anything a systems administrator does on a weekly or daily basis.

## How Ansible works 
Ansible there are 2 categories of computers: the control node and managed nodes. The control node is a computer that run ansible. There must be at least one control node, although a backup control node may also exist. A managed node is any device being managed by the control node.
Ansible works by connecting to nodes (clients, servers, or whatever you're configuring) on a network, and then sending a small program called an Ansible module to that node. Ansible executes these modules over SSH and removes them when finished. 

### password-less authentication 

we will create the ssh key on the master node  using ssh-keygen it will generate 3 file 
 - authorizaed_key: A file storing the public keys
 - id_rsa.pub: the public key 
 - id_rsa: the private key 
 
 we create the ssh on managed node 

we will copy the public key from master node to managed node using below command 

 on master node 

 cd ~/.ssh/
 cat id_rsa.pub

 on target node 

 vi ~/.ssh/authorized_key 

then you can try to login using ssh 
