# ansible adhoc command 

we can create the inventory file any location, but we have give the path in command, or else we can add the host in this path /etc/ansible/host 

we will use the ping command 

ansible -i /path/to/inventory.ini -m ping all 

-i is used to give the inventory path, if host are not added in /etc/ansible/host 
-m is used for ansible module, in this command we are using ping module 
all is used to run the command on all the servers give in inventory 

