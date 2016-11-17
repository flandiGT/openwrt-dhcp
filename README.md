openwrt-dhcp
================

configure firewall aspects of your openwrt system.
compare: [http://wiki.openwrt.org/doc/uci/dhcp]

Role Variables
--------------

| variable name     | type             | element structure    | default |
|-------------------|------------------|----------------------|---------|
| dhcp_configs      | array of objects | see attributes below | <empty> |

Role Variable elements
----------------------

dhcp_configs attributes:

| attribute name | property type       | valid values / examples                                                      |
|----------------|---------------------|------------------------------------|
| interface      | text                | interface name this dhcp-config belongs to  |
| leasetime      | interval as text    | 1h/12h...                 |
| limit          | number              | number of maximum leases, e.g. 150                 |
| start          | number              | starting IP address                |

Dependencies
------------

* openwrt-uci

Example Playbook
----------------

```
    - role: openwrt-dhcp
      dhcp_configs: [{
        interface: guest,
        leasetime: 12h,
        limit: 150,
        start: 100
      }]
```

[http://wiki.openwrt.org/doc/uci/dhcp]: http://wiki.openwrt.org/doc/uci/dhcp
