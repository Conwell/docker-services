# Common docker services
Common docker services for projects with traefik network

## Include:
 - traefik:v2.1 dashboard http://traefik.${HOST_IP}.xip.io
 - mariadb:10.4 with phpmyadmin http://phpmyadmin.${HOST_IP}.xip.io
 - elasticsearch:7.5.2 with sense UI http://sense.${HOST_IP}.xip.io/app/sense
   use elasticsearch:9200 as elastic server
 - maildev user interface http://maildev.${HOST_IP}.xip.io
 - rabbitmq:3.8 manageable with UI http://rabbitmq.${HOST_IP}.xip.io
 - redis:5 with UI redis-commander http://redis-commander.${HOST_IP}.xip.io
 - sftp with login `sftp -P 2222 ${FTP_USER}@$0.0.0.0`
 
_**${HOST_IP}** and **${FTP_USER}** set in `.env` file_


### Setup and run
Copy or create new **.env** file from **.env.dist**

`cp .env.dist .env`

then for start services 

`docker-compose up -d`

### Disable one or more services on start
If you want you can change any env variable that will be used in containers.

For disable one or some containers just create new `docker-compose.override.yml` with content like this:

```
version: '3.7'
  
  services:
  
    phpmyadmin:
      restart: no
      entrypoint: ["echo", "Service phpmyadmin disabled"]

```

This will disable phpmyadmin service.
