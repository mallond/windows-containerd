# Lindows Ansible Monster - Windows II

## Install Ansible in WSL/Ubuntu
```
sudo apt update
sudo apt install ansible
```

### Enable Windows Remote Management 
```
# Setup WinRM
winrm quickconfig -Force
Enable-PSRemoting

# > Open Windows firewall port 5985
# > Open Azure firewall port 5985 if public IP is used
# > Create Ansible BOT user
# > Open port 5985 both in Windows Firewall and Azure Firewall

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








