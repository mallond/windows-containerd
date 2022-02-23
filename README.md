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

Windows Firewall Defender - Advanced Security
```
Open ports that need to be open
```

```
#find the wsl IP address
wsl hostname -I
```




