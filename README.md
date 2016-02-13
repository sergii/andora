# Andora

Andora is ansible roles to deploy Ruby on Rails applications with docker containers in a capistrano style
Project name is [an]sible, [do]cker and [ra]ils

## Features

- Setup a host with dependencies and structure of directories
- Deploy a release
- Export database data
- Rollback to the previous release

## Requirements

- Docker in your deployer machine

## Usage

Install andora

```
$ cd project
$ git clone git@github.com:weazar/andora.git ansible
```

Run an ansible docker container

```
$ cd ansible
$ docker run -v ~/.ssh:/root/.ssh -v "$PWD":/mnt/src -w /mnt/src --rm -it weazar/ansible /bin/bash
```

Setup a host

```
$ ansible-playbook playbooks/setup.yml
```

Deploy release

```
$ ansible-playbook playbooks/deploy.yml
```

Export database data

```
$ ansible-playbook playbooks/export_data.yml
```

Rollback to the previous release

```
$ ansible-playbook playbooks/rollback.yml
```
