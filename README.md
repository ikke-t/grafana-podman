grafana-podman
==============

This role setups up Grafana as container using podman and systemd. It also
pushes configurations to grafana over API.

Requirements
------------

You need to have ansible, and target system having systemd and podman capabilities.


Role Variables
--------------

See the defaults.yml and an example in tests/test.yml and tests/test_vars.yml

* grafana_domain: Grafana's domain config option
* grafana_root_url: Grafana's root_url config option, e.g. ```http://%(domain)s/```,
  or ```https://%(domain)s/grafana```
* grafana_public_url: If your grafana is behind LB, e.g. 'https://example.com/grafana'.
  How do you reach your grafana from outside?
* grafana_admin: Grafana config option admin username
* grafana_admin_default_password: Grafana config option
* grafana_admin_password: By default "{{ grafana_admin_default_password }}"
* grafana_smtp_*: [See manual](https://grafana.com/docs/grafana/latest/alerting/notifications/#email)
* grafana_admins: List of admin users
* grafana_users: List of viewer users
* grafana_dashboards: List of json files or urls
* grafana_datasources: List of datasources
* grafana_email_notification_channels: List of email notification channels

* container_*: Passed to podan_container_systemd role,
  [see options at](https://github.com/ikke-t/podman-container-systemd)


Dependencies
------------

roles:
  - ikke_t.podman_container_systemd
collections:
  - containers.podman
  - community.grafana

Example Playbook
----------------

See tests/test.yml.

License
-------

GPLv2 or later

Author Information
------------------

Ilkka Tengvall
