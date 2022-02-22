## 1.　sudo
Login as root
```
$ su -
```
Install sudo
```
$ apt-get update -y
$ apt-get upgrade -y
$ apt install sudo
```

Verify whether sudo was successfully installed via dpkg -l | grep sudo.
```
# dpkg -l | grep sudo
```

Adding user in sudo group
```
$ su -
$ usermod -aG sudo your_username
```
or
```
# adduser user_name sudo
```

Check if user is in sudo group
```
$ getent group sudo
```

Verify whether user was successfully added to sudo group via getent group sudo.
```
$ getent group sudo
```

Give privilege as a su.

Open sudoers file:

```
$ sudo visudo
```

Add this line in file:
```
your_username    ALL=(ALL) ALL
```

## 2. git, vim, oh my zsh

Installing git
```
$ apt-get update -y
$ apt-get upgrade -y
$ apt-get install git -y
```

Check git version
```
$ git --version
```

Installing wget (wget is a free and open source tool for downloading files from web repositories.)
```
$ sudo apt-get install wget
```

Installing Vim
```
$ sudo apt-get install vim
```

Installing Oh my zsh (because it is easier to use)
```
$ sudo apt-get install zsh
$ zsh --version
$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

## 3. SSH

### 3.1. Installing SSH
```
$ sudo apt-get update
$ sudo apt install openssh-server
```

Check the SSH server status

```
$ sudo systemctl status ssh
```

Restart the SSH service
```
$ service ssh restart
```

Changing default port (22) to 4242
```
$ sudo nano /etc/ssh/sshd_config
```

Edit the file change the line #Port22 to Port 4242
Find thid line:

```
#Port 22
```
Change it like this:
```
Port 4242
```
Check if port settings got right
```
$ sudo grep Port /etc/ssh/sshd_config
```
Restart the SSH service
```
$ sudo service ssh restart
```

#### not necessary (don't know why)
To disable SSH login as root irregardless of authentication mechanism, replace below line

```
32 #PermitRootLogin prohibit-password
```
with:
```
32 PermitRootLogin no
```
### 3.2. UFW (Uncomplicated Firewall)

Install UFW
```
$ apt-get install ufw
```

Verify whether ufw was successfully installed via dpkg -l | grep ufw.
```
$ dpkg -l | grep ufw
```

Enable
```
$ sudo ufw enable
```
Check the status
```
$ sudo ufw status numbered
```
Configure the rules
```
$ sudo ufw allow ssh
```
Configure the port rules
```
$ sudo ufw allow (port number, for example 2222)
```
Delete the new rule
```
$ sudo ufw status numbered
$ sudo ufw delete (that number, for example 5 or 6)
```
