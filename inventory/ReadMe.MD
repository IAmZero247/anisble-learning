# Inventory File 

  - https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html

### Sample File in Default Location /etc/ansible/hosts
  ```
      cat /etc/ansible/hosts

      [rhel]
      host1 
      host2
      [ubuntu]
      host3
      host4
      [other]
      host5
  ```
  
### Host Info 
  
  
  1.  Default location >> /etc/ansible/hosts file 
  2.  Using -i option >> ansible -i my_hosts
  3.  Define in ansible.cfg file location of hostfile
      
      - inventory = /etc/ansible/hosts
     
      - `>> ansible all -m ping  -i /etc/ansadmin/hosts`


### To list hosts

  1. cat file
  2. using ansible command
     ```
     ansible -i host --list-hosts 
     ```

