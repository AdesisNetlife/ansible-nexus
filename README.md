# Readme

## Description

*ansible-nexus* is an [Ansible](http://ansible.com) role.
Use this role to install Sonatype Nexus.

## Provides

1. Latest Nexus server

## Requires

1. Ansible 1.7 o higher
2. Ubuntu Server 14.04
3. Vagrant (optional)

## Usage

### Get the code

```bash
$ git clone git@github.com:AdesisNetlife/ansible-nexus.git
```

The code should reside in the roles directory of ansible ( See [ansible documentation](http://docs.ansible.com/playbooks.html#roles) for more information on roles ), in a folder named nexus.

### Create a host file

Following example make ansible aware of the Vagrant box reachable on localhost port 2222.

```bash
$ vi ansible.host
```

with

```ini
[nexus]
127.0.0.1 ansible_ssh_port=2222
```

### Create host specific variables

### Run the playbook

First create a playbook including the nexus role, naming it nexus.yml

```yml
- name: Nexus
  hosts: nexus
  roles:
    - ansible-nexus
```

Use *ansible.host* as inventory. Run the playbook only for the remote host *nexus*. Use *vagrant* as the SSH user to connect to the remote host. *-k* enables the SSH password prompt.

```bash
$ ansible-playbook -k -i ansible.host nexus.yml -u vagrant
```