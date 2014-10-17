modcloth.npi
============

This role installs the New Relic Platform Installer. It also allows
installation and configuration of npi plugins.

For any plugins installed, this role adds an upstart managed service
configuration.

Requirements
------------

None

Role Variables
--------------

See `defaults/main.yml` for defaults.

```yml
npi_prefix: # Location to install NPI
npi_bin: # Location to place npi binary (should be in $PATH)
npi_download: # URL to download the installer from
npi_java_package: # Java runtime package name

# List of npi plugins to install
# Should be key/value pairs with:
#   key: plugin name
#   value: configuration (another map of key/value pairs)
# List of configuration options:
#   template: # Template to use to generate plugin.json (plugin.json is written only if this is set)
npi_plugins:

new_relic_license_key: # New Relic license key
```

Dependencies
------------

None

Example Playbook
----------------

```yml
- hosts: servers
  roles:
  - role: modcloth.npi
    new_relic_license_key: ABCDE
    npi_plugins:
      com.newrelic.plugins.mysql.instance:
        template: templates/plugins.json.j2
```

License
-------

MIT

Author Information
------------------

Modcloth, Inc.
