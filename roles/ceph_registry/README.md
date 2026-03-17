# Ceph Registry Role

Configure a local container registry for Ceph container images.
This role sets up a registry container with optional TLS support and authentication.

## Requirements

No requirements.

## Role Variables

| Variable                      | Required | Type    | Default                          | Comments                                                                                                    |
|-------------------------------|----------|---------|----------------------------------|-------------------------------------------------------------------------------------------------------------|
| ceph_registry_path            | No       | string  | files/container_images/          | Base path for registry data and images.                                                                     |
| ceph_registry_data_path       | No       | string  | {{ ceph_registry_path }}/data    | Path for registry data storage.                                                                             |
| ceph_registry_images_path     | No       | string  | {{ ceph_registry_path }}/images  | Path for container images.                                                                                  |
| ceph_registry_port            | No       | integer | 443                              | Port on which the registry will listen.                                                                     |
| ceph_registry_container_name  | No       | string  | seapath-registry                 | Name of the registry container.                                                                             |
| ceph_registry_tls_enabled     | No       | boolean | `registry_tls_enabled` or true   | Enable TLS for the registry.                                                                                |
| ceph_registry_tls_cert        | No       | string  |                                  | Path to the TLS certificate file on the Ansible control node. If not set, a certificate will be created.    |
| ceph_registry_tls_key         | No       | string  |                                  | Path to the TLS key file on the Ansible control node. If not set, a certificate will be created.            |
| ceph_registry_tls_ca          | No       | string  |                                  | Path to the TLS CA certificate file on the Ansible control node. If not set, a certificate will be created. |
| ceph_registry_auth_enabled    | No       | boolean | `registry_auth_enabled` or false | Enable authentication for the registry.                                                                     |
| ceph_registry_username        | No       | string  | `registry_username`              | Username for registry authentication.                                                                       |
| ceph_registry_password        | No       | string  | `registry_password`              | Password for registry authentication.                                                                       |
| ceph_registry_ceph_version    | No       | string  | `ceph_version` or 20.2.0         | Ceph version for container images.                                                                          |
| ceph_registry_ceph_image      | No       | dict    | See defaults                     | Configuration for the Ceph container image (name, tag, source, tar_file).                                   |
| ceph_registry_registry_image  | No       | dict    | See defaults                     | Configuration for the Registry container image (name, tag, source, tar_file).                               |

## Example Playbook

```yaml
- hosts: cluster_machines
  vars:
    ceph_registry_port: 5000
    ceph_registry_tls_enabled: true
    ceph_registry_tls_cert: "/tmp/registry.crt"
    ceph_registry_tls_key: "/tmp/registry.key"
    ceph_registry_ceph_version: "18.2.0"
  roles:
    - { role: ceph_registry }
```
