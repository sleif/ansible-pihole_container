# sleif.pihole_container

This role runs a Pihole instance in a container.

## Requirements

- Podman installed on the target host.
- ansible role sleif.podman

## Role Variables

- container_storage_dir_base_local: '/srv'
- pihole_password
- pihole_external_web_port

### settings about local dns domain

- pihole_rev_server: False
- pihole_rev_server_target: 192.168.178.1
- pihole_rev_server_domain: fritz.box
- pihole_rev_server_cidr: "192.168.178.0/24"
- pihole_whitelist_entries: []

## Example Playbook

```yml
- hosts: "server"
  user: root
  tasks:
    - name: include_role sleif.pihole_container
      ansible.builtin.include_role:
        name: sleif.pihole_container
        apply:
          tags: "pihole_container"
      vars:
        podman_network_name: "slirp4netns:port_handler=slirp4netns"
      tags: "pihole_container"
```

## License

MIT

## Author Information

Created in 2021 by Sebastian Berthold
