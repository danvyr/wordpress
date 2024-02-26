# Wordpress with redis, nginx and certbot (letsencrypt), installing with ansible in docker-compose

## About

Quick installation wordpress using Ansible on Ubuntu.

What Ansible script is doing:

1. Adding new user to Ubuntu Linux
1. Install docker compose
1. Up Wordpress, nginx, redis, certbot and MariaDB containers
1. Configure domain and redis in `wp-config.php`
1. Add to cron cert-bot for renewing certificates for domain.
1. Some files permissions fixes

## How to use

1. Edit your DNS zone to bound your domain and your IP, so Let's Encrypt could check that you have rights on your domain name.
1. Put your varialbes in ansible/roles/wordpress/vars/main.yaml
1. Add you server to inventory.ini
1. Run ansible: `ansible-playbook site.yaml -i inventory.ini`
1. Cert-bot should successfully received certificate `docker logs certbot`
1. After that uncoment NGINX configuraition for SSL `ansible/roles/wordpress/template/nginx.conf.j2`
1. Running ansible job again or uncoment on server and execute `docker restart webserver`

## Wordpress plugins

1. Object Cache - for redis cahcing (need to enable chaching on after activation)
1. WP Super Cache - html caching (need to enable chaching on after activation)
1. Classic Editor
1. All In One WP Security

## Wordpress tips

1. Move admin page with plugin All In One WP Security
