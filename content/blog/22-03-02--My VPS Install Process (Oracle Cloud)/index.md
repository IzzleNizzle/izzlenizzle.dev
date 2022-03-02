---
title: My VPS Install Process (Oracle Cloud)
date: 2022-03-02T13:37:00.000Z
description: How I like to set up my Ubuntu 20.04 VPS servers, Oracle Cloud edition.
---
# Install Process for Ubuntu 20.04 Image - Oracle Cloud

First steps:

```bash
#/bin/bash
# custom install script 1

sudo apt update; sudo apt upgrade
sudo adduser newUser
sudo usermod -aG sudo newUser
sudo -u newUser mkdir /home/newUser/.ssh
sudo cp /home/ubuntu/.ssh/authorized_keys /home/newUser/.ssh/
sudo chown newUser:newUser /home/newUser/.ssh/authorized_keys
sudo reboot now

```

Oracle fires up Ubuntu instances with two default users: "ubuntu" and "opc". Next we will remove the old predictable accounts. 

Log back in as the new user:

`sudo userdel -r ubuntu`

`sudo userdel -r opc`

Now we will harden ssh access and change the ssh port. SSH ports are often tested by public, change port to slow down those trying to intrude.

`sudo vim /etc/ssh/sshd_config`

add this:

```bash
# custom changes
PasswordAuthentication no
PermitRootLogin no
Protocol 2
Port 1234
AllowUsers newUser
MaxAuthTries 6
# end custom changes
```

Custom command for Oracle cloud to open the new ssh port
`sudo iptables -I INPUT -p tcp -s 0.0.0.0/0 --dport 1234 -j ACCEPT`

This takes place of the ufw work below. Oracle cloud doesn't use ufw

For non Oracle cloud ubuntu instance:

`sudo ufw enable`
`sudo ufw allow 1234/tcp`
`sudo ufw status numbered`
`sudo ufw delete 2`

Then restart ssh. I also include some instructions here to install nvm ([Node.js Version Manager](https://github.com/nvm-sh/nvm)) and a [Nginx web server](https://www.nginx.com/)

```bash
sudo service ssh restart
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
source ~/.profile
nvm install 16.14.0
sudo apt install nginx
```

You can use this command to search what node versions are available and choose your own if you prefer.

`nvm ls-remote`
