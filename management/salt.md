# Salt

Salt is a configuration management tool written in python similar to ansible,
puppet, and chef.  Scripts are written in YAML and Jinja.

Salt is free and open source and licensed under the Apache 2.0 license.

[Website](https://saltstack.com/)
[github](https://github.com/saltstack/salt)

## Ports

Minions listens to Master on port 4505.
Minions send to Master on port 4506.

## Terms

All of the configuration management tools are very similar and use different
terms to further brand their product.

- Configuration Management - see states
- A grain is a static fact about the systemsuch as OS, kernel, and CPU
  architecture.  Custom grains can be set such as physical location in data
  center or role.  Grains are lowercase.
- Master(s) rule(s) Minions
- Orhestration is the act of running commands on several systems at once.
- Pillar is user-defined variables.  Data is stored on the salt master and only
  accessible by minions.  Often pillar distributes secrets.
- States are the declaritive way that the server should be configured.
- YAML Ain't Markup Language is a human friendly data serialization standard for
  all programming languages.

## Ad-hoc example

```
salt '*' user.add user home=/home/user shell=/bin/bash
```

## Declaritive example

```
user:
  user.present:
    - home: /home/user
    - shell: /bin/bash

## Managing Windows

Modules specific to Windows start with ```win_```.
