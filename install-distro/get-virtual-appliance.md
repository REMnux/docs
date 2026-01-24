# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the REMnux virtual appliance in the OVA format, import it into your hypervisor, then [run the upgrade command](keep-the-distro-up-to-date.md) to make sure it's up-to-date.

{% hint style="info" %}
REMnux is currently based on an x86/amd64 version of Ubuntu, and won't run on ARM processors such as Apple's M-series chips.
{% endhint %}

## Step 1: Download the Virtual Appliance File <a href="#download-virtual-appliance" id="download-virtual-appliance"></a>

The REMnux virtual appliance is approximately 7 GB. It comes as an industry-standard OVA file, which you can import into your virtualization software. It's based on Ubuntu 24.04 (Noble).

Decide which OVA file to download. Unless you're using Oracle VM VirtualBox, get the general OVA file. If you're using VirtualBox, get the VirtualBox version. Download your preferred OVA file:

{% tabs %}
{% tab title="General OVA" %}
This general OVA file works with most hypervisors. If you're using VirtualBox, get the VirtualBox version instead from the other tab:

[Download the general OVA file.](https://download.remnux.org/202601/remnux-noble-amd64.ova)
{% endtab %}

{% tab title="VirtualBox OVA" %}
This VirtualBox OVA file is specifically for VirtualBox. Get the general version from the other tab if you're using other hypervisors:

[Download the VirtualBox OVA file.](https://download.remnux.org/202601/remnux-noble-amd64-virtualbox.ova)
{% endtab %}
{% endtabs %}

{% hint style="success" %}
Some browsers ([e.g., Brave](https://github.com/brave/brave-browser/issues/4413)) change the extension of the OVA file after downloading it, possibly giving it the incorrect .ovf extension. If that happens, rename the file so it has the .ova extension before proceeding.
{% endhint %}

## Step 2: Confirm the Hash of the OVA File <a href="#confirm-hash" id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

{% tabs %}
{% tab title="General OVA Hash" %}
The general OVA file:

```
156e0cf2db2d580cd2d90b6dc1aaf892d5bd25d340c122f9a007887c0336e151
```
{% endtab %}

{% tab title="VirtualBox OVA Hash" %}
The VirtualBox OVA file:

```
7cc8b55a8db32a1a9d42839fe3454922a6eb45010419428f3ce5fece4193e184
```
{% endtab %}
{% endtabs %}

## Step 3: Import the OVA File <a href="#import-ova-file" id="import-ova-file"></a>

If possible, upgrade your virtualization software to the latest version. Then, use it to import the downloaded OVA file. If you're not sure how to do that, follow the instructions below:

{% tabs %}
{% tab title="Direct Import" %}
* [VMware Workstation](https://docs.vmware.com/en/VMware-Workstation-Pro/15.0/com.vmware.ws.using.doc/GUID-DDCBE9C0-0EC9-4D09-8042-18436DA62F7A.html?hWord=N4IghgNiBcIJYFsAOB7ATgFwAQoG5hAF8g)
* [VMware vSphere](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-17BEDA21-43F6-41F4-8FB2-E01D275FE9B4.html)
* [VMware Fusion](https://docs.vmware.com/en/VMware-Fusion/11/com.vmware.fusion.using.doc/GUID-275EF202-CF74-43BF-A9E9-351488E16030.html)
* [Oracle VM VirtualBox](https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html)
{% endtab %}

{% tab title="Conversion" %}
* [KVM/QEMU](https://www.vinchin.com/en/blog/convert-ova-to-qcow2.html)
* [AWS](https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-image-import.html)
* [Hyper-V](get-virtual-appliance.md#hyper-v)
* [Proxmox](https://www.proxmox.com)
{% endtab %}
{% endtabs %}

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

If running VirtualBox on Windows 10, be sure to [disable Hyper-V](https://forums.virtualbox.org/viewtopic.php?f=25\&t=99390) using the command `bcdedit /set hypervisorlaunchtype off`. Do this even if Hyper-V appears disabled in the Windows Features listing. If you don't, you are likely to run into problems downloading files and updating REMnux.

If your REMnux window is too small when you boot it up the system in VirtualBox, activate the Scaling Mode for the VM via the VirtualBox menu View > Scaling Mode.

If your REMnux virtual machine is unable to communicate over the network, check whether it has a network interface other than the loopback ("lo") by running the `ifconfig` command. If a non-loopback interface is missing, perform the following steps to add it:

1. Run the `networkctl` command to determine the name of the adapter ("link") of type "ether". It might be named something like "enp0s17".
2. Set up the network interface by replacing _YOUR\_NIC_ in the following command with the name you've identified in the previous step (e.g., "enp0s17)": `sudo ip link set up YOUR_NIC`
3. Edit the /etc/netplan/01-netcfg.yaml file (e.g., use the `code` command). Under "ethernets:" replace the name there (e.g, "ens33") with the name of your network card (e.g., "enp0s17").
4. Reboot your REMnux virtual machine.

If you're building your own VirtualBox VM (not using the pre-built VirtualBox OVA), install VirtualBox Guest Additions from the ISO for full functionality:

1. Devices → Insert Guest Additions CD image
2. Navigate to the mounted CD under `/media/remnux/` and run `sudo ./VBoxLinuxAdditions.run`
3. Reboot

Note: The Ubuntu `virtualbox-guest-*` packages do not provide auto-resize and clipboard support. Use the ISO-based Guest Additions instead.

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

If you converted the REMnux virtual appliance to KVM/QEMU, run `remnux install` to automatically install spice-vdagent (display resize, copy/paste) and other KVM guest tools.

### Proxmox

To use REMnux in Proxmox, [import the general OVA](https://www.itsfullofstars.de/2019/07/import-ova-as-proxmox-vm/) using CPU type `qemu64` (not `kvm64`). After importing:

1. Go to VM > Options > Boot Order and enable the imported disk.
2. Optionally set VM > Hardware > Display to SPICE(qxl) for better graphics.

**First Boot:** The SPICE display may cause boot issues before guest tools are installed. If the VM fails to boot properly:

1. Set Hardware > Display to "Standard VGA" temporarily.
2. Boot the VM and log in.
3. Run `remnux install` to install guest tools and apply display fixes.
4. Shut down, change display back to SPICE, and boot normally.

After running `remnux install`, Proxmox integration (qemu-guest-agent, spice-vdagent, nomodeset) is configured automatically.

## Step 6: Upgrade the REMnux Virtual Machine <a href="#upgrade-remnux" id="upgrade-remnux"></a>

After installing the REMnux virtual machine, run the following command inside the VM as a regular, non-root user to upgrade it to the latest version of the distro:

```
sudo remnux install
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 7: Take a Snapshot of the Virtual Machine <a href="#take-snapshot" id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual machine, so you can return it to a known good state if the need arises.
