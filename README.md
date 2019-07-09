shellbro.systemd_alert_services
===============================

Ansible role for creating systemd alert services (CentOS 7).

Alert services can be used in `OnFailure=` definitions of other units to issue
notifications about failures. Two alert services are created at the moment
`alert-email@` and `alert-slack@`. It uses
[slacktee](https://github.com/coursehero/slacktee) for Slack integration.


Requirements
------------

Ansible version >= 2.4.

In addition, `slacktee` configuration file `.slacktee` must be present in
Ansible working directory (or `files` directory). `.slacktee` has the form of:

```
webhook_url=""
token="[YOUR_TOKEN_HERE]"
tmp_dir="/tmp"
channel="general"
username="systemd"
icon="ghost"
attachment=""
```

Role Variables
--------------

* user - run alert services as this user (by default `root`)
* email - email address or username who receives email notification (by default
`root`)

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: shellbro.systemd_alert_services
          user: devops

License
-------

BSD

Author Information
------------------

Jakub Gorczyca
