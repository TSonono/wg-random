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

## Auto-start on boot
There different ways of doing this. The approach presented here will be using
`systemd`, but one could for instance use `crontab` for this as well.

### Steps

1. Verify `systemd` is installed on your system by running `systemctl --version`
1. Copy the `wg-random` script to `/usr/local/bin`
2. Copy the `wg-random.service` file in this repository to
   `/etc/systemd/system`.
3. Run `systemctl daemon-reload`
4. Run `systemctl enable wg-random.service`

The service should not be started/stopped to control the status of the VPN. This
is merely a way to have the VPN auto-start on boot. To start/stop the VPN after
the device has been booted, the `wg-random` script should be used directly.

## TODO
- Option to block non VPN communication with `iptables`
