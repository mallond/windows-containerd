## Jenkins
```
docker run -d --name jenkins9080 --restart unless-stopped -p 9080:8080 -p 50000:50000 -v /mnt/c/Users/devops/jenkins9080:/var/jenkins_home jenkins/jenkins:lts-jdk11 
  
# This takes some time to become accessible due to all the loding plugins
# docker container ls
# sudo docker exec -it jenkins9080 /bin/bash
# cat /var/jenkins_home/secrets/initialAdminPassword

> Important note to mapping data. For windows the /User/devops/jenkins9082 needs to be created in powershell. Keep the other jenkin instance directories at this user level.  

Example of five independent containers running: 
```
/User/devops/jenkins9081
/User/devops/jenkins9082
/User/devops/jenkins9083
/User/devops/jenkins9084
etc
```
