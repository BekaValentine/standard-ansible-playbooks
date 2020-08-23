# standard-ansible-playbooks

A collection of Ansible playbooks that all of my Python web apps have in common.

## Ansible usage

Ansible needs to be told which inventory file to use using `-i` (by default is uses `/etc/ansible/hosts`).

For example, to test your connection to infrastructure by pinging all hosts, run:

```bash
ansible -i hosts all -m ping
```

Or to run all playbooks (i.e. configure all infrastructure):

```bash
ansible-playbook -i hosts playbooks/all.yml
```

## Variables that must be defined

### `$ANSIBLE_HOSTS`

The ssh names of the hosts to deploy to.

### `$CADDY_DOMAIN_NAME`

The domain name of the web app.

### `$APP_NAME`

The name of the app.

### `$APP_REPO`

The git repo url for the app.
