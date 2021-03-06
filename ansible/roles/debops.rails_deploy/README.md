## [![DebOps project](http://debops.org/images/debops-small.png)](http://debops.org) rails_deploy

[![Travis CI](http://img.shields.io/travis/debops/ansible-rails_deploy.svg?style=flat)](http://travis-ci.org/debops/ansible-rails_deploy) [![test-suite](http://img.shields.io/badge/test--suite-ansible--rails__deploy-blue.svg?style=flat)](https://github.com/debops/test-suite/tree/master/ansible-rails_deploy/)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-debops.rails__deploy-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1591)

`debops.rails_deploy` role allows you to easily setup infrastructure
capable of running Rails applications. It removes all of the headaches
associated to setting up a secure Rails app that is ready for production so
you can concentrate on developing your app.

#### High level goals

- Setup an entire rails app server with 1 line of configuration with sane defaults
- Optionally and easily separate your app servers, database and worker into
  multiple servers
- Quickly and easily switch between popular default databases and backend servers
- Be as secure as possible and adhere to as many best practices as possible

#### Backups and logging

- Postgresql runs a daily backup with daily/weekly rotation
- Both your backend server and background worker get logged to 1 logrotated file
- The rails process gets sent to syslog.user

#### System level minutia

- User accounts, permissions and ssh keys are automatically managed
- Paths such as logs, pids and sockets are automatically managed

#### Deploy features

- Automatically set deploy keys to github/gitlab with 1 line of configuration
  - This leverages their API, all you have to do is supply their token
- Keep track of your schema file and config folder's mtime in local facts
  - This allows the deploy task to attempt to guess if your server needs a full restart or a quick reload
- Only run database commands from a single master app server
  - This master is defined by simply being first in the group list
- Various options to turn certain features on/off
  - A few examples would be database creation, migration and force restarting your server
- Add custom services which get restarted/reloaded at the end of the deploy cycle
  - If you have a SOA setup this could be handy
- Add and remove custom tasks at various points in the deploy
  - By default it is set to precompile assets and clear the /tmp cache
- Optionally swap a static deploy page in/out during the deploy cycle

#### Security

- Secure passwords are managed automatically for your database
- Ports are blocked and only whitelisted for IP addresses/masks that you specify
- SSL is enabled by default but can be turned off if you really don't want it
- Self signed SSL certs are automatically managed for you
  - Changing to properly signed certificates is a breeze

### Installation

This role requires at least Ansible `v1.7.0`. To install it, run:

    ansible-galaxy install debops.rails_deploy

### Documentation

More information about `debops.rails_deploy` can be found in the
[official debops.rails_deploy documentation](http://docs.debops.org/en/latest/ansible/roles/debops.rails_deploy.html).


### Role dependencies

- `debops.etc_services`
- `debops.redis`
- `debops.nginx`
- `debops.nodejs`
- `debops.mysql`
- `debops.ruby`
- `debops.monit`
- `debops.secret`
- `debops.postgresql`

### Are you using this as a standalone role without DebOps?

You may need to include missing roles from the [DebOps common
playbook](https://github.com/debops/debops-playbooks/blob/master/playbooks/common.yml)
into your playbook.

[Try DebOps now](https://github.com/debops/debops) for a complete solution to run your Debian-based infrastructure.





### Authors and license

`rails_deploy` role was written by:
- Nick Janetakis | [e-mail](mailto:nick.janetakis@gmail.com) | [Twitter](https://twitter.com/nickjanetakis) | [GitHub](https://github.com/nickjj)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

***

This role is part of the [DebOps](http://debops.org/) project. README generated by [ansigenome](https://github.com/nickjj/ansigenome/).
