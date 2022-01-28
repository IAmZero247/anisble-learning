# AD HOC COMMANDS

  - https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html

### Syntax 

  ```
  $ ansible [pattern] -m [module] -a "[module options]"
  ```
  
  1. `Examples of modules` 
      
      -  ping >>
         ```
            ansible all -m ping
         ```   
      -  command >>
         ```
         ansible all -m command -a "uptime"
         ansible all -m command -a "date"
         ansible all -m command -a "who"
         ansible all -m command -a "whoami"
         ansible all -m command -a "pwd"
         ```
      -  stat >>
         ```
           ansible all -m stat -a "path=/etc/hosts"
         ```
      -  yum >>
         ```
           ansible all -m yum -a "name=git" -b
           ansible all -m yum -a "name=tree" -b
         ```
      -  user >>
  
         ```
           ansible all -m user  -a "name=ruby" -b
           ansible all -m user -a
           
           verify in managed nodes:
           cat /etc/passwd"
         ```
      -  setup >> gives entire info of managed nodes 
         ```
          ansible all -m setup
         ```
