# Linux

## Create New User

1. Login to Server or Console
2. Chcek Sudo already installed

```bash
which sudo
```

3. Installation Sudo

```bash
apt-get install sudo
```

4. Verification Sudo after Installation

```bash
sudo --version
```

5. Create New User

```bash
adduser namauser
```

6. Adding New User to the Sudo Group

```bash
usermod -aG sudo namauser
```

7. Verification the New User already in the Sudo Group

```bash
groups namauser
```

8. Check the permission of the Sudo file

```bash
ls -l /usr/bin/sudo
```

> [!NOTE]
> It should be:
> -rwsr-xr-x 1 root root /usr/bin/sudo

9. Try login with the New user

```bash
su - namauser
sudo ls /root
```

## Adding Config to SSH for the New User

1. Edit the configuration file of SSH

```bash
sudo nano /etc/ssh/sshd_config
```

2. Find and Edit the line of: change from Yes to No

```bash
PermitRootLogin no
```

3. Adding New Line

```bash
AllowUsers NameUser
```

4. Save and exit

```bash
ctrl + x and y
```

5. Restart the Service SSH

```bash
systemctl restart sshd atau sshd.service
```

# SSH Config

1. Limitation access for Sudo Users: to Increase the Security

```bash
sudo visudo
```

and adding this command line:
nameuser ALL=(ALL:ALL) /usr/bin/apt-get, /usr/bin/systemctl

> [!NOTE]
> This will restrict the user to only using sudo for apt-get and systemctl commands.

2. Restrict Root and Allow Sudo User from SSH

Edit line for root access

```bash
PermitRootLogin no
```

Adding new line

```bash
AllowUsers NameUser
```

3. Audit and Logging: ACtivate audit to monitor user activity.

```bash
sudo apt-get install auditd
sudo systemctl enabled auditd
sudo systemctl start auditd
```

4. Create a cusom banner file /etc/ssh/sshd-banner)
   > [!NOTE]
   > That will be displayed when someone tries to log in via SSH, In The SSH configuration file /etc/ssh/sshd_config, We set two importants things:

- Prevents direct login as root via SSH
- pointing the specifies the file path of banner that will be displayed

a. Edit and Adding the configuration

```bash
PemritRootLogin no
```

and adding

```bash
Banner /etc/ssh/sshd-banner
```

> [!NOTE]
> Check the file sshd-banner for the example notification message

. Restart SSH Service

```bash
sudo systemctl restart sshd or sshd.service
```
