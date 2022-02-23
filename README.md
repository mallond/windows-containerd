# windows-containerd
Install Instructions for Windows II and Container-d

## Powershell Install wsl linux

List available Linux Distrobutions
```
wsl -l -o
```

Install Linux Distro
```
wsl --install -d Ubuntu-20.04
```

Reboot Windows

## Install Docker in WSL2 Linux only containers

Install Http-Transport, Certificate handler, curl software properties
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

Install Docker GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Set stable repository
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

Docker
```
sudo apt-get install docker-ce -y
sudo gpasswd -a $USER docker
# relaunch terminal
```

Start Docker service
```
sudo service docker start
or
sudo service docker restart
```

Test Docker Install
```
#Wsl install
docker run --name nginx0 -d -p 8080:80 nginx
docker run --name nginx1 -d -p 8081:80 nginx

#Powershell test
curl 127.0.0.1:8080
curl 127.0.0.1:8081

#Clean up
docker container rm nginx1 nginx0 --force
docker rmi nginx

```
## Networking
Windows Firewall Defender - Advanced Security
```
Open ports that need to be open
```

Azure Specific Example of Netsh
```
#find the wsl IP address
wsl hostname -I example 192.168.171.139
windows: ipconfig - get the IPv4 Address example:10.6.0.4

Parameters:
       Tag              Value
       listenport     - IPv4 port on which to listen.
       connectaddress - IPv4 address to which to connect.
       connectport    - IPv4 port to which to connect.
       listenaddress  - IPv4 address on which to listen.
       protocol       - Protocol to use.  Currently only TCP is supported.

# This will map the Windows 10.6.0.4 address to the WSL address of 192.168.171.139. Azure will take care of the Public mapping to the 10.6.0.4 private address. 
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=10.6.0.4 connectport=8080 connectaddress=192.168.171.139
```

## On Startup or Restart
Out of the box, windows does not start a wsl cron and the docker service. As IP address in docker may change, we need to activate two things:1) WSL cron; 2) Windows on Startup script

Powershell script
```
#Note private IP address will remain constant; however, the wsl and public ip address could change
wsl.exe sudo /etc/init.d/ssh start
$wsl_ip = (wsl hostname -I).trim()
Write-Host "WSL Machine IP: ""$wsl_ip"""
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=10.6.0.4 connectport=8080 connectaddress=$wsl_ip
netsh interface portproxy add v4tov4 listenport=8081 listenaddress=10.6.0.4 connectport=8081 connectaddress=$wsl_ip
```
Wsl Script
```
sudo service docker start
docker start nginx0
docker start nginx1
```




