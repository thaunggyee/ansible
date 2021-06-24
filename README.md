# How to Install Ansible AWX on Ubuntu 20.04 LTS.

Ansible AWX is a free and opensource front-end web application that provides a user interface to manage Ansible playbooks and inventories, as well as a REST API for Ansible. It is an open source version of Red Hat Ansible Tower. In this guide, we are going to install Ansible AWX on Ubuntu 20.04 LTS system.

* Login to your machine and update.
```bash
sudo apt update -y
```
* Install docker on your machine.
```bash
sudo apt install docker.io -y
sudo systemctl status docker
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker 
```
* Install docker-compose 
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```
* Install ansible 
```bash
sudo apt install ansible -y
ansible --version
```
* Install node and npm
```bash
sudo apt install nodejs npm -y
sudo npm install npm --global
```
* install and setup ansible aws
```bash
sudo apt install -y python3-pip git pwgen
```
* Next, install the docker-compose module that matches your version of docker-compose.
```bash
docker-compose --version
sudo pip3 install docker-compose==1.29.2
```
* We are now going to download the latest AWX zip file from Github. To do so, we will use the wget command as follows.
```bash
wget https://github.com/ansible/awx/archive/17.1.0.zip
unzip 17.1.0.zip
cd awx-17.1.0 /installer
```
* Then generate a 30 character secret key using the pwgen tool as follows:
```bash
 pwgen -N 1 -s 30
 ```
 * Uncomment the admin and password parameters and be sure to provide a strong admin password. This is the password that you will use to log in to AWX on the web login page.
```bash
vim inventory
admin_user=admin
admin_password=<Strong-Admin-password>
secret_key=lKjpI3Hdj2PWlp8De6g2pDj9e5dU5e
```
* Run playbook to install ansible aws
```bash
sudo su -
cd /home/thaunghtikeoo/awx-*/installer/
kill service running on port 80 (i.e nginx)
ansible-playbook -i inventory install.yml
```

Usage---> 

![images of credentials]
(https://github.com/tho861998/ansible/images/credential.png)




