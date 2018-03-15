# Show detailed information about all active docker networks

Docker creates separate networks for each deployed container on the fly.
You can also define networks manually using `docker network create ...`.

The other day one of the automagically created docker networks used the same ip-address range as the machines in our DMZ do.
Resulting in a jenkins not being able to reach our code repository - ouch!

First approach: 
```bash
nb-syngeni350-2:clone_and_build vbe$ docker network ls
NETWORK ID          NAME                                 DRIVER              SCOPE
75395ceaf6fc        bridge                               bridge              local
14c470a3331f        dockerreviewboard_default            bridge              local
451687ada456        dockersonarqube_default              bridge              local
c9453bffec39        dockprom_monitor-net                 bridge              local
4b745e59e3bf        herokukotlingettingstarted_default   bridge              local
a6751fdc44cb        host                                 host                local
727293b514ed        none                                 null                local
b61749a36eb4        piwikcompose_default                 bridge              local
579be723f6ce        itzelbritzel                         bridge              local
6153c06203f3        sonar_default                        bridge              local
6acb102ed6c5        sonarqube_default                    bridge              local
b7b00e885f5e        uumsonar_default                     bridge              local
``` 

Now, what you can do to get more detailed information is
```bash
docker network inspect <NETWORK-ID | NAME>

nb-syngeni350-2:vbe$ docker network inspect 14c470a3331f
[
    {
        "Name": "dockerreviewboard_default",
        "Id": "14c470a3331f8d2c1f92902ef55b04cab3debe5beecd4314d02a60d1cf030e3d",
        "Created": "2017-11-07T13:02:06.422193119Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.23.0.0/16",
                    "Gateway": "172.23.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]
```

Nice. But to get a complete overview i combined the first and the latter in a script:

```bash
#!/bin/sh

ids="$(docker network ls |grep -v NETWORK | awk '{print $1}')"

for id in $ids
do
  docker network inspect "$id" \
    | jq '.[] | (.Name + ": " + .IPAM.Config[].Subnet)'
done
```

The result look like this:

```bash
nb-syngeni350-2:clone_and_build vbe$ showDockerNetworks.sh
"bridge: 172.17.0.0/16"
"dockerreviewboard_default: 172.23.0.0/16"
"dockersonarqube_default: 172.19.0.0/16"
"dockprom_monitor-net: 172.22.0.0/16"
"herokukotlingettingstarted_default: 172.24.0.0/16"
"piwikcompose_default: 172.26.0.0/16"
"itzelbritzel: 172.25.0.0/16"
"sonar_default: 172.18.0.0/16"
"sonarqube_default: 172.20.0.0/16"
"uumsonar_default: 172.21.0.0/16"
```







