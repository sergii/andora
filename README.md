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
$ docker run -v ~/.ssh:/root/.ssh -v "$PWD":/mnt/src --rm -it weazar/ansible /bin/bash
```

Set variables in `group_vars/webservers`

- Set your app name
- Set git repository path

Set environment variables in `playbooks/roles/deploy/templates/env.j2`

- RAILS_ENV=production
- PORT=3000
- MYSQL_ROOT_PASSWORD=password
- MYSQL_USER=app_name
- MYSQL_PASSWORD=password
- MYSQL_DATABASE=app_name_production
- DEFAULT_URL_OPTIONS='//domain_name'
- SECRET_KEY_BASE=secret_key # For generate secret key use the command `rake secret`

Setup a host

```
$ ansible-playbook playbooks/setup.yml
```

Deploy release

```
$ ansible-playbook playbooks/deploy.yml
```

Export database data

- Put your dump.sql file to `playbooks/roles/export_data/files/dump.sql`

```
$ ansible-playbook playbooks/export_data.yml
```

Rollback to the previous release

```
$ ansible-playbook playbooks/rollback.yml
```

**How to configure docker for rails application see [weazar/dora](https://github.com/weazar/dora)**

## License

Author: Yuri Smirnov <hello.wwweb@gmail.com>

Licensed under the [MIT License](http://www.opensource.org/licenses/MIT).
