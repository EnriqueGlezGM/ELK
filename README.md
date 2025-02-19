# ELK

First, run docker compose and wait to all containers start:
```console
docker compose up -d
```

Second, you have to log as root in logstash container:
```console
docker exec -it --workdir /root --user root logstash bash
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

To log in to Kibana I recommend resetting the password for the elastic user:
```console
docker exec -it es01 /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
```

Other interesting commands are:
- Stop the container(s) using the following command:
```console
docker compose down
```
- Delete all containers using the following command:
```console
docker rm -f $(docker ps -a -q)
```
- Delete all volumes using the following command:
```console
docker volume rm $(docker volume ls -q)
```
- Delete all images using the following command:
```console
docker rmi $(docker images -aq)
```
