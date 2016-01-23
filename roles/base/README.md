ansible-basic-server
====================

Basic Ubuntu Server Setup

This installs basic software for Ubuntu servers.

### Unattended Upgrades

This repository will enable unattented security updates. It will not allow the server to reboot itself, however. When you log in, you may receive messages saying the server requires a reboot. It would be good to reboot your server at those times.

If this is an issue, you may wish to setup a configuration (load balancer with 2+ web nodes) that will allow for failover if you choose to restart your server(s) at this time.