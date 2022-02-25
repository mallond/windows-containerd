## Jenkins

```
# from powershell
mkdir data/jenkins9081
mkdir data/jenkins9082
mkdir data/jenkins9083
mkdir data/jenkins9084
```
```
docker run -d --name jenkins9080 --restart unless-stopped -p 9080:8080 -p 50000:50000 -v /mnt/c/Users/devops/data/jenkins9080:/var/jenkins_home jenkins/jenkins:2.336-jdk11
  
# This takes some time to become accessible due to all the loding plugins
# docker container ls
# sudo docker exec -it jenkins9080 /bin/bash
# cat /var/jenkins_home/secrets/initialAdminPassword
# if needed docker restart jenkins9080
```

> Important note to mapping data. For windows the /User/devops/jenkins9082 needs to be created in powershell. Keep the other jenkin instance directories at this user level.  

Example of five independent containers running: 
```
/User/devops/data/jenkins9081
/User/devops/data/jenkins9082
/User/devops/data/jenkins9083
/User/devops/data/jenkins9084
etc
```
![image](https://user-images.githubusercontent.com/993459/155770750-edb4e87f-982e-4fa7-9075-b4ba70fb1a97.png)

