# Ansible Role: Cobalt Strike Teamserver ([Ludus](https://ludus.cloud))

An Ansible role that installs and spins up a Cobalt Strike Teamserver on a Debian or Ubuntu server.

> [!WARNING]
> Currently support for Windows has not been implemented but with enough demand I am happy to further this

## Requirements
- You need to supply a valid Cobalt Strike license for this to be successful.
- Add the Ludus Ansible Galaxy Role.
  ```ludus ansible role add 0xRedpoll.ludus_cobaltstrike_teamserver```

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # Utilise this variable to set a password for your teamserver, defaults to 0xRedpoll
    ludus_cobaltstrike_teamserver_password: "0xRedpoll"

    # If you want to use a custom C2 profile, add it to the files directory and set the variable to the filename (no path)
    ludus_cobaltstrike_c2_profile: ""

    # Add your Cobalt Strike license into this variable
    ludus_cobaltstrike_license: "0000-0000-0000-0000"

## Dependencies

None.

## Example Playbook

```yaml
- hosts: cobaltstrike_teamserver_host
  roles:
    - 0xRedpoll.ludus_cobaltstrike_teamserver
  vars:
    ludus_cobaltstrike_teamserver_password: "0xRedpoll"
    ludus_cobaltstrike_c2_profile: ""
    ludus_cobaltstrike_license: "0000-0000-0000-0000"
```

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-cobaltstrike-teamserver"
    hostname: "{{ range_id }}-cobaltstrike"
    template: debian-12-x64-server-template
    vlan: 20
    ip_last_octet: 2
    ram_gb: 4
    cpus: 4
    linux: true
    testing:
      snapshot: false
      block_internet: false
    roles:
      - 0xRedpoll.ludus_cobaltstrike_teamserver
    role_vars:
      ludus_cobaltstrike_teamserver_password: "0xRedpoll"
      ludus_cobaltstrike_license: "0000-0000-0000-0000"
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [0xRedpoll](https://github.com/0xRedpoll), for [Ludus](https://ludus.cloud/).
