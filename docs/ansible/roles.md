# Roles

## "Known Good" role providers:

Note: The usage of these roles do not relieve you of the responsibility of doing a manual code review.

- [Sitewards](https://github.com/sitewards/)
- [Jeff Geerling](https://github.com/geerlingguy)
- [Julien](https://github.com/juju4)

## Naming

Roles should be named in the format:

```
${VENDOR}.${ROLE}
```

Some examples include:

```
sitewards.developer-access
geerlingguy.mysql
juju4.falco
```

Where possible, it is preferred to use the hyphen (`-`) character over the underscore (`_`) character.

## ${INVENTORY} specific roles

**Do not write them**. Examples such as:

```
   - { role: clamav, when: "current_env == 'production'" }
```

Are an antipattern. The pose several problems:

- Ansible cannot be adequately tested, except by applying it to produciton
- The roles are inherently unstable, being less subject to the same review as other roles
- The roles are not reusable

Instead, if roles are not required in a given environment supply configuration that implies
they are empty. For example, in the case of:

```
  - "sitewards.lets-encrypt"
```

Supplying the host fact:

```
lets_encrypt_resources: []
```

will apply only a minimal configuration, and request zero certificates.

