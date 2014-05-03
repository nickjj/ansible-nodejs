## What is ansible-nodejs?

It is an [Ansible](http://www.ansible.com/home) role to install the latest stable version of nodejs without having to compile nodejs on the machine you're setting up.

### What problem does it solve and why is it useful?

Compiling node on a low env VPS/instance could easily take 10 minutes and during that time your CPU is going to be pegged at 100%.

ansible-node solves this by using a rock solid third party apt repository where the author maintains the latest stable version of nodejs for many ubuntu builds. You can also supply your own ppa if you want a different one.

## Role variables

```
---
nodejs_ppa: "ppa:chris-lea/node.js"
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

Let's say you want to edit the ppa repo, you can do this by opening or creating `yourplaybook/group_vars/app.yml` and then making it look something like this:

```
---
nodejs_ppa: "ppa:somewhere/nodejs.js"
```

## Installation

`$ ansible-galaxy install nickjj.nodejs`

## Requirements

Tested on ubuntu 12.04 LTS but it should work on other versions that are similar.

## License

MIT