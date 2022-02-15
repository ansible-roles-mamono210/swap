[![](https://github.com/ansible-roles-mamono210/molecule_test_ec2/workflows/build/badge.svg)](https://github.com/ansible-roles-mamono210/molecule_test_ec2/actions?query=workflow%3Abuild)
[![CircleCI](https://circleci.com/gh/ansible-roles-mamono210/molecule_test_ec2.svg?style=svg)](https://circleci.com/gh/ansible-roles-mamono210/molecule_test_ec2)

Role Description
=========

Create and destroy EC2 resources.

Requirements
------------

None

Role Variables
--------------

See details in 'meta/argument_specs.yml'.

```YAML
---
image:
instance_type: t2.micro
keypair_name:
security_group_name:
vpc_subnet_id:
tag_name:
tag_created_by:

ssh_user:
ssh_port: 22

security_group_description: 'Security group for testing Molecule'
security_group_rules:
  - proto: tcp
    from_port: "{{ ssh_port }}"
    to_port: "{{ ssh_port }}"
    cidr_ip: '0.0.0.0/0'
  - proto: icmp
    from_port: 8
    to_port: -1
    cidr_ip: '0.0.0.0/0'
security_group_rules_egress:
  - proto: -1
    from_port: 0
    to_port: 0
    cidr_ip: '0.0.0.0/0'
keypair_path: "{{ lookup('env', 'MOLECULE_EPHEMERAL_DIRECTORY') }}/ssh_key"
```

Dependencies
------------

None

Example Playbook
----------------

```YAML
---
- hosts: all
  become: true
  roles:
    - molecule_test_ec2
```

License
-------

BSD
