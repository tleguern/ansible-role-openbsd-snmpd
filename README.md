# `ansible` role `OpenBSD snmpd`

Install and configure `snmpd` from the OpenBSD project.

# Requirements

None

# Role Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `snmpd_user` | User name of `snmpd` | `{{ __snmpd_user }}` |
| `snmpd_group` | Group name of `snmpd` | `{{ __snmpd_group }}` |
| `snmpd_service` | Service name of `snmpd` | `{{ __snmpd_service }}` |
| `snmpd_package` | Package name of `snmpd` | `{{ __snmpd_package }}` |
| `snmpd_conf_dir` | Path to base directory of `snmpd.conf` | `{{ __snmpd_conf_dir }}` |
| `snmpd_conf_file` | Path to `snmpd.conf` | `{{ snmpd_conf_dir }}/snmpd.conf` |
| `snmpd_bin` | Path to `snmpd` | `{{ __snmpd_bin }}` |
| `snmpd_flags` | Additional flags for service `snmpd` | `""` |
| `snmpd_global` | Global parameters | (Optional) |
| `snmpd_users` | Users configuration | (Mandatory) |

## OpenBSD

| Variable | Default |
|----------|---------|
| `__snmpd_user` | `_snmpd` |
| `__snmpd_group` | `_snmpd` |
| `__snmpd_service` | `snmpd` |
| `__snmpd_package` | `""` |
| `__snmpd_conf_dir` | `/etc` |
| `__snmpd_bin` | `/usr/sbin/snmpd` |

# Dependencies

None

# Example Playbook

```yaml
- hosts: localhost
  roles:
    - ansible-role-openbsd-snmpd
  vars:
    snmpd_global:
      system_description: "My little VPS"
      system_location: "My hoster"
    snmpd_users:
    - { name: admin, authkey: {{ authkey }}, enckey: {{ enckey }} }
```

# License

```
Copyright (c) 2019 Tristan Le Guern <tleguern@bouledef.eu>

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

# Author Information

Tristan Le Guern <tleguern@bouledef.eu>

Inspired by work from Tomoyuki Sakurai <y@trombik.org>
