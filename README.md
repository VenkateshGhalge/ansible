# Ansible

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

## Ansible playbook 

In ansible playbook we have plays or task which need to performed on the servers, we can give the name of group and take action on them. 
task use ansible modules which need to perform task like copy the file or install the software on the servers 


name: install apache on webservers 
  host: webserver
  become: true 

  tasks:
  - name: installing apache 
    ansible.builtin.apt:
      name: apache2
      state: present 

to run the playbook 

ansible-playbook -i webhost -u ansible -k firstplaybook.yaml

## Ansible Role 

 It is use to divided the playbook into small unit, so we have more readability and modularity. we divided different section of playbook into different folder is called as role 

 below is folder 

 roles/
    common/               # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies
        library/          # roles can also include custom modules
        module_utils/     # roles can also include custom module_utils
        lookup_plugins/   # or other types of plugins, like lookup in this case

we can use the below command to created the folder 

ansible-galaxy role init test 

