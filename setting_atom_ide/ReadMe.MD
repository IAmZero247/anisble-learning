
# Install atom IDE
https://atom.io/

# Install Plugins

## package1
  1. install package -> atom linter-js-yaml
  2. npm install linter-js-yaml
  
## package2 
  1. install package -> atom remote-sync
  
  2. `npm install remote-sync`
  
  3. Right Click ->Remote Sync ->Config
       1. scp/sftp
       2. hostname -> give public ip 
       3. port -> 22
       4. target directory -> /home/osboxes/ansible-demos-exercises
       5.  ignorepath->
       6. username -> osboxes
             password -> osboxes.org 
             
       7. uploadOnSave -> enabled
          userAtomicWrites -> disabled
          delete local files/folder upon remote delete -> delete
       
