libredevops.prometheus.node_exporter
=========

A simple role to install and configure Prometheus Node Exporter as a service on any Linux system (with systemd).

Requirements
------------

Internet connectivity on the host to install node exporter.

Role Variables
--------------

```yaml
prometheus_system_user_name: prometheus

prometheus_node_exporter_installation_path: /var/lib/prometheus
prometheus_node_exporter_binary_name: node_exporter

prometheus_node_exporter_service_enabled: true
prometheus_node_exporter_service_started: true

prometheus_node_exporter_os: linux
prometheus_node_exporter_arch: amd64
prometheus_node_exporter_version: 1.8.1
prometheus_node_exporter_download_url: "https://github.com/prometheus/node_exporter/releases/download/v{{ prometheus_node_exporter_version }}/node_exporter-{{ prometheus_node_exporter_version }}.{{ prometheus_node_exporter_os }}-{{ prometheus_node_exporter_arch }}.tar.gz"

prometheus_node_exporter_extra_args: "--web.listen-address=:9200"

prometheus_node_exporter_collector_enabled:
  - cpu_vulnerabilities

prometheus_node_exporter_collector_disabled:
  - bcache
  - fibrechannel
  - hwmon
  - mdadm
  - nvme
  - powersupplyclass
  - selinux
```

Dependencies
------------

No dependencies

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: linux_servers
      roles:
         - { role: libredevops.prometheus.node_exporter, prometheus_node_exporter_version: 1.8.1 }

License
-------

GPL-v3

Author Information
------------------

[@santiagomr](https://github.com/santiagomr)
