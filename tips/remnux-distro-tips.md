# REMnux Distro Tips

## Localhost Listener on TCP and UDP Ports 53 <a id="port-53-listener"></a>

Ubuntu uses a daemon named "systemd-resolved" for resolving DNS queries that you initiate from the system. This daemon listens on the localhost interface on TCP and UDP ports 53. If you're running a tool that attempts to listen on these ports on localhost, your tool might not function properly.

To get around this, reconfigure the tool so it listens on the Ethernet network interface of your REMnux system and not on the localhost network interface. For example, to do this for [FakeNet-NG](../discover-the-tools/explore+network+interactions/services.md#fakenet-ng), edit its configuration file /usr/lib/python2.7/dist-packages/fakenet/configs/default.ini so that the `LinuxRestrictInterface` parameter is set to your Ethernet network interface name, such as `ens33`.

Alternatively, you can disable the systemd-resolved daemon until the next reboot like this:

```text
sudo systemctl stop systemd-resolved
```

If you wish to disable systemd-resolved permanently issue the following command. However, note that if you disable this daemon, you will be unable to resolve DNS queries from your REMnux system unless you reconfigure the system's DNS resolver settings. Also, some software, such as OpenVPN and other VPN clients, might not function properly if systemd-resolved is disabled.

```text
sudo systemctl disable systemd-resolved
```

## REMnux Behind a Non-Transparent Proxy <a id="behind-proxy"></a>

The [REMnux installer](../behind-the-scenes/technologies/remnux-installer.md) is presently not compatible with non-transparent network proxies. You can still set up and use REMnux behind such a proxy, though this will involve applying [Salt state files](../behind-the-scenes/technologies/saltstack-management.md) directly, instead of using the REMnux installer to set up and upgrade your REMnux system.

You can start with either a pristine compatible Linux system where you'll either [install REMnux](../install-distro/install-from-scratch.md) from scratch or [add REMnux](../install-distro/add-to-existing-system.md), or you can start with a prebuilt [REMnux virtual appliance](../install-distro/get-virtual-appliance.md). Configure that system to use your proxy like you'd configure any Ubuntu system. To do this, you'll usually need to:

* [Configure APT to use your proxy](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/) by defining the necessary details in /etc/apt/apt.conf.d.
* Define environment variables `https_proxy`, `http_proxy`, and `ftp_proxy` to specify your proxy.

If you're not starting with a prebuit REMnux virtual appliance, follow [instructions to manually install SaltStack](https://docs.remnux.org/behind-the-scenes/technologies/state-files-without-the-remnux-installer#manually-installing-saltstack) on the system you'll be using for REMnux. Next, modify /etc/salt/minion to include your proxy details:

```text
# Set http proxy information for the minion when doing requests
proxy_host:
proxy_port:
proxy_username:
proxy_password:
```

Next, to install REMnux or upgrade it later, follow instructions to:

1. [Retrieve the latest REMnux Salt state files.](https://docs.remnux.org/behind-the-scenes/technologies/state-files-without-the-remnux-installer#retrieving-remnux-state-files)
2. [Invoke SaltStack to install the state file grouping](https://docs.remnux.org/behind-the-scenes/technologies/state-files-without-the-remnux-installer#invoking-saltstack-to-install-state-file-groupings) appropriate for you \(e.g., `remnux.dedicated`\)

If you have the expertise, [consider suggesting a revision to REMnux installer](https://app.gitbook.com/@lennyzeltser/s/remnux/get-involved/enhancement-ideas#the-remnux-installer-should-work-with-non-transparent-proxies) that corrects its inability to connect through non-transparent proxies.

## GUI Interactions When REMnux Is in the Cloud <a id="gui-cloud-remnux"></a>

If you set up a REMnux system in a cloud environment, such as AWS, you can not only interact with it using the text-based SSH interface, but also using the graphical Gnome interface that comes with REMnux. One way to do this is to set up X11 forwarding through SSH.Another is to use [TigerVNC](https://tigervnc.org), which you can tunnel over SSH and set up like this:

1. Harden the configuration of your cloud-based REMnux system and set up SSH authentication according to your requirements and risk tolerance.
2. Install TigerVNC viewer on the local system from which you're planning to access the remote REMnux system.
3. Connect to your remote REMnux system using SSH.
4. Install TigerVNC server on your remote REMnux system: `sudo apt install -y tigervnc-standalone-server`
5. Set up your VNC password using the [vncpasswd](https://tigervnc.org/doc/vncpasswd.html) command.
6. On your local system create an SSH tunnel from port 5901 to port 5901 using a command such as `ssh -L 5901:localhost:5901`
7. Launch a TigerVNC server on your remote REMnux system: `vncserver :1`
8. Start a VNC client on your local system, directing it to connect to "localhost:1"



