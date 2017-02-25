openwrt-dhcp
============

configure DHCP aspects of your openwrt system.
compare: [http://wiki.openwrt.org/doc/uci/dhcp]

Dependencies
------------

* [openwrt-uci](https://github.com/flandiGT/openwrt-uci)

Role Variables

--------------

| variable name     | type             | element structure    | default |
|-------------------|------------------|----------------------|---------|
| dhcp_configs      | array of objects | see attributes below | []      |
| dhcp_hosts        | array of objects | see attributes below | []      |

Role Variable elements
----------------------

dhcp_configs attributes:

| attribute name | property type       | valid values / examples                      |
|----------------|---------------------|----------------------------------------------|
| index          | number              | optional: the index of the dhcp-host setting |
| interface      | text                | interface name this dhcp-config belongs to   |
| leasetime      | interval as text    | 1h/12h...                                    |
| limit          | number              | number of maximum leases, e.g. 150           |
| start          | number              | starting IP address                          |

dhcp_hosts attributes:

| attribute name | property type       | valid values / examples                            |
|----------------|---------------------|----------------------------------------------------|
| name           | text                | name of the host                                   |
| mac            | mac address as text | mac address of the host (like '01:23:45:67:89:01') |
| ip             | ip address as text  | IP address of the host (like '192.168.1.2')        |

Example Playbook
----------------

```
 - role: openwrt-dhcp
   dhcp_configs:
   - interface: lan
     leasetime: 24h
     limit: 150
     start: 100
   - interface: guest
     leasetime: 12h
     limit: 150
     start: 100 
   dhcp_hosts:
   - name: 'windows-pc'
     mac: '01:23:45:67:89:01'
     ip: '192.168.1.2'
   - name: 'android-phone'
     mac: '98:76:54:32:10:98'
     ip: '192.168.1.3'
```

Official documentation
* [OpenWRT Wiki / DNS and DHCP configuration](http://wiki.openwrt.org/doc/uci/dhcp)
