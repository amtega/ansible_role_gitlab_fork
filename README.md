# Amtega gitlab_fork role

This is an [Ansible](http://www.ansible.com) role to fork a GitLab project.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

The role setups the following facts:

- `gitlab_fork_fact`: dictionary with the result of the fork

## Example Playbook

This is an example playbook:

``` yaml
---
- name: gitlab_fork role sample
  hosts: localhost
  roles:  
    - amtega.gitlab_fork
  vars:    
    gitlab_fork_project_path: /myproject
    gitlab_fork_allow_duplicated: no
```

## Testing

Tests are based on docker containers. You can setup docker engine quickly using the playbook `files/setup.yml` available in the role [amtega.docker_engine](https://galaxy.ansible.com/amtega/docker_engine).

Once you have docker, you can run the tests with the following commands:

```shell
$ cd amtega.gitlab_fork/tests
$ ansible-playbook main.yml
```

To run test you must pass the following set of variables, that can be defined in the inventory or passed in the command line:

- `gitlab_fork_test_gitlab_cli_api_url`: gitlab cli api url
- `gitlab_fork_test_gitlab_cli_api_version`: gitlab cli api (default is 4)
- `gitlab_fork_test_gitlab_cli_token`: gitlab cli token to connect
- `gitlab_fork_test_gitlab_cli_validate_certs`: validate certs when calling gitlab cli (default is `no`)
- `gitlab_fork_test_project_path`: path of the project to fork in gitlab
- `gitlab_fork_test_allow_duplicated`: allow or not duplicated forks (default is `no`)

One way to provide all the previous information is calling the testing playbook an additional vault inventory plus the default one provided for testing, as it's show in this example:

```shell
$ cd amtega.gitlab_fork/tests
$ ansible-playbook main.yml -i inventory -i ~/mycustominventory.yml --vault-id myvault@prompt
```

## License

Copyright (C) 2019 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García.
