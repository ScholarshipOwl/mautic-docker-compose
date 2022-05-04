# Mautic Docker-Compose
Repository includes docker-compose configurations and documentation for running Mautic in docker.

## Install
Make sure you have docker-compose and docker installed.

### Start
Start docker containers:
```shell
docker-compose up
```

Now open:
```shell
http://localhost:8080
```

Finish setup and you are ready to use.
### Database Setup
Leave configs untouched in order to use pre-configured MySQL server.

You may connect to database from docker container.
By default, we do not map MySQL server port to the localhost port as we suggest you have mysql running.
We propose to override local docker-compose.yaml and map mysql container port to localone.

File: `docker-compose.override.yml` ⇩
```yaml
version: '3'

services:
  mauticMysql:
    ports:
      - 3316:3306
```

Now you can connect to DB on localhost and port `3316`. Username `root` and password `secret`.

```shell
mysql -h 127.0.0.1 -P 3316 -u root -psecret
```

### Mailhog SMTP Server
You may use [Mailhog](https://github.com/mailhog/MailHog) server for testing the emails.

On email configuration step set mail transport to "Other SMTP Server" and next SMTP server `mauticMailhog` port `1025`.
Leave encryption and authentication mode "None".

Open mailhog in browser by link:
```shell
https://localhost:8025
```

## Persistence
By default code and database will be persistent. You may disable it by commenting out the `volumes` form docker-compose.yaml file.

#### Code and Media
Mautic code will be copied into `.storage/mautic` on first start. It is done in order to persist uploaded files and test plugins.

#### MySQL
MySQL data is saved in `.storage/media`

