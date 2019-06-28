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

Create an InfluxDB proxy:

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
         telegraf_influxdb_listener_config:
            service_address: ":8186"
            read_timeout: 10s
            write_timeout: 10s
            max_body_size: 0
            max_line_size: 0

License
-------

GPL-3+

Author Information
------------------

Mathieu GRZYBEK
