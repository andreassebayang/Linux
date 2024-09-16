# Linux

# Create New User

1. Login to Server or Console

2. Chcek Sudo already installed
   which sudo

3. Installation Sudo
   apt-get install sudo

4. Verification Sudo after Installation
   sudo --version

5. Create New User
   adduser namauser

6. Adding New User to the Sudo Group
   usermod -aG sudo namauser

7. Verification the New User already in the Sudo Group
   groups namauser

8. Check the permission of the Sudo file
   ls -l /usr/bin/sudo

It should be:
-rwsr-xr-x 1 root root /usr/bin/sudo

9. Try login with the New user
   su - namauser
   sudo ls /root

# Adding Config to SSH for the New User

1. Edit the configuration file of SSH
   sudo nano /etc/ssh/sshd_config

2. Find and Edit the line of: change from Yes to No
   PermitRootLogin no

3. Adding New Line
   AllowUsers NameUser

4. Save and exit
   ctrl + x and y

5. Restart the Service SSH
   systemctl restart sshd atau sshd.service
