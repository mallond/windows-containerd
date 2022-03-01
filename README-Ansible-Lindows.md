# Lindows Ansible Monster

## Install Ansible in Ubuntu
```
sudo apt update
sudo apt install ansible
```

## Install Windows Remote Management 
[winrm](https://docs.ansible.com/ansible/latest/user_guide/windows_setup.html#winrm-setup)

### Enable PSRemoting Basic
```
Set-Item -Path WSMan:\localhost\Service\Auth\Basic -Value $true
```

## Modify Hosts file
```
sudo vi /etc/ansible/hosts
```

## Example hosts file
```
[win]
server1 ansible_host=10.7.0.4
server2 ansible_host=13.64.226.128

[win:vars]
ansible_user=robo
ansible_password=robo
ansible_connection=winrm
ansible_port=5985
ansible_winrm_transport=ntlm

#Note: ntlm is the easiest for windows
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








