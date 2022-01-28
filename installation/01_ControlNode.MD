# Ansible Server - Control Node

 1. Setup EC2 instance
 2. Setup Hostname
 3. Create ansibleadmin user
 4. Add user to sudoens file
 5. Generate ssh key
 6. Enable password based login
 7. Install Ansible
 
 
 
 
 ### Setup EC2 
    
      
- use amazon linux ami
- new security group -> ansible-sg
                open port  22
                           80
                           8080
                           
 ### Setup Hostname
    
- Hostname command
      
   ```sh
		sudo su - 
		hostname ans-control-node
   ``` 
    
- Edit /etc/hostname [Permanent]
    
   ```sh
        vi /etc/hostname
        ans-control-node
        
        sudo su -
   ```

 ### Create ansibleadmin user
 
   ```sh
		useradd ansadmin
		passwd  ansadmin
		>> ansadmin123
   ```
 
 ### Add user to sudoens file
   
   ```sh
      
	   visudo 
	   
	   add under root
	   
	   `ansadmin ALL=(ALL)	NOPASSWD:ALL `
   
   ```
   
 ### Generate ssh key
   
   ```sh
     
     sudo su - ansadmin 
	
     #generate sshkey with empty passphrase
	
     ssh-keygen
     ll -a
	
     cd .ssh
	
       >> 1. id_rsa
       >> 2. id_rsa.pub
	
   ```
    
### Enable password based login   


  ```
      switch to root 
    
      sudo su - 
      whoami
    
      vi /etc/ssh/sshd_config
    
      now update for below:
      PasswordAuthentication yes
    
      service sshd restart | reboot
   ```
 
 ### Install Ansible
 
   1. Install python and python-pip
   
   ```sh
       yum install python
       yum install python-pip
   ```
   
   2. Install ansible using pip check for version
     
   ```sh
     
      pip install ansible
      ansible --version
     
   ```
   
   3. Create new ansible.cfg in location /etc/ansible 

       Copy content from *https://github.com/IAmZero247/Ansible-Notes/blob/main/00_lab-env-setup/ansible.cfg*
     
        ```
	     mkdir /etc/ansible
	     cd /etc/ansible

	     touch ansible.cfg 
	     vi ansible.cfg

	     copy n paste 

	     :wq

	     Verify:

	     ansible --version
			[DEPRECATION WARNING]: Ansible will require Python 3.8 or newer on the controller
			 starting with Ansible 2.12. Current version: 2.7.18 (default, Jun 10 2021,
			00:11:02) [GCC 7.3.1 20180712 (Red Hat 7.3.1-13)]. This feature will be removed
			from ansible-core in version 2.12. Deprecation warnings can be disabled by
			setting deprecation_warnings=False in ansible.cfg.
			ansible [core 2.11.7]
			config file = /etc/ansible/ansible.cfg
			configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
			ansible python module location = /usr/lib/python2.7/site-packages/ansible
			ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
			executable location = /usr/bin/ansible
			python version = 2.7.18 (default, Jun 10 2021, 00:11:02) [GCC 7.3.1 20180712 (Red Hat 7.3.1-13)]
			jinja version = 2.7.2
			libyaml = True
         ```
    
   4. Create new host file in location /etc/ansible
   
   ```
   touch hosts
   ```
   
    - add ip of managed nodes in hosts file
