# Managed Node

 1. Setup EC2 instance
 2. Setup Hostname
 3. Create ansibleadmin user
 4. Add user to sudoens file
 5. Enable password based login
 
 
 
 
 ### Setup EC2 
    
      
- use redhat linux | amazon linux | ubuntu
- new security group -> ansible-sg
                open port  22
                           80
                           8080
                           
 ### Setup Hostname
    
- Hostname command
      
   ```sh
		sudo su - 
		hostname ans-rhelmanaged-node
   ``` 
    
- Edit /etc/hostname [Permanent]
    
   ```sh
        vi /etc/hostname
        ans-rhelmanaged-node
        
        sudo su -
   ```

 ### Create ansibleadmin user
 
   ```sh
		useradd ansadmin
		passwd  ansadmin
		>> ansadmin123
		
		#for ubunntu u need to create /home directory for user to 
		useradd ansadmin ansadmin -d /home/ansadmin
		passwd ansadmin
		>> ansadmin123
		
   ```
 
 ### Add user to sudoens file
   
   ```sh
      
	   visudo 
	   
	   add under root
	   
	   `ansadmin ALL=(ALL)	NOPASSWD:ALL `
   
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
 
   
   
  1. Update the ip of managed node into hosts file in control node 
   
   ```
     ifconfig
     or 
     ip addr
   ```
   
  2. copy sshkey from control node to managed node [ssh-copy-id host]

  ```
   sudo su - ansadmin
   ssh-copy-id ip_address_of_managed_node
   
   verify from control node
   ssh ip_address_of_managed_node
  ```
   
 
