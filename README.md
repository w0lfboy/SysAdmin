# SysAdmin
Linux System Administration fundamentals

In the project, we were presented with a scenario from a fictional company as if we were a Systems Administrator.  
We were then tasked with changing file permissions, creating/deleting users, and auditing the system via Lynis.
- Step 1: Ensure Permissions on Sensitive Files
- Step 2: Create User Accounts
- Step 3: Create User Group and Collaborative Folder
- Step 4: Lynis Auditing
- Bonus: chkrootkit

## Step 1: Ensure Permissions on Sensitive Files
  Inspect the file permissions of each of the files below and change them to the assigned permissions. 
  - `/etc/shadow` should allow only root read and write access.
    - `ls -al`
    - `sudo chmod 600 /etc/shadow`
  - `/etc/gshadow` should allow only root read and write access.
    - `ls -al`
    - `sudo chmod 600 /etc/gshadow`
  - `/etc/group` should allow root read and write access, and allow everyone else read access only.
    - `ls -al`
    - `sudo chmod 644 /etc/group`
  - `/etc/passwd` should allow root read and write access, and allow everyone else read access only.
    - `ls -al`
    - `sudo chmod 644 /etc/passwd` 
      
## Step 2: Create User Accounts
Add user accounts for sam, joe, amy, sara, and admin.
  - `sudo adduser sam`
  - `sudo adduser joe`
  - `sudo adduser amy`
  - `sudo adduser sara`
  - `sudo adduser admin`
We want to make sure that only the admin user has general sudo group access. 
  - `sudo usermod -aG sudo admin` 
  - `groups admin`
    
## Step 3: Create user Group and Collaborative Folder
Add the group engineers to the system.
  - `sudo addgroup engineers`
Add users sam, joe, amy, and sara to the managed group.
  - `sudo usermod -aG engineers sam`
  - `sudo usermod -aG engineers joe`
  - `sudo usermod -aG engineers amy`
  - `sudo usermod -aG engineers sara`
Create a shared folder for this group: /home/engineers.
  - `sudo mkdir /home/engineers`
  - `sudo chgrp engineers /home/engineers`
Change ownership on the new engineers' shared folder to the engineers group.
  - `sudo chgrp engineers /home/engineers`
    
## Step 4: Lynis Auditing
Install the Lynis package to your system.
  - `sudo apt install lynis`
Check the Lynis documentation for instructions on how to run a system audit.
  - `man lynis`
Run a Lynis system audit with sudo.
  - `sudo lynis audit system`
    
## Bonus: `chkrootkit`
Install the chkrootkit package to your system
  - `sudo apt install chkrootkit`
Check the chkrootkit documentation for instructions on how to run a scan to find system root kits.
  - `man chkrootkit`
Run chkrootkit (with sudo) in expert mode to verify the system does not have a root kit installed.
  - `sudo chkrootkit -x`
 
