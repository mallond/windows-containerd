
```
sudo apt update
sudo apt install ansible
```

```
sudo vi /etc/ansible/hosts

# Example hosts file
[servers]
server1 ansible_host=203.0.113.111
server2 ansible_host=203.0.113.112
server3 ansible_host=203.0.113.113

[all:vars]
ansible_python_interpreter=/usr/bin/python3

```

```
# Show all servers
ansible-inventory --list -y

#Or for localhost this is implied 
ansible localhost -m ping
```

```
ansible localhost -a "ls -al"
```
