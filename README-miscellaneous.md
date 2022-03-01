# Miscellaneous

Container Performance 

```
docker container stats

```

![image](https://user-images.githubusercontent.com/993459/155811710-d92b78b5-3bd6-46be-938f-42627149fd73.png)

[influxDb Docker Monitoring](https://www.influxdata.com/influxdb-templates/docker/)

Number of Docker containers  
Network TX traffic per container/sec  
CPU usage per container  
Memory usage % per container  
Memory usage per container  
Network RX traffic per container/sec  

## Get Docker Container IP-Address
```
docker ps
# inspect container id
docker inspect  6d7930b794f6 | grep "IPAddress"
```
