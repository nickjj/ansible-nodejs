## What is ansible-nodejs? [![Build Status](https://secure.travis-ci.org/nickjj/ansible-nodejs.png)](http://travis-ci.org/nickjj/ansible-nodejs)

It is an [ansible](http://www.ansible.com/home) role to install the latest stable version of nodejs without having to compile nodejs on the machine you're setting up.

### What problem does it solve and why is it useful?

Compiling node on a low end VPS/instance could easily take 10 minutes and during that time your CPU is going to be pegged at 100%.

ansible-node solves this by using a rock solid third party apt repository where the author maintains the latest stable version of nodejs for many ubuntu builds. You can also supply your own ppa if you want a different one.

## Role variables

```
---
# The ppa to pull in nodejs.
nodejs_ppa: "ppa:chris-lea/node.js"

# The amount in seconds to cache apt-update.
apt_cache_valid_time: 86400
```

## Example playbook

For the sake of this example let's assume you have a group called **app** and you have a typical `site.yml` file.

To use this role edit your `site.yml` file to look something like this:

```
---
- name: ensure app servers are configured
- hosts: app

  roles:
    - { role: nickjj.nodejs, tags: node }
```

Let's say you want to edit the ppa repo, you can do this by opening or creating `group_vars/app.yml` which is located relative to your `inventory` directory and then making it look something like this:

```
---
nodejs_ppa: "ppa:somewhere/nodejs.js"
```

## Installation

`$ ansible-galaxy install nickjj.nodejs`

## Requirements

Tested on ubuntu 12.04 LTS but it should work on other versions that are similar.

## Ansible galaxy

You can find it on the official [ansible galaxy](https://galaxy.ansible.com/list#/roles/795) if you want to rate it.

## License

MIT