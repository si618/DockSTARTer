# UniFi Network Application

[![Docker Pulls](https://img.shields.io/docker/pulls/linuxserver/unifi-network-application?style=flat-square&color=607D8B&label=docker%20pulls&logo=docker)](https://hub.docker.com/r/linuxserver/unifi-controller)
[![GitHub Stars](https://img.shields.io/github/stars/linuxserver/docker-unifi-network-application?style=flat-square&color=607D8B&label=github%20stars&logo=github)](https://github.com/linuxserver/docker-unifi-controller)
[![Compose Templates](https://img.shields.io/static/v1?style=flat-square&color=607D8B&label=compose&message=templates)](https://github.com/GhostWriters/DockSTARTer/tree/master/compose/.apps/unifinetapp)

## Description

[UniFi Network Application](https://www.ubnt.com/enterprise/#unifi) software is
a powerful, enterprise wireless software engine ideal for high-density client
deployments requiring low latency and high uptime performance.

## Install/Setup

This container requires a [mongodb instance](https://docs.linuxserver.io/images/docker-unifi-network-application/#setting-up-your-external-database) 
which is included in DockSTARTer but [requires configuration](https://github.com/jacobalberty/unifi-docker?tab=readme-ov-file#setting-up-running-stopping-upgrading).

The default volume mount follows the suggested `~/unifi` location, so if you
mount elsewhere update variable `UNIFINETAPP_VOLUME_STORAGE` to suit.

### Common Issue: Devices Get Stuck In "Adopting" State

To prevent your devices getting stuck on an "Adopting" loop, log in to your
controller and update how the controller sends the inform command. This can be
achieved by going to `Settings > Controller Settings`. On the right hand side,
you will see `Controller Hostname/IP`, change this to your Docker host's IP
address or hostname. Additionally, make sure to toggle (it is `off` by default)
the option that says `Override inform Host`. This will make it so the inform
command is `http://<xxx.xxx.xxx.xxx>:8080/inform` where `xxx.xxx.xxx.xxx` is
your Docker host's IP and not an internal docker address.

If you don't see this option or are having problems finding the settings then
look over near the top and click
`Can't find what you need? Switch to Classic Mode`. You will then need to go to
`Controller` near the bottom and on the right hand side look for
`Controller Hostname/IP` and follow the same steps mentioned above.
