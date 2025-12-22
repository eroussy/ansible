# Deploy rt-tests Role

This role deploys the rt-tests utility.

## Requirements

No requirement.

## Role Variables

| Variable                       | Required | Default | Type   | Comments                      |
|--------------------------------|----------|---------|--------|-------------------------------|
| deploy_rttests_rttests_version | no       | 1.10    | String | Version of rt-tests to deploy |

## Example Playbook

```yaml
- name: deploy rt-tests
  hosts:
    - cluster_machines
    - standalone_machine
    - VMs
  become: true
  roles:
    - { role: seapath_ansible.deploy_rttests }
```
