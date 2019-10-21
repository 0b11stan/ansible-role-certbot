# ansible-role-certbot

Here is an ansible role to deploy a letsencrypt ssl certificate on your docker applications.

## Usage

To use it, simply add this repo as a submodule to your roles.
```
$ git submodule add git@github.com:0b11stan/ansible-role-certbot.git roles/certbot
```

Copy your vars file and edit the file with your prefered vars.
```
$ cp roles/certbot/vars/main.yml.dist roles/certbot/vars/main.yml
```
