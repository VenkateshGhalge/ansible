# ansible adhoc command 

we can create the inventory file any location, but we have give the path in command, or else we can add the host in this path /etc/ansible/host 

we will use the ping command 

- ansible -i /path/to/inventory.ini -m ping all 

-i is used to give the inventory path, if host are not added in /etc/ansible/host 
-m is used for ansible module, in this command we are using ping module 
all is used to run the command on all the servers give in inventory 


- ansible -i inventory.ini -m shell -a "sudo apt install nodejs" all

-m we are using shell module
-a argument to be passed 

- ansible webappservers -a "/sbin/reboot"

-webappservers: is the group of servers we what action on 

- ansible webappservers -a "/sbin/reboot" -f 10 

-f is to forks to run reboot at same time in the servers 

- ansible webappservers -a "/sbin/reboot" -u webapps --become 

-u is the use you want use to run the command 
-become is use to run the command as root 

# manage file 

- ansible webappservers -m ansible.builtin.copy -a "src = /app_01/core/lib/app.war dest=/temp/hosts"

we can use file module to update the permission of files and ower and group 

- ansible  




