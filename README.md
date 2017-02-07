Role Name
=========

Launch new instance AMI image

Requirements
------------

The role uses the EC2 module

Role Variables
--------------

Settable variables that are in defaults/main.yml.

* `instance_name`   : name of the created instance
* `old_ami_name`    : Base AMI to create the instance
* `old_ami_owner`   : Base AMI owner
* `region`          : Region to launch the ec2 instance to create the new AMI
* `default_ami_id`  : In case you don't want to use the AMI used in the ASG, set this variable
* `instance_user`   : User of the EC2 instance 
* `zone`            : AWS zone
* `instance_user`   : User to log in
* `keypair`         : SSH keypair to access
* `security_groups` : AWS security group
* `instance_type`   : AWS instance type
* `volumes`         : AWS volumes
  * `device_name`   : Device path
  * `device_type`   : Device type
  * `volume_size`   : Volume size
  * `delete_on_termination`: True/False

Example Playbook
----------------

It assumes you use the ec2 dynamic inventory

```yaml
- hosts: localhost
  connection: local
  gather_facts: no
  roles:
    - role: launch-ami
```

License
-------

GPL
