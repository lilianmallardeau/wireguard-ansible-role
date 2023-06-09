WireGuard Ansible Role
=========================

An Ansible role to install WireGuard and configure an interface. Works on Debian-based distributions.

Requirements
------------

None

Role Variables
--------------

```yaml
# Private key 
wireguard_private_key: <private_key>

# Interface name
wireguard_interface_name: wg0

# IP address
wireguard_ip_address: 10.0.0.1/24

# Listen port
wireguard_listen_port: 51820

# Peers, empty by default
wireguard_peers:
  - public_key: <peer public key>
    allowed_ips: <peer allowed ip addresses>
    endpoint: <ip_addr:port>  # Optional, domain names can also used
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: wireguard
      vars:
        wireguard_private_key: kDK3ciMkq+WE1GiIGPRw6ryMUdsb6zGrAmi/8h6KIm0=
        wireguard_interface_name: wg0
        wireguard_ip_address: 10.0.0.1/24
        wireguard_listen_port: 51820
        wireguard_peers:
          - public_key: fK9L5i9Y/atI2qs7JGjMK2Ab6nccl/rrx+sUA11Zrgo=
            allowed_ips: 10.0.0.2/24
            endpoint: example.com:51820
          - public_key: VT9WaisSQbwELinfBcIlGbFWtahePZyT92TgsIXX52M=
            allowed_ips: 10.0.0.3/24
```

License
-------

MIT
