# REMnux Distro Tips

## Localhost Listener on TCP and UDP Ports 53 <a id="localhost-port-53-listener"></a>

Ubuntu a daemon named "systemd-resolved" for resolving DNS queries that you initiate from the system. This daemon listens on the localhost interface on TCP and UDP ports 53. If you're running a tool that attempts to listen on these ports on localhost, your tool might not function properly.

To get around this, reconfigure the tool so it listens on the Ethernet network interface of your REMnux system and not on the localhost network interface. For example, to do this for FakeNet-NG, edit its configuration file /usr/lib/python2.7/dist-packages/fakenet/configs/default.ini so that the `LinuxRestrictInterface` parameter is set to your Ethernet network interface name, such as `ens33`.

Alternatively, you can disable the systemd-resolved daemon until the next reboot like this:

```text
sudo systemctl stop systemd-resolved
```

If you wish to disable systemd-resolved permanently issue the following command. However, note that if you disable this daemon, you will be unable to resolve DNS queries from your REMnux system unless you reconfigure the system's DNS resolver settings.

```text
sudo systemctl disable systemd-resolved
```

