# standard-ansible-playbooks

A collection of Ansible playbooks that all of my Python web apps have in common.

## How To Use These Standard Playbooks

To use these playbooks, you need to have:

- A Debian webserver.
- A Flask-based Python webapp.
- Ansible on your controlling machine.

Additionally, you must define the various variables specified below, as they provide the necessary information for your app to be installed and run.

## Ansible Usage

Ansible needs to be told which inventory file to use using `-i` (by default is uses `/etc/ansible/hosts`).

For example, to test your connection to infrastructure by pinging all hosts, run:

```bash
ansible -i hosts all -m ping
```

Or to run all playbooks (i.e. configure all infrastructure):

```bash
ansible-playbook -i hosts playbooks/all.yml
```

## Variables

The following variables exist within the playbooks. Some of them are mandatory, and are marked as such, others are optional.

### `caddy_domain_name`

Location: caddy.yml

MANDATORY

The domain name of the web app.

### `user_name`

Location: app.yml

MANDATORY

The name of the user and group that runs the app.

### `user_name`

Location: app.yml

MANDATORY

The name of the user that owns the app.

### `app_name`

Location: app.yml

MANDATORY

The name of the app.

### `app_description`

Location: app.yml

MANDATORY

The description of the app to use for the app's systemd service.

### `github_repo`

Location: app.yml

MANDATORY

The git repo url for the app.

### `app_environment`

Location: app.yml

OPTIONAL

The environment variables to use for the systemd service execstart.
