# ELK

First, run docker compose and wait to all containers start:
	docker compose up

Second, you have to log as root in logstash container:
	docker exec -it --workdir /root --user root logstash bash

When you are in, you need to change the permissions for config folder:
	chown -R logstash:root /usr/share/logstash/config

Also, due to a bug, you should overwrite logstash.yml:
	cat /usr/share/logstash/config/logstashContent.yml > /usr/share/logstash/config/logstash.yml

When you have done all of this, uncomment logstash pipeline, the file is logstash.conf, and restart logstash container.

Other interesting commands are:
- Stop the container(s) using the following command:
	docker-compose down
- Delete all containers using the following command:
	docker rm -f $(docker ps -a -q)
- Delete all volumes using the following command:
	docker volume rm $(docker volume ls -q)
