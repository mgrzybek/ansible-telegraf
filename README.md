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

Set agent options:

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
         telegraf_main_config:
            global_tags:
                os_project: "cloud-1"
            add_node_type: false
            agent:
                interval: "{{ telegraf_metrics_agent_interval_seconds }}"
                round_interval: false
                metric_batch_size: 1024
                metric_buffer_limit: 10240
                collection_jitter: 8s
                flush_jitter: 8s
                precision: ""
                debug: false
                quiet: false
                logfile: ""
                omit_hostname: false
            
License
-------

GPL-3+

Author Information
------------------

Mathieu GRZYBEK
