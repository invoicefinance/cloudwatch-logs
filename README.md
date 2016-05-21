Role Name
=========

Installs AWS CloudWatch Log Agent

Requirements
------------

Requires ec2_facts.

Role Variables
--------------

List of logs with the following keys

| Name       | Description            | Required
|------------|------------------------|---------
| file       | Full path to log file  | Yes
| format     | Datetime format        | No
| group_name | CloudWatch Log Group   | Yes


Dependencies
------------

This role has no dependencies, but the agent does need valid AWS IAM credentials.
Refer to the AWS documentation for more information.

Example Playbook
----------------

    - hosts: servers
      vars:
        cloudwatch_logs:
          - file: /var/log/auth.log
            format: "%b %d %H:%M:%S"
            group_name: "auth"
          - file: /home/ubuntu/.bash_history
            group_name: "bash_history"
      roles:
         - { role: cloudwatch_logs }

License
-------

GPLv3

Author Information
------------------

Created by David Harris
