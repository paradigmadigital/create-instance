# create-instance

Launch a new instance from an AMI image


## Role Variables

Settable variables that are in defaults/main.yml.

* `name`                      : name of the created instance
* `instance.base_ami_id`      : ami ID to use for the instance [Default: None]
* `instance.user`             : user of the EC2 instance
* `instance.region`           : the AWS region to use.  Must be specified if ec2_url is not used. If not specified then the value of the EC2_REGION environment variable, if any, is used. See http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region [Default: None]
* `instance.zone`             : AWS availability zone in which to launch the instance [Default: None]
* `instance.keypair`          : AWS ssh keypair
* `instance.security_groups`  : security group id (or list of ids) to use with the instance [Default: None]
* `instance.type`             : instance type to use for the instance, see http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html [Default: None]
* `instance.vpc_subnet_id`    : the subnet ID in which to launch the instance (VPC) [Default: None]
* `instance.tags`             : a hash/dictionary of tags to add to the new instance or for starting/stopping instance by tag; '{"key": "value"}' and '{"key": "value","key": "value"}' [Default : None]
* `instance.assign_public_ip` : when provisioning within vpc, assign a public IP address. Boto library must be 2.13.0+ (Choices: yes, no)[Default: None]
* `instance.wait`             : wait for the instance to be 'running' before returning.  Does not wait for SSH, see 'wait_for' example for details.  (Choices: yes, no)[Default: no]
* `instance.volumes`          : a list of hash/dictionaries of volumes to add to the new instance; '[{"key": "value", "key": "value"}]'; keys allowed are - device_name (str; required), delete_on_termination (bool; False), device_type (deprecated), ephemeral (str), encrypted (bool; False), snapshot (str), volume_type (str), iops (int) - device_type is deprecated use volume_type, iops must be set when volume_type='io1', ephemeral and snapshot are mutually exclusive.  [Default: None]

## Example Playbook

It assumes you use the ec2 dynamic inventory

```yaml
- hosts        : localhost
  connection   : local
  gather_facts : no
  roles:
    - role: create-instance
```

## License

GPLv2

## Author

jamatute@paradigmadigital.com
