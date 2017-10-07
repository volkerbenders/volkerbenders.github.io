# Docker Links

* [How to set Java heap size (Xms/Xmx) inside Docker container?](https://stackoverflow.com/questions/29923531/how-to-set-java-heap-size-xms-xmx-inside-docker-container)
* [Volker: Testen docker sonarqube](https://github.com/pascalgrimaud/docker-sonarqube)
* Getting Filesystem Mountpoints from running Docker container
  Usually done with
  ```bash
  $> docker inspect uumsonar_sonarqube_1
[
    {
        "Id": "188e05a3885873121d5110336a264d2440873d9dd2f6293bfa8d41ee42149931",
        "Created": "2017-08-17T15:16:01.891731621Z",
        "Path": "./bin/run.sh",
        "Args": [
        ...
  ```
  Resulting in a quite verbose output with a lot of stuff that distracts you from the info you're looking for.
  [JQ to sthe rescue]()
  JQ is like *nix `grep` but for structured JSON data

  The Mountpoint lookup can be written like this:
  ```bash
  $> docker inspect uumsonar_sonarqube_1 | jq '.[0] | .Mounts'
[
  {
    "Type": "bind",
    "Source": "/home/vbe/dev/uum_sonar/sonarqube",
    "Destination": "/opt/sonarqube/data",
    "Mode": "rw",
    "RW": true,
    "Propagation": "rprivate"
  }
]
  ```
## Best Practices
- [Favour VOlumes over bind mount](https://docs.docker.com/engine/admin/volumes/volumes/#start-a-container-with-a-volume)


## Docker setup / installation
- [local image store location](https://stackoverflow.com/questions/19234831/where-are-docker-images-stored-on-the-host-machine?rq=1)
## Monitoring
- [Aru Guptas Codeship](https://blog.codeship.com/monitoring-docker-containers/)
- [5 Methods for Docker Monitoring](https://plus.google.com/+JavaCodeGeeks/posts/RHr4tX8REiz)
- [Prometheus](https://docs.docker.com/engine/admin/prometheus/)
- [cAdvisor](https://oliverveits.wordpress.com/2016/11/02/how-to-set-up-docker-monitoring-via-cadvisor-influxdb-and-grafana/)
