# Ansible Role: nginx_web

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

This Ansible role installs **Nginx** on a target system and deploys a **custom HTML page** (`index.html`) for the "Sandra Tech" website. It is designed to be reusable and production-ready, following best practices with separate directories for tasks, handlers, vars, defaults, and templates.

---

## Table of Contents

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
- [Directory Structure](#directory-structure)
- [License](#license)

---

## Requirements

- Ansible 2.9+
- Target system: Linux (tested on Ubuntu, CentOS, Amazon Linux)
- Nginx package available in the system repositories

---

## Role Variables

| Variable      | Default                  | Description                              |
|---------------|--------------------------|------------------------------------------|
| `web_root`    | `/usr/share/nginx/html`  | Destination directory for `index.html`  |
| `owner`       | `nginx`                  | Owner of deployed files                  |
| `group`       | `nginx`                  | Group of deployed files                  |

You can override these variables in your playbook or inventory.

---

## Dependencies

None. This role is standalone.

---

## Example Playbook

```yaml
- hosts: webservers
  become: yes
  roles:
    - nginx_web

---

## Directory Structure

nginx_web/
├── tasks/
│   └── main.yml            # Install nginx and copy HTML
├── handlers/
│   └── main.yml            # Restart Nginx, wait for port 80
├── templates/
│   └── index.html.j2       # HTML template for Sandra Tech website
├── vars/
│   └── main.yml            # Role-specific variables
├── defaults/
│   └── main.yml            # Default variables (overridable)
├── meta/
│   └── main.yml            # Role metadata
└── README.md               # This file



