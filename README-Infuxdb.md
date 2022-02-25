docker run --restart unless-stopped -p 8086:8086 \
      -v ~/data/influxdb2:/var/lib/influxdb2 \
      -e DOCKER_INFLUXDB_INIT_USERNAME=admin \
      -e DOCKER_INFLUXDB_INIT_PASSWORD=password \
      -e DOCKER_INFLUXDB_INIT_ORG=everi.com \
      -e DOCKER_INFLUXDB_INIT_BUCKET=everi \
      influxdb:2.0
