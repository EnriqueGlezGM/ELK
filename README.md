# ELK

First, run docker compose and wait to all containers start:
```console
$ docker-compose up
```

Second, you have to log as root in logstash container:
```console
$ docker exec -it --workdir /root --user root logstash bash
```
	

When you are in, you need to change the permissions for config folder:
```console
# chown -R logstash:root /usr/share/logstash/config
```

Also, due to permissions, you should overwrite logstash.yml:
```console
# cat /usr/share/logstash/config/logstashContent.yml > /usr/share/logstash/config/logstash.yml
```

When you have done all of this, uncomment logstash pipeline, the file is logstash.conf, and restart logstash container.

Other interesting commands are:
- Stop the container(s) using the following command:
```console
$ docker-compose down
```
- Delete all containers using the following command:
```console
$ docker rm -f $(docker ps -a -q)
```
- Delete all volumes using the following command:
```console
$ docker volume rm $(docker volume ls -q)
```
