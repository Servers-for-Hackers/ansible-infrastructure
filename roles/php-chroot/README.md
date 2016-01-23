PHP5 with Chroot
===============

Ansible Role for PHP and PHP-FPM

## Chroot PHP5

This Ansible role creates PHP-FPM resource pool which is chroot'ed to the `/var/www` directory. 

**The assumed/hard-coded chroot directory may not fit your needs.**

This means that in PHP-FPM's eyes, the entire server is only what's inside of the `/var/www` directory.

This is good for security, but there are measurable conquences for this:

1. A `/tmp` directory for uploads must be accessible to PHP.
2. A sessions directory (I chose `/tmp/sessions`) must be accessible for PHP
3. Timezone settings will give errors without `/usr/share/zoneinfo` files and possibly without `/etc/localtime` file being accessible.
4. The usual `/dev/null`, `/dev/random` and `/dev/urandom` "special device files" may need to be accessible. In particular, `/dev/urandom` is used by Symfony's security classes to generate random numbers.

<!-- -->

> Note: All file paths above appear as such to chroot'ed PHP, but in reality live inside of the `/var/www` directory. See the `tasks/chroot.yml` file to see that configuration being setup.

