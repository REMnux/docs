# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the prebuilt REMnux virtual appliance, import it into your hypervisor, then [run the update command](keep-the-distro-up-to-date.md) to make sure it's up-to-date.

{% hint style="info" %}
REMnux is currently based on an x86/amd64 version of Ubuntu, and won't run on ARM processors such as Apple's M-series chips.
{% endhint %}

## Step 1: Download the Virtual Appliance File <a href="#download-virtual-appliance" id="download-virtual-appliance"></a>

The REMnux virtual appliance is approximately 9 GB. It's based on Ubuntu 24.04 (Noble), and is available in several formats.

Decide which virtual appliance file to download. If in doubt, get the General OVA file. If you're using VirtualBox or Proxmox, download the appropriate file instead.

{% tabs %}
{% tab title="General OVA" %}
This general OVA file works with most hypervisors. If you're using VirtualBox or Proxmox, go to another corresponding tab.

[Download the general OVA file.](https://download.remnux.org/202602/remnux-noble-amd64.ova)
{% endtab %}

{% tab title="VirtualBox OVA" %}
This VirtualBox OVA file is specifically for VirtualBox. If you're using another hypervisor, go to another corresponding tab.

[Download the VirtualBox OVA file.](https://download.remnux.org/202601/remnux-noble-amd64-virtualbox.ova)
{% endtab %}

{% tab title="Proxmox QCOW2" %}
This QCOW2 file is specifically for Proxmox. If you're using another hypervisor, go to another corresponding tab.

[Download the Proxmox QCOW2 file.](https://download.remnux.org/202601/remnux-noble-amd64-proxmox.qcow2)
{% endtab %}
{% endtabs %}

## Step 2: Confirm the Hash of the Downloaded File <a href="#confirm-hash" id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

{% tabs %}
{% tab title="General OVA Hash" %}
The general OVA file:

```
1b10f522671d42b5fac60238d660871001ecdd94474aace55e0ef2b88e2bdecb
```
{% endtab %}

{% tab title="VirtualBox OVA Hash" %}
The VirtualBox OVA file:

```
7cc8b55a8db32a1a9d42839fe3454922a6eb45010419428f3ce5fece4193e184
```
{% endtab %}

{% tab title="Proxmox QCOW2 Hash" %}
The Proxmox QCOW2 file:

```
95adcfd293b29aee77c0c95b2d0a9a7f8f2f7829c49f20b3def16b5b28638e93
```
{% endtab %}
{% endtabs %}

## Step 3: Import the Virtual Appliance <a href="#import-ova-file" id="import-ova-file"></a>

When importing the REMnux virtual appliance, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run. As a point of reference, most people find 4 GB RAM and 100 GB disk sufficient.

## Step 4: Start the REMnux Virtual Machine <a href="#start-remnux-vm" id="start-remnux-vm"></a>

Once you start your REMnux virtual machine, it will automatically log you into the REMnux environment.

There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted. When you need to elevate your privileges or access the REMnux virtual appliance remotely, note the following default credentials:

{% hint style="success" %}
Username: `remnux`\
Password: `malware`
{% endhint %}

If necessary, [change the keyboard layout](../tips/remnux-config-tips.md#keyboard-layout-change) of your system to match your locale and setup.

## Step 5: Consider Special Hypervisor Requirements <a href="#hypervisor-requirements" id="hypervisor-requirements"></a>

Depending on which hypervisor or environment you're using, you might need to take the following steps:

### VirtualBox

If your REMnux window is too small when you boot the system in VirtualBox, activate the Scaling Mode for the VM via the VirtualBox menu View > Scaling Mode.

If your REMnux virtual machine is unable to communicate over the network, check whether it has a network interface other than the loopback ("lo") by running the `ifconfig` command. If a non-loopback interface is missing, perform the following steps to add it:

1. Run the `networkctl` command to determine the name of the adapter ("link") of type "ether". It might be named something like "enp0s17".
2. Set up the network interface by replacing _YOUR\_NIC_ in the following command with the name you've identified in the previous step (e.g., "enp0s17"): `sudo ip link set up YOUR_NIC`
3. Edit the /etc/netplan/01-netcfg.yaml file (e.g., use the `code` command). Under "ethernets:" replace the name there (e.g, "ens33") with the name of your network card (e.g., "enp0s17").
4. Reboot your REMnux virtual machine.

If you're building your own VirtualBox VM (not using the pre-built VirtualBox OVA), install VirtualBox Guest Additions from the ISO for full functionality:

1. Devices → Insert Guest Additions CD image
2. Navigate to the mounted CD under `/media/remnux/` and run `sudo ./VBoxLinuxAdditions.run`
3. Reboot

Note: The Ubuntu `virtualbox-guest-*` packages do not provide auto-resize and clipboard support. Use the ISO-based Guest Additions instead.

### VMware

If you experience an unresponsive keyboard, mouse, or broken clipboard/copy-paste when running REMnux in VMware, the issue is likely caused by VMware configuring the desktop to use Wayland instead of Xorg. To fix this:

1. Edit the GDM configuration file: `sudo nano /etc/gdm3/custom.conf`
2. Find the line `#WaylandEnable=false` and uncomment it by removing the `#`, so it reads `WaylandEnable=false`.
3. Reboot your REMnux virtual machine.

### Hyper-V

It's possible to import the pre-built REMnux virtual appliance into Hyper-V, but you'll need to take a few conversion steps. You'll need to extract the contents of the REMnux OVA file to obtain the enclosed VMDK file that captures the virtual disk of the distro, then convert it to the VHD format supported by Hyper-V:

1. Download the General OVA of the REMnux distro, as [outlined above](get-virtual-appliance.md#download-virtual-appliance).
2. Extract the downloaded OVA file using a tool such as "tar". One of the extracted files will have the .vmdk.gz name, such as remnux-noble-disk1.vmdk.gz.
3. Decompress the extracted .vmdk.gz file using a tool such as "gunzip" to generate a file with the .vmdk extension.
4. Use [qemu-img](https://qemu.readthedocs.io/en/latest/tools/qemu-img.html) (`qemu-img convert -O vhdx -o subformat=dynamic`) or [StarWind V2V Converter](https://www.starwindsoftware.com/starwind-v2v-converter) to convert the .vmdk file to the VHD format supported by Hyper-V.
5. Import the generated VHD file into Hyper-V.

For an overview of this process, see the video [How To Install REMnux on Windows 10 Hyper-V](https://www.youtube.com/watch?v=d8uyVi0nH-U) by Cyrus.

### Remote Cloud, Such as AWS

The REMnux virtual appliance ships in "dedicated" installation mode, which automatically turns off the SSH daemon. This configuration is generally desirable when running REMnux in a local lab. If you're deploying the virtual appliance in a cloud environment, you might need to keep SSH enabled to remotely access your REMnux system. In that case:

1. Edit the /etc/remnux-config and change the mode from `dedicated` to `cloud`.
2. Enable the SSH daemon by running: `sudo systemctl enable ssh`.
3. Change the default user's password and otherwise strengthen the SSH authentication method according to your requirements and risk tolerance.
4. Reboot your REMnux system.

### KVM/QEMU

If you converted the REMnux virtual appliance to KVM/QEMU, use Standard VGA display for the first boot. After booting, run `remnux install` to automatically install spice-vdagent (display resize, copy/paste) and other KVM guest tools. You can then switch to SPICE for better graphics.

### Proxmox

REMnux provides a prebuilt QCOW2 virtual appliance optimized for Proxmox Virtual Environment. Download it from the [Proxmox QCOW2 link above](get-virtual-appliance.md#download-virtual-appliance).

To import the QCOW2 file:

1. Upload the QCOW2 file to your Proxmox storage (e.g., via SCP to `/var/lib/vz/images/`).
2. Create a new VM with your preferred settings (recommended: 4 GB RAM, VirtIO SCSI, SPICE display).
3. Import the disk: `qm importdisk <vmid> /path/to/remnux-noble-amd64-proxmox.qcow2 local-lvm`
4. Attach the imported disk: VM > Hardware > double-click "Unused Disk" > Add.
5. Set boot order: VM > Options > Boot Order > enable the disk.

The QCOW2 image is pre-configured with:

* SPICE display support
* qemu-guest-agent
* spice-vdagent (clipboard, display resize)
* nomodeset kernel parameter

Alternative: You can also [import the general OVA](https://syncbricks.com/how-to-import-ova-to-proxmox/) using CPU type `qemu64`. For the first boot, set the display to Standard VGA (not SPICE). After booting, run `remnux install` to install guest tools and apply display fixes. You can then switch to SPICE for better graphics.

## Step 6: Upgrade the REMnux Virtual Machine <a href="#upgrade-remnux" id="upgrade-remnux"></a>

After installing the REMnux virtual machine, run the following command inside the VM as a regular, non-root user to upgrade it to the latest version of the distro:

```
remnux install
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 7: Take a Snapshot of the Virtual Machine <a href="#take-snapshot" id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual machine, so you can return it to a known good state if the need arises.
