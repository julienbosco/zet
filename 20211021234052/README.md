# CLI Quicksheet for Netgear M5300
Instruction starting with a # mean *Privileged Mode* (`enable`).
## Changing management IP address

    > enable
    # configure
    # network mgmt_vlan <number>
    # serviceport ip {ipaddress mask [gateway|}
    # serviceport protocol {none | bootp | dhcp }

With this, the WebUI is accessible.

