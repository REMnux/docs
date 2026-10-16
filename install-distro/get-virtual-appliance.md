# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the prebuilt REMnux virtual appliance, import it into your hypervisor, then [run the update command](keep-the-distro-up-to-date.md) to make sure it's up-to-date. On AWS, you can [launch the REMnux AMI](run-remnux-on-aws.md) instead.

## Step 1: Download the Virtual Appliance File <a href="#download-virtual-appliance" id="download-virtual-appliance"></a>

The REMnux virtual appliance is approximately 8 GB. It's based on Ubuntu 24.04 (Noble), and is available in several formats.

Choose the file for your system's processor, then the one for your hypervisor. Apple M-series Macs need the arm64 files. On an Intel or AMD system with another hypervisor, try the VMware OVA file.

{% tabs %}
{% tab title="Intel or AMD (amd64)" %}
**VMware OVA** is for [VMware Workstation](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion) and for [VMware Fusion](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion) on Intel Macs. Other hypervisors that accept OVA files can import it too.

<a href="https://download.remnux.org/202610b/remnux-noble-amd64.ova" class="button secondary" data-icon="download">Download VMware OVA</a>

```
060acb0087c7ae6d138d7a994f5a1daf957fe3f9d0fdf72012b2c43e88876ef9
```

**VirtualBox OVA** is specifically for [VirtualBox](https://www.virtualbox.org/).

<a href="https://download.remnux.org/202610b/remnux-noble-amd64-virtualbox.ova" class="button secondary" data-icon="download">Download VirtualBox OVA</a>

```
a6b164fe044a12a6c21ae1d0c1f9ebffb708cefb24ebad0607434cdbf6841f73
```

**Proxmox QCOW2** is specifically for [Proxmox](https://www.proxmox.com/en/products/proxmox-virtual-environment/overview).

<a href="https://download.remnux.org/202610b/remnux-noble-amd64-proxmox.qcow2" class="button secondary" data-icon="download">Download Proxmox QCOW2</a>

```
9ef87306cd9b982de9109d08627040a15b2eb9d75040c9ceeffabce1a0004568
```

**Amazon EC2 AMI** is for running REMnux on Intel or AMD instances in AWS.

<a href="run-remnux-on-aws.md" class="button secondary" data-icon="cloud">Run REMnux on AWS</a>
{% endtab %}

{% tab title="ARM (arm64)" %}
Use these files on Apple M-series Macs and other 64-bit ARM systems.

**VMware Fusion ZIP** is specifically for [VMware Fusion](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).

<a href="https://download.remnux.org/202610b/remnux-noble-arm64-fusion.zip" class="button secondary" data-icon="download">Download Fusion ZIP</a>

```
d3af2491f029068972419e3208e58800e8c9944a99e6a7e3227a5fce0273b295
```

**UTM ZIP** is specifically for [UTM](https://mac.getutm.app/).

<a href="https://download.remnux.org/202610b/remnux-noble-arm64-utm.zip" class="button secondary" data-icon="download">Download UTM ZIP</a>

```
59f3035e7ac3767f4626b1670a86782f483cae7961c9d39f05c968c3245bfa48
```

**Amazon EC2 AMI** is for running REMnux on Graviton instances in AWS.

<a href="run-remnux-on-aws.md" class="button secondary" data-icon="cloud">Run REMnux on AWS</a>

The arm64 appliance lacks the tools that REMnux supports only on amd64. They include Wine and the tools that depend on it, such as scdbg, plus the tools [listed for the container](remnux-as-a-container.md#tools-unavailable-on-arm-systems).
{% endtab %}
{% endtabs %}

## Step 2: Confirm the Hash of the Downloaded File <a href="#confirm-hash" id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum`. Make sure it matches the hash listed under the file's download link in Step 1.

## Step 3: Import the Virtual Appliance <a href="#import-ova-file" id="import-ova-file"></a>

When importing the REMnux virtual appliance, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run. As a point of reference, most people find 4 GB RAM and 100 GB disk sufficient.

## Step 4: Start the REMnux Virtual Machine <a href="#start-remnux-vm" id="start-remnux-vm"></a>

Once you start your REMnux virtual machine, it will automatically log you into the REMnux environment.

There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted. When you need to elevate your privileges or access the REMnux virtual appliance remotely, note the following default credentials:

{% hint style="success" %}
Username: `remnux`\
Password: `malware`
{% endhint %}

These credentials apply to the downloadable virtual appliance. On instances launched from the [REMnux AMIs](run-remnux-on-aws.md), the `remnux` password is locked. You sign in to them over SSH with your key pair.

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

### VMware Fusion and UTM on Apple M-series Macs

The arm64 files are ZIP archives. Unzip the file you downloaded. Then open the `.vmwarevm` folder in VMware Fusion, or the `.utm` file in UTM.

Newer versions of Fusion may ask whether to upgrade the virtual machine. Either answer works. If you might also open the virtual machine in Fusion 13, choose not to upgrade it.

### Hyper-V

It's possible to import the pre-built REMnux virtual appliance into Hyper-V, but you'll need to take a few conversion steps. You'll need to extract the contents of the REMnux OVA file to obtain the enclosed VMDK file that captures the virtual disk of the distro, then convert it to the VHD format supported by Hyper-V:

1. Download the VMware OVA of the REMnux distro, as [outlined above](get-virtual-appliance.md#download-virtual-appliance).
2. Extract the downloaded OVA file using a tool such as "tar". One of the extracted files will have the .vmdk.gz name, such as remnux-noble-disk1.vmdk.gz.
3. Decompress the extracted .vmdk.gz file using a tool such as "gunzip" to generate a file with the .vmdk extension.
4. Use [qemu-img](https://qemu.readthedocs.io/en/latest/tools/qemu-img.html) (`qemu-img convert -O vhdx -o subformat=dynamic`) or [StarWind V2V Converter](https://www.starwindsoftware.com/starwind-v2v-converter) to convert the .vmdk file to the VHD format supported by Hyper-V.
5. Import the generated VHD file into Hyper-V.

For an overview of this process, see the video [How To Install REMnux on Windows 10 Hyper-V](https://www.youtube.com/watch?v=d8uyVi0nH-U) by Cyrus.

### Remote Cloud, Such as AWS

You can run REMnux in a cloud environment by importing the virtual appliance into it. You can also [install REMnux from scratch](install-from-scratch.md) on a cloud VM. On AWS, you can launch the [REMnux AMI](run-remnux-on-aws.md) if you prefer. It already has SSH set up for your key pair.

The REMnux virtual appliance ships in "dedicated" installation mode, which automatically turns off the SSH daemon. This configuration is generally desirable when running REMnux in a local lab. If you're deploying the virtual appliance in a cloud environment, you might need to keep SSH enabled to remotely access your REMnux system. In that case:

1. If the file `/etc/remnux-config` exists from an older REMnux installer, delete it. Otherwise, the installer will keep using the mode listed in that file when you later update REMnux.
2. Switch to the `cloud` installation mode by running `sudo remnux install --mode=cloud`. The installer will save this mode and apply it when you later update REMnux, so SSH will stay enabled. Connect the system to the internet first, because this command will also update the distro.
3. Create any missing SSH host keys by running `sudo ssh-keygen -A`. Then enable and start the SSH daemon with `sudo systemctl enable --now ssh`.
4. Change the default user's password and otherwise strengthen the SSH authentication method according to your requirements and risk tolerance.
5. Reboot your REMnux system.

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

If REMnux is stuck at a low resolution (such as 640x480) in Proxmox, run `remnux install` and reboot.

## Step 6: Upgrade the REMnux Virtual Machine <a href="#upgrade-remnux" id="upgrade-remnux"></a>

After installing the REMnux virtual machine, run the following command inside the VM as a regular, non-root user to upgrade it to the latest version of the distro:

```
remnux install
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 7: Take a Snapshot of the Virtual Machine <a href="#take-snapshot" id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual machine, so you can return it to a known good state if the need arises.
