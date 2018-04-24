Ansible role: resolv
=========

[![MIT licensed][mit-badge]][mit-link]
[![Galaxy Role][role-badge]][galaxy-link]

This role generates custom */etc/resolv.conf* for quick and smart DNS setup during configuration management.
The role is primarily used as a dependency for other roles in the environment which doesn't have stable dns resolver
configuration.
For example when testing local dns server setup, this role can be used as temporary resolv configuration for installing
dependencies.

Optionally it can lock the */etc/resolv.conf* file by changing it's 'i' attribute.

Requirements
------------

One of the following OS (or deriviatives):
 - Debian (Raspbian, Minibian)
   - all


Role Variables
--------------
| Variables | Description | Default|
|-----------|-------------|--------|
| **resolv_nameservers** | The list of dns resolvers to be added to */etc/resolv.conf* | `9.9.9.9` |
| **resolv_lock** | Whether or not to lock the */etc/resolv.conf*. Useful when setting up the dns resolver which uses DHCP but does not need to use DNS resolver pushed by DHCP server | `no` |

Dependencies
------------

None

Example Playboouk
----------------

    - hosts: rpi_3
      roles:
         - { role: drew-kun.resolv, resolv_lock: no }

License
-------

[MIT][mit-link]

Author Information
------------------

Andrew Shagayev | [e-mail](mailto:drewshg@gmail.com)

[role-badge]: https://img.shields.io/badge/role-drew--kun.resolv-green.svg
[galaxy-link]: https://galaxy.ansible.com/drew-kun/resolv/
[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://raw.githubusercontent.com/drew-kun/ansible-resolv/master/LICENSE
