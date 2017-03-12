Ansible - Remote Bluehost backups
=======================

A simple Ansible playbook for remotely backing up databases and folders tested for Bluehost but should work for any kind shared hosting or server. 
Ideal for triggering with a cron.

## Requirements

In the source machine:

* Ansible

In the remote machine

* ssh access
* mysql-python


## Instructions

* Configure it by rename `vars.sample.yml` to `vars.yml` and fil in with your own details.
* Edit the `hosts` file to point to your server or servers.
* Run it: `ansible-playbook -i hosts main.yml`.

You can filter by tags:

* `databases` To backup only databases.
* `folders` To backup only folders.
* `notify` To send an email notification.

Optionally create a cron job like this:

Database backups at 9pm every day 

`0 21 * * *    cd /path/to/playbook; ansible-playbook -i hosts main.yml --tags databases --skip-tags notify`

Folders backups at 9pm every Sunday 

`0 21 * * 7    cd /path/to/playbook; ansible-playbook -i hosts main.yml --tags folders`