ansible-role-cloud-dns
======================

[![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)
![](https://github.com/mtulio/ansible-role-cloud-dns/actions/workflows/release.yml/badge.svg)
![](https://github.com/mtulio/ansible-role-cloud-dns/actions/workflows/ci.yml/badge.svg?branch=main)
![](https://img.shields.io/ansible/role/59600)

Ansible Role to manage CLoud Domains.

Providers
---------

- Supported providers

| Provider | Offering |
| -- | -- |
| AWS | Route53 |
| DigitalOcean | Domains |


Requirements
------------

- Ansible Collection `amazon.aws`
```
ansible-galaxy collection install amazon.aws
```

- Ansible Collection `community.aws`
```
ansible-galaxy collection install community.aws
```

- Ansible [Collection](https://docs.ansible.com/ansible/latest/collections/community/digitalocean/index.html) `community.digitalocean`

```
ansible-galaxy collection install community.digitalocean
```

Role Variables
--------------

- `cloud_dns_zones`: list of DNS domains (zones) to be created on cloud provider.

<!--

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

-->

Example Playbook
----------------

- Create Route53 domain (AWS):

```yaml
- hosts: localhost
  roles:
  - role: mtulio.cloud_load_balancer
    cloud_dns_zones:
      - domain: "example.com"
        provider: aws
      - domain: "private.example.com"
        provider: aws
        vpc_name: "my-vpc"
        vpc_region: us-east-1
        private_zone: yes
```

- Create Domain on DigitalOcean:

```yaml
- hosts: localhost
  roles:
  - role: mtulio.cloud_load_balancer
    cloud_dns_zones:
      - domain: "example.com"
        provider: do
        vpc_region: "nyc3"
        project: "my-project"
```


License
-------

Apache-2.0

Author Information
------------------

[Marco Braga (@mtulio)](https://github.com/mtulio)
