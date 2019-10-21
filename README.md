# ansible-role-certbot

Here is an ansible role to deploy a letsencrypt ssl certificate on your docker applications.
It is heavily inspired by [this article](https://www.humankode.com/ssl/how-to-set-up-free-ssl-certificates-from-lets-encrypt-using-docker-and-nginx).

## Ansible usage

To use it, simply add this repo as a submodule to your roles.
```
$ git submodule add git@github.com:0b11stan/ansible-role-certbot.git roles/certbot
```

Copy your vars file and edit the file with your prefered vars.
```
$ cp roles/certbot/vars/main.yml.dist roles/certbot/vars/main.yml
```

Then, dont forget to add this role to your main recipe file.

## Docker usage

To use the generated certificates in your docker app simply call the letsencrypt volumes in your `docker-compose.yml`.
```yaml
volumes:
  letsencrypt-config:
    external: true
  letsencrypt-data:
    external: true
  letsencrypt-dh:
    external: true
```

Then, you can can use these volumes inside your typical webserver.
```yaml
services:
  typical_webserver:
    build: ./typical_webserver
    ports:
      - 80:80
      - 443:443
    volumes:
      - letsencrypt-data:/srv/letsencrypt
      - letsencrypt-config:/etc/letsencrypt
      - letsencrypt-dh:/etc/ssl/certs
```

For mor details, see [this ansible project](https://github.com/0b11stan/ansible-martinade) that use [this docker project](https://github.com/0b11stan/docker-martinade).

## Roadmap

- [x] Deploy ssl certificates for multiple domains using certbot conainer.
- [ ] Setup a cron job for automatic renewal of certificates.
