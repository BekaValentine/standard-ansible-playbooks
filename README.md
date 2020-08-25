# standard-ansible-playbooks

A collection of Ansible playbooks and roles that all of my Python web apps have in common.

## How To Use These Standard Playbooks

To use these playbooks, you need to have:

- A Debian webserver.
- A Flask-based Python webapp.
- Ansible on your controlling machine.

With these resources, you can then modify the `all.yml` playbook. There, you will find a `caddy` role which has its variables commented out. You will need to uncomment the variable and give a value in place of `...`. You will also see an `app` role, which is completely commented out. Similarly, you need to uncomment this and give values for variables for each app you wish to deploy.

If the git repo is private, you should place a copy of the private key into a file in the `playbooks` directory, and then supply the `github_deploy_key` variable, with the filename, to the `app` role.

in app.yml in the git clone task. Make sure that is a deploy key for the repo (NOT a new key in your github account).

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

The following variables exist within the roles. Some of them are mandatory, and are marked as such, others are optional.

### Caddy Role Variables

These variables are used in the `caddy` role.

#### `caddy_domain_name`

MANDATORY

The domain name of the web app.

### App Role Variables

These variables are used in the `app` role.

#### `user_name`

MANDATORY

The name of the user and group that runs the app.

#### `user_name`

Location: app.yml

MANDATORY

The name of the user that owns the app.

#### `app_name`

MANDATORY

The name of the app.

#### `app_description`

MANDATORY

The description of the app to use for the app's systemd service.

#### `github_repo`

MANDATORY

The git repo url for the app.

#### `github_deploy_key`

OPTIONAL

The file name of the private key for github deployment.

#### `app_environment`

OPTIONAL

The environment variables to use for the systemd service execstart.
