modcloth.npi
============

This role installs the New Relic Platform Installer. It also allows
installation and configuration of npi plugins.

For any plugins installed, this role adds an upstart managed service
configuration.

Requirements
------------

NodeJS and Java should be installed

Role Variables
--------------

See `defaults/main.yml` for defaults.

```yml
npi_prefix: # Location to install NPI
npi_bin_path: # Location to place npi binary (should be in $PATH)
npi_remote_install_script: # URL to download the installer from

# List of npi plugins to install
# Should be key/value pairs with:
#   key: plugin name
#   value: configuration (another map of key/value pairs)
# List of configuration options:
#   template: # Template to use to generate plugin.json (plugin.json is written only if this is set)
npi_plugins:

# the below variables are used to generate newrelic.json for the plugin
# see: https://github.com/newrelic-platform/newrelic_memcached_java_plugin for example
new_relic_license_key: # New Relic license key
new_relic_log_level: # log level for plugin 
new_relic_log_file_name: # log filename for plugin
new_relic_file_path: # log file path for plugin
new_relic_log_limit_in_kbytes: # limit for log file size

# proxy settings (if collection goes through an outbound proxy)
new_relic_proxy_host
new_relic_proxy_port
new_relic_proxy_username
new_relic_proxy_password
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
