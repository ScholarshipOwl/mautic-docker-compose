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

