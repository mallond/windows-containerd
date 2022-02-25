
```
# from powershell
mkdir data/influxdb2
```
```
docker run --restart unless-stopped --name influxdb2 -p 8086:8086 \
      -v /mnt/c/Users/devops/data/influxdb:/var/lib/influxdb2 \
      -e DOCKER_INFLUXDB_INIT_USERNAME=admin \
      -e DOCKER_INFLUXDB_INIT_PASSWORD=password \
      -e DOCKER_INFLUXDB_INIT_ORG=everi.com \
      -e DOCKER_INFLUXDB_INIT_BUCKET=everi \
      influxdb:2.0
```      
