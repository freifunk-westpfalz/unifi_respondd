# unifi_respondd

This queries the API of a UniFi controller to get the current status of the Accesspoints and sends the information via the respondd protocol. Thus it can be picked up by `yanic` and other respondd queriers.

## Overview

![](docs/architecture.png)


## Config File:
```yaml
controller_url: unifi.lan
controller_port: 8443
username: ubnt
password: ubnt
ssid_regex: .*freifunk.*
offloader_mac:
    SiteName: 00:00:00:00:00:00
    SiteName2: 00:00:00:00:00:00
site_prefix: 
    SiteName: ffwp-Node-Prefix-
    SiteName2: ffwp2-Node-Prefix-
nodelist: https://MAPURL/data/meshviewer.json
version: v5
ssl_verify: True
multicast_enabled: false
multicast_address: ff05::2:1001
multicast_port: 1001
unicast_address: fe80::68ff:94ff:fe00:1504
unicast_port: 10001
interface: eth0
verbose: true
logging_config:
    formatters:
      standard:
        format: '%(asctime)s,%(msecs)d %(levelname)-8s [%(filename)s:%(lineno)d] %(message)s'
    handlers:
      console:
        class: logging.StreamHandler
        formatter: standard
    root:
      handlers:
      - console
      level: DEBUG
    version: 1
```

## Requirements
For multicast to work, `unifi_respondd` has to be run on a computer in the Freifunk Network. Otherwise, Yanic will not be able to get the information created by this project.

The host on which `unifi_respondd` is running has to have at least Python 3.6 installed. python3-pip is also recommended.  

## Installation
To install `unifi_respondd` you have to clone this repository and run `pip install .`.

## Usage
First, copy `unifi_respondd.yaml.example` to `unifi_respondd.yaml` with e.g. `cp unifi_respondd.yaml.example unifi_respondd.yaml`.

Then edit `unifi_respondd.yaml` as needed and run `respondd.py`  
