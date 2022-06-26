# Wireguard Random VPN Selector for Linux

A tool that utilizes the Wireguard CLI (`wg` and `wg-quick`) to establish a
Wireguard VPN connection using Wireguard by randomly selecting a configuration
file stored in `etc/wireguard`

## Requirements

- Wireguard
  - Installation for most common Linux based systems:
    https://www.wireguard.com/install/
  - Fedora Silverblue: `rpm-ostree install wireguard-tools`
- Wireguard configuration file(s) stored in `etc/wireguard`
  - Many VPN providers (Mullvad and ProtonVPN for example) have the option to
    provide Wireguard configuration files. For examples of how they look like:
    https://www.wireguardconfig.com/

The `wg-random` script must run as `sudo`, as root priviligares are required to
run the Wireguard CLI commands.

## Usage

The following commands must be run with `sudo`

```bash
# To start the vpn:
wg-random up
# To stop the vpn:
wg-random down
```

## TODO
- Document how to make this command run on startup
- Option to block non VPN communication with `iptables`
