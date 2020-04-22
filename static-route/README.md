# Description

This role add's static route(s) to the host(s).

## OS

Tested on:

- Centos 7
- Centos 8

## Variables

The statroute_list is a list of dictionairies and can be declaired as follows:

- destination KEY: the destination Network.
- gateway KEY: the gateway to use to route to the destination network.
- device KEY: the device to use to route to the destination network.

## Example usages

```yaml
statroute_list:
  - { destination: '10.241.0.0/24', gateway: '192.168.122.254', device: 'eth0' }
  - { destination: '10.242.0.0/24', gateway: '192.168.122.254', device: 'eth0' }
  - { destination: '10.243.0.0/24', gateway: '192.168.122.254', device: 'eth0' }
```

```yaml
statroute_list:
  - destination: '10.241.0.0/24'
    gateway: '10.242.0.1/24'
    device:  'eth0'
  - destination: '10.242.0.0/24'
    gateway: '10.242.0.1/24'
    device:  'eth0'
  - destination: '10.243.0.1/24'
    gateway: '10.243.0.1/24'
    device:  'eth0'
```
