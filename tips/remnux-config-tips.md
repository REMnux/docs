# REMnux Configuration Tips

## Changing the Keyboard Layout <a id="keyboard-layout-change"></a>

To change the keyboard layout of your REMnux system, perhaps to another language, take the following steps:

1. Open the Settings window using the command `gnome-control-center`.
2. Go to the Region & Language area.
3. Press the + button in the Input Sources area.
4. Select the desired language and click the Add button.
5. Close the Settings window.

Sometimes you might need to reboot for the setting to take into effect. 

You can switch between the keyboard layouts by clicking the language icon in the top right corner of your desktop. If you need additional guidance, please [see this article](https://websiteforstudents.com/configure-ubuntu-18-04-lts-beta-keyboard-layout-for-native-languages/).

## Localhost Listener on TCP and UDP Ports 53 <a id="port-53-listener"></a>

Ubuntu uses a daemon named "systemd-resolved" for resolving DNS queries that you initiate from the system. This daemon listens on the localhost interface on TCP and UDP ports 53. If you're running a tool that attempts to listen on these ports on localhost, your tool might not function properly.

To get around this, reconfigure the tool so it listens on the Ethernet network interface of your REMnux system and not on the localhost network interface.

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

If you set up a REMnux system in a cloud environment, such as AWS, you can not only interact with it using the text-based SSH interface, but also using the graphical Gnome interface that comes with REMnux.

You'll need to activate the SSH daemon on your REMnux system; one way to do this is to run the `sshd start` command. Before doing this, be sure to harden the configuration of your cloud-based REMnux system and set up SSH authentication according to your requirements and risk tolerance.

### X11 Forwarding

One way to remotely interact with REMnux using a graphical interface is to use X11 forwarding through SSH. If you [installed REMnux in "addon" mode](../install-distro/add-to-existing-system.md), you'll need to configure your SSH daemon to support X11 forwarding; in other cases, SSH on REMnux is already set up appropriately.

Next:

1. Configure the SSH client on your local system to enable X11 forwarding.
2. Connect to your remote REMnux system using SSH, assuming the SSH daemon on REMnux is configured and active.
3. Activate X server software on your local system, unless you're running Linux. If you're using Linux as your local system, it will natively support receiving X11 connections. If you're using Windows or macOS, you'll need to install X server software. [Xming](http://www.straightrunning.com/XmingNotes/) and [VcXsrv](https://sourceforge.net/projects/vcxsrv/) for Windows and [XQuartz](https://www.xquartz.org) for macOS are reasonable free options.

For an example of performing some of these steps, consider an AWS blog post on [setting up X11 forwarding](https://aws.amazon.com/de/blogs/compute/how-to-enable-x11-forwarding-from-red-hat-enterprise-linux-rhel-amazon-linux-suse-linux-ubuntu-server-to-support-gui-based-installations-from-amazon-ec2/).

### VNC Access

Another way to remotely interact with the REMnux graphical environment is to use a VNC tol such as [TigerVNC](https://tigervnc.org), which you can tunnel over SSH and set up like this:

1. Install TigerVNC viewer on the local system from which you're planning to access the remote REMnux system.
2. Connect to your remote REMnux system using SSH, assuming the SSH daemon on REMnux is active.
3. Install TigerVNC server on your remote REMnux system: `sudo apt install -y tigervnc-standalone-server`
4. Set up your VNC password using the [vncpasswd](https://tigervnc.org/doc/vncpasswd.html) command.
5. On your local system create an SSH tunnel from port 5901 to port 5901 using a command such as `ssh -L 5901:localhost:5901`
6. Launch a TigerVNC server on your remote REMnux system: `vncserver :1`
7. Start a VNC client on your local system, directing it to connect to `localhost:1`

## Transferring Files In and Out of REMnux <a id="transferring-files"></a>

There are several ways of transferring files, such as malware samples, in and out of REMnux.

### Virtual Machine Tools <a id="vm-tools"></a>

If you're running REMnux as a local VM, one way to transfer files in and out of the VM is to use the copy-and-paste or file transfer capabilities of your hypervisor. If using copy-and-paste, you can place files in and out of the VM by copying them to or from [Nautilus](../discover-the-tools/general+utilities.md#nautilus), which is the GUI file browsing tool on REMnux.

If REMnux is running in VirtualBox, you can go to the Devices menu of VirtualBox for your REMnux VM and select `Shared Folders`, `Shared Clipboard` , and `Drag and Drop`. To enable this functionality, you need to have Guest Additions installed in the REMnux virtual machine, which is preinstalled as part of the VirtualBox version of the REMnux virtual appliance. The appliance ships with `Shared Clipboard` and `Drag and Drop` enabled.

In VMware, similar functionality is supported by the open-vm-tools package, which is prenistalled in the general version of the REMnux virtual appliance and if you installed the distro from scratch using the REMnux installer. You can modify settings of your REMnux virtual machine to disable `Drag and Drop` and `Copy and Paste`, if you wish; they're enabled by default. You can also enable `Shared Folders`, which are disabled by default.

{% hint style="danger" %}
Enabling hypervisor-based file and clipboard sharing capabilities someone increases the risk that if you run malicious code in your REMnux virtual machine, the malware will adversely affect your underlying code. Many analysts consider this an acceptable risk.
{% endhint %}

### SFTP

Another way to get files in and out of REMnux is to use the SFTP protocol, which is supported by [OpenSSH](../discover-the-tools/general+utilities.md#openssh). Unless you installed REMnux in `cloud` mode or are running [REMnux as a Docker container](../install-distro/remnux-as-a-container.md), OpenSSH is disabled by default. You can activate OpenSSH in your VM using the `sshd start` command. You can then use an SFTP client to connect to or from REMnux; the SFTP client built into REMnux is the command-line tool `sftp`.

### Removable Media

Yet another method to transfer files in and out of REMnux is to use removable media, such as a USB drive. If running REMnux as a VM, you'd need to use your hypervisor to map the USB drive into the virtual machine.

### Mapping Files into the Container <a id="mapping-files"></a>

If you are running [REMnux as a Docker container](../install-distro/remnux-as-a-container.md), you can invoke the container by mapping a directory on your local system into the container to create a shared location for your files. You can use [Docker's `-v` or `--mount` parameters](https://docs.docker.com/storage/volumes/) when launching the container to achieve this.

## Switching REMnux Installation Mode After the Install <a id="switch-mode"></a>

If you installed REMnux using one installation mode, for example `addon`, you can switch to another installation mode, for example `dedicated`, by taking the following steps:

1. Edit the /etc/remnux-config and change the mode from `addon` to `dedicated`.
2. Run the command `remnux update`.
3. Reboot.

## Fixing a VMware Issue by Switching from Wayland to Xorg <a id="vmware-wayland-x11"></a>

There have been sporadic reports of VMware conflicting with the Ubuntu graphical environment, which by default uses [Wayland](https://wiki.ubuntu.com/Wayland) display protocol. The problems manifest themselves through the VM being unresponsive to keyboard and mouse; clipboard sharing and copy-and-paste VMware features might not be working, too.

If you encounter this issue, try configring your REMnux virtual machine to switch from Wayland to Xorg. The change should be unnoticeable to your user experience, but it might address the VMware issue. To make the switch, switch to the root user account \(`sudo -s`\) and edit the file /etc/gdm3/custom.conf. Uncomment this line:

```text
#WaylandEnable=false
```

So it says:

```text
WaylandEnable=false
```

Then reboot your virtual machine \(`reboot`\).

