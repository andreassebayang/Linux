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
