# Ansible with Kubernetes
We will setup a network of VMS, which will have: 

**Ansible controller** - "ansible.example.com"

**Kubernetes master** - "master.example.com"

**Kubernetes node**  - "nodeone.example.com"

**Kubernetes node** - "nodetwo.example.com"

*we will controll all the nodes from our ansible controller node.*

**run**
```docker
docker-compose -f ./ansible_kubernetes/docker-compose.yml up -d
```

**stop**
```docker
docker-compose -f ./ansible_kubernetes/docker-compose.yml down
```

## Configure SSH keys


**Generate sshkey:**

```shell
ssh-keygen
```

**Copy public key to other VMS or hosts:**

```shell
ssh-copy-id -i ~/.ssh/id_rsa.pub root@master.example.com
ssh-copy-id -i ~/.ssh/id_rsa.pub root@nodeone.example.com
ssh-copy-id -i ~/.ssh/id_rsa.pub root@nodetwo.example.com
```

**Now try logging into the machine, with:**

```shell
ssh root@master.example.com
ssh root@nodeone.example.com
ssh root@nodetwo.example.com
```

## ANSIBLE
inside your ansible VM run this command to install ansible.

```shell
apt install ansible
```

### Use exiting ansible configuration

1. install git  `apt install git`

2. clone this repo

```git
git clone https://github.com/mb-wali/debian.git
```

3. navigate to repo

```shell
cd debian/ansible_kubernetes/
```

4. modify **ansible.cfg** to point to the hosts file.

Ansible configuration file.
which overrides `/etc/ansible/ansible.cfg`

```
Inventory = /debian/ansible_kubernetes/hosts
```

**check ansible hosts**

list only master hosts of ansible
```shell
ansible masters --list-hosts
```

list all the hosts of ansible
```shell
ansible all --list-hosts
```

ping all ansible hosts
```shell
ansible -m ping all
```

### Playbooks
Ansible playbooks are blueprint of automation tasks

**Check playbook syntax**

```shell
ansible-playbook ./playbooks/docker.yml --syntax-check
```

### Playbooks
we have writen one playbook `./playbooks/docker.yml`, we can run this to install docker on all the machines.

run
```shell
ansible-playbook ./playbooks/docker.yml
```
