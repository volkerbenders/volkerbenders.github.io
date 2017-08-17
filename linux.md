# Tips and Links regarding linux and stuff

* List open ports
sudo netstat -lptu[n]

```bash
$> sudo netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 172.19.8.20:9990        0.0.0.0:*               LISTEN      22652/java
tcp        0      0 127.0.0.1:11211         0.0.0.0:*               LISTEN      1059/memcached
tcp        0      0 0.0.0.0:9102            0.0.0.0:*               LISTEN      1273/bacula-fd
...
```
