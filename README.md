# Architecture

## ansible.cfg:
The main Ansible configuration file.

## inventory and inventory_1:
Files containing `lists of hosts/servers` that Ansible will manage.

## Host Variables (host_vars/):
Contains `host-specific variables` **for different servers**:
- Each file contains `variables specific to that host`, like SSH users and configuration templates.

## Files Directory (files/):
Contains `static files used in playbooks`:
- `default_site.html:` Default web page content.
- `sudoer_simone:` **Sudo configuration** for user 'simone'.

## Playbooks:
- `ping.yml:` A simple playbook to test connectivity to hosts.
- `site.yaml:` The main playbook that orchestrates the entire configuration.
    - `sites_before_roles.yaml:` is just same above but before implementing the roles.

## /roles directory:
Contains `modular`, `reusable` **configurations** `split by server function`:

- `base/:` Common configurations **for all servers**.

- `handlers/:` Contains **event handlers triggered by tasks**.

- `tasks/:` **Core configuration tasks**.

- `templates/:` Contains templated config files for SSH **(sshd_config_*.j2)**.

- `web_servers/:` Configuration **specific to web servers**.

- `files/:` **Static files like default web pages**.

## sudoer_simone
Is a sudo configuration file that `grants elevated privileges to the` user simone.
- `simone:` **Username** this rule applies to.
- `ALL:` Allows the rule to **apply from any host/location**.
- `NOPASSWD:` Allows the user to **execute sudo commands without being prompted for a password**.
- `ALL:` Allows executing any command with sudo.
