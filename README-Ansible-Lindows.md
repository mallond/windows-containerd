# Lindows Ansible Monster

## Install Ansible in Ubuntu
```
sudo apt update
sudo apt install ansible
```
## Modify Hosts file
```
sudo vi /etc/ansible/hosts

## Example hosts file
[servers]
server1 ansible_host=203.0.113.111
server2 ansible_host=203.0.113.112
server3 ansible_host=203.0.113.113

[all:vars]
ansible_python_interpreter=/usr/bin/python3

```

## Show all Servers
```
# Show all servers
ansible-inventory --list -y

#Or for localhost this is implied 
ansible localhost -m ping
```

## Test a few commands
```
ansible localhost -a "ls -al"
```

## Seting up the Windows Remote Management

### Enable PSRemoting 

```
Enable-PSRemoting -SkipNetworkProfileCheck
```
![image](https://user-images.githubusercontent.com/993459/156064080-e3e3a3b2-2eac-408a-bd9e-1947b0966d64.png)


