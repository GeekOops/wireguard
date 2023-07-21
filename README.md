# pdostal.wireguard

This role tends to be simple.

## How to

Create `main.yml`

```yaml
- name: Wireguard for automated hosts
  hosts: automated
  become: true
  roles:
  - pdostal.wireguard
```

Create `hosts.yml`

```yaml
all:
  vars:
    network: vpn
    port: 51871

automated:
  hosts:
    pdostal:
      address: 172.27.172.1/24, 10.0.0.1/24
      public_key: EXAMPLEKEY123EXAMPLEKEY123=
      endpoint: 111.222.111.222:51871
      allowed_ips: 172.27.172.0/24, 10.0.0.0/24
      private_key: !vault |

manual:
  hosts:
    laptop:
      public_key: EXAMPLEKEY123EXAMPLEKEY123=
      allowed_ips: 172.27.172.2/32, 10.0.0.2/32
    phone:
      public_key: EXAMPLEKEY123EXAMPLEKEY123=
      allowed_ips: 172.27.172.3/32, 10.0.0.3/32
```

This is my first public role, let me know how do you like it!

