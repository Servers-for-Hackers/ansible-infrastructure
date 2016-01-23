# Ansible Role for Nodejs (Debian/Ubuntu)

Chris Lea is working with [nodesource](https://nodesource.com/) to supply Ubuntu users with the latest stable NodeJS. This means the Launchpad PPA is not used anymore.

To help make this easy for users NodeSource and Chris Lea has provided a [shell script](https://deb.nodesource.com/setup) to install NodeJS. That [reasoning and more information is outlined here](https://chrislea.com/2014/07/09/joining-forces-nodesource/).

This Ansible role is a conversion of that shell script, making this role a mirror of the "official" (quotes used emphatically) way to install the latest stable NodeJS on Ubuntu.

## What does it do?

This role mirrors the shell script, running the following tasks:

* Ensure the Ubuntu Distro is Supported. If it is supported, the remaining tasks are run:
* Remove the old Chris Lea NodeJS PPA, if it exists
* Add NodeSource GPG Keys
* Add NodeSource Apt Sources List
* Install NodeJS (and implicitly, npm)
