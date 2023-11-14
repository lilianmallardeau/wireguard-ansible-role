WireGuard Ansible Role
=========================

An Ansible role to install WireGuard and configure an interface. Works on Debian-based distributions.

Requirements
------------

None

Role Variables
--------------

```yaml
# Private key. If empty (default), a new private key will be generated and saved on the server.
# It will be reused next time for the same interface if the file exists.
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
    psk: <preshared_key>  # Optional
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
        wireguard_interface_name: wg0
        wireguard_ip_address: 10.0.0.1/24
        wireguard_listen_port: 51820
        wireguard_peers:
          - public_key: fK9L5i9Y/atI2qs7JGjMK2Ab6nccl/rrx+sUA11Zrgo=
            allowed_ips: 10.0.0.2/32
            endpoint: example.com:51820
          - public_key: VT9WaisSQbwELinfBcIlGbFWtahePZyT92TgsIXX52M=
            allowed_ips: 10.0.0.3/32
```

License
-------

MIT
