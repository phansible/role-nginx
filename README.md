# Phansible Role: Nginx

[![CI](https://github.com/phansible/role-nginx/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-nginx/actions/workflows/ci.yml)

An Ansible Role that installs [Nginx](https://nginx.org/) from the distribution packages and configures a default site that hands PHP requests to php-fpm, specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04, 26.04 or Debian 12, 13
- Ansible 2.15 or newer
- PHP requests are passed to `/run/php/php-fpm.sock`, the socket the distro and sury php-fpm packages register for the installed PHP version. Install php-fpm separately, for example with [role-php](https://github.com/phansible/role-php).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
nginx:
    docroot: "/vagrant"
    servername: "myApp.vb"
```

- `nginx.docroot`: document root of the default site.
- `nginx.servername`: `server_name` of the default site.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    nginx:
      docroot: /var/www/app/public
      servername: app.test
  roles:
    - role-php
    - role-nginx
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-nginx/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-nginx/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
