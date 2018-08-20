# Tasks

## Option format

A task should take options only in the following format:

```yaml
# Removes all anonymous user accounts
- mysql_user:
    name: ''
    host_all: "yes"
    state: "absent"
```

An alternative but **now deprecated** is as follows:

```yaml
---
# Removes all anonymous user accounts
- mysql_user name='' host_all=yes state=absent
```

## Variables

Where a task uses a variable, that variable should be documented in the `${ROLE_ROOT}/defaults/main.yml` file, with
an appropriate default value if possible.

For example, in the following task the variable `sitewards__locales__locales` is used.

```yaml
---
- name: Ensure necessary locales exist
  locale_gen:
    name: "{{ item }}"
    state: present
  with_items: "{{ sitewards__locales__locales }}"
```

This should be documented with in the `${ROLE_ROOT}/defaults/main.yml` as follows:

```yaml
## This variable denotes the locales that should be installed on a given machine. It takes an array of locales
## ensuring each are present.
##
## For a full list of locales (on a Debian based system) see "/usr/share/i18n/SUPPORTED"
## (Optional)
sitewards__locales__locales: []
# - en_US
```

The "Double hash" syntax is used to denote comments that describe the body of the code, and the "Single hash" syntax
is used to denote example code.

## Specific Tasks

### Template

Where the "template" task is used, the template should be reflected in the `templates` directory in the same path it
would appear on the destination infrastructure. For example, if installing an NGINX vhost the layout for the role
would be:

```
tasks/main.yml
templates/etc/nginx/sites-enabled/000-default.conf
```

where the path on the destination machine would be `/etc/nginx/sites-enabled/000-default.conf`.

The task would then look like:

```
- name: "Install the NGINX default vhost"
  template:
    src: "etc/nginx/sites-enabled/000-default.conf"
    dest: "/etc/nginx/sites-enabled/000-defualt.conf"
    owner: "root"
    mode: "u=rw,g=r,o=r"
```
