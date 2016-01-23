ansible-nginx
=============

Ansible Role for Nginx

## Dependencies

This depends on an SSL role, which is not a public github repository as it contains SSL certificate/key files. While they are encrypted, I still don't want it up on a public git repository.

See the [ansible-ssl-example](https://github.com/Servers-for-Hackers/ansible-ssl-example) role in this repository for an example of that.

## Serversforhackers.com Usage

This role setups configurations for potentially any site, but I can and will put serversforhackers.com specifics into this repository!

### Variables Used:

* **ssl_key** - Path to the ssl key used to generate the CSR and certificate for SSL certificates pertaining to this site
* **ssl_crt** - Path to the the root domain ssl certificate
* **ssl_wildcard_crt** - Path to the wildcard subdomain ssl certificate
* app_env - APPENV environment variable passed to PHP application

## PHP Configuration

This repository will assume PHP-FPM is running in a chroot'ed environment. I chroot PHP-FPM to the `/var/www` directory. This means Nginx must pass file paths (document root, script file name, etc) to PHP as if the `/var/www` directory is the root `/` directory.

These assumptions are built into the location block passing requests to PHP. Be aware of that before using this Ansible role!
