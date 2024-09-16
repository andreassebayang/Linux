# Linux

## Create New User

1. Login to Server or Console

2. Chcek Sudo already installed

````Command
which sudo

3. Installation Sudo
```command
apt-get install sudo

4. Verification Sudo after Installation
```Command
sudo --version

5. Create New User
```Command
adduser namauser

6. Adding New User to the Sudo Group
```Command
usermod -aG sudo namauser

7. Verification the New User already in the Sudo Group
```Command
groups namauser

8. Check the permission of the Sudo file
```Command
ls -l /usr/bin/sudo

> [!NOTE]
> It should be:
> -rwsr-xr-x 1 root root /usr/bin/sudo

9. Try login with the New user
   ```Command
   su - namauser
   sudo ls /root

## Adding Config to SSH for the New User

1. Edit the configuration file of SSH
```Command
sudo nano /etc/ssh/sshd_config

2. Find and Edit the line of: change from Yes to No
```Command
PermitRootLogin no

3. Adding New Line
```Command
AllowUsers NameUser

4. Save and exit
```Command
ctrl + x and y

5. Restart the Service SSH
```Command
systemctl restart sshd atau sshd.service
````
