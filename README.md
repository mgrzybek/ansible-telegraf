ansible-telegraf
================

A role to deploy Telegraf agent.

Requirements
------------


Role Variables
--------------


Dependencies
------------

This is a standalone role.

Example Playbook
----------------

Configure a system/net monitoring with an influxdb backend:

    - hosts: servers
      roles:
         - ansible-telegraf
      vars:
         telegraf_output_influxdb_config:
            urls: ["http://metrics.example.com:8086"]
            database: "telegraf"
            skip_database_creation: true
            retention_policy: ""
            timeout: 5s
            insecure_skip_verify: true

License
-------

GPL-3+

Author Information
------------------

Mathieu GRZYBEK
