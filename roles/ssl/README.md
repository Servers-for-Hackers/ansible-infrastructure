ansible-ssl-example
===================

Example Ansible Role for SSL

The `vars/main.yml` file should contain your SSL certificate private key and certificate file contents.

```yml
---
ssl_key: |
    KEY STUFF HERE

ssl_crt: |
    CERT STUFF HERE
```

You should not save these in plaintext, however.

## Ansible Vault

Rather than save SSL contents in plaintext, we can instead (with Ansible 1.5), use [Ansible Vault](http://www.ansible.com/blog/2014/02/19/ansible-vault). This will let you encrypt any YAML file contents.

### 1. Create An Encrypted File

    ansible-vault create vars/main.yml

This will ask you for a password, which you'll need to later use the variable file (so Ansible can read its contents).

You can encrypt an already-existing existing file as well:

    ansible-vault encrypt vars/main.yml

### 2. Edit the YAML File

You'll be brought into the file to edit. This defaults to vim. When you save the file, the file's contents will be encrypted.

In order to go back and edit the file later, you can go back into via the `ansible-vault` command again:

    ansible-vault edit vars/main.yml

You'll be prompted for the password to get back into the file for editing.

This `ssl_key` and `ssl_crt` variables I defined in `vars/main.yml` are used inside of the `tasks/main.yml` file to add an SSL certificate onto the server being provisioned.

### 3. Run Ansible Playbooks

Setup a main playbook which uses the roles:

```yml
---
- hosts: web
  roles:
    - server
    - user
    - ssl
    - nginx
    - php
```

Then you can run it. Note we need to use the `--ask-vault-pass` so that Ansible can decrypt the encrypted variable file:

    ansible-playbook sfh.yml -s -k -u vagrant --ask-vault-pass

The above command is what I use when testing in Vagrant:

* `ansible-playbook` - run a playbook
* `sfh.yml` - use the `sfh.yml` file
* `-s` - Use "sudo" for running commands
* `-k` - Use password authentication (I don't have an SSH keys setup in this case). Since user Vagrant has passwordless sudo abilities, this technically isn't needed to run commands, but we need to tell Ansible not to assume that we're using key-based authentication
* `-u vagrant` - Use user "vagrant" when running commands
* `--ask-vault-pass` - Ask the Vault password so Ansible can read encrypted files

