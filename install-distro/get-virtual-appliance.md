# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the REMnux virtual appliance in the OVA format, import it into your hypervisor, then [run the upgrade command](keep-the-distro-up-to-date.md) to make sure it's up-to-date.

## Step 1: Download the Virtual Appliance File <a id="download-virtual-appliance"></a>

The REMnux virtual appliance approximately 5 GB. It comes as an industry-standard OVA file, which you can import into your virtualization software.

Decide which OVA file to download by making two choices:

* _Will you use VirtualBox or another hypervisor?_ Unless you're using Oracle VM VirtualBox, get the general OVA file. If you're using VirtualBox, get the VirtualBox version. 
* _Do you prefer to Ubuntu 20.04 \(Focal\) or 18.04 \(Bionic\) as the base OS?_ The 20.04 version is newer, and will be supported longer; go with the 20.04 unless you specifically need the 18.04 version.

Then download your preferred OVA file:

{% tabs %}
{% tab title="General OVA" %}
Download the [Ubuntu 20.04 \(Focal\) OVA file](https://app.box.com/s/u1uoseysbxk0hay31t12hm0m45wvl8tq) or the [Ubuntu 18.04 \(Bionic\) OVA file](https://app.box.com/s/90on2oy03ej3p183yvd4yqw56zfidn1k). These OVA files work with most hypervisors; if you're using VirtualBox, get the VirtualBox version instead from the other tab.
{% endtab %}

{% tab title="VirtualBox OVA" %}
Download the [Ubuntu 20.04 \(Focal\) OVA file](https://app.box.com/s/wf8pxzgo5cvrirglmeieqsrqkncera5c) or the [Ubuntu 18.04 \(Bionic\) OVA file](https://ufile.io/o6bc66wr). These VirtualBox OVA files are specifically for VirtualBox; get the general version from the other tab if you're using other hypervisors.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Some browsers \([e.g., Brave](https://github.com/brave/brave-browser/issues/4413)\) change the extension of the OVA file after downloading it, possibly giving it the incorrect .ovf extension. If that happens, rename the file so it has the .ova extension before proceeding.
{% endhint %}

## Step 2: Confirm the Hash the OVA File <a id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

{% tabs %}
{% tab title="General OVA Hash" %}
General OVA file based on Ubuntu 20.04 \(Focal\):

```text
8be61dec9856f47bd2592b1c5b5e499cbcffc66a58114e6ca24c85e5a0fcc1d9
```

General OVA file based on Ubuntu 18.04 \(Bionic\):

```text
01d1ade3ef76e935b0f283e857a88324dda7628997a8a3ecd2c8cbc6a6c45522
```
{% endtab %}

{% tab title="VirtualBox OVA Hash" %}
VirtualBox OVA File based on Ubuntu 20.04 \(Focal\):

```text
b7718176a7a9b4425111b4b733a51f6d5f3c95145aa0da53a3361f79631894d2
```

VirtualBox OVA file based on Ubuntu 18.04 \(Bionic\):

```text
43f7e4fe7a58bd2012df5624423846307b4a028f655ad02cf40f929b6dc8231d
```
{% endtab %}
{% endtabs %}

## Step 3: Import the OVA File <a id="import-ova-file"></a>

If possible, upgrade your virtualization software to the latest version. Then, use it to import the downloaded OVA file. If you're not sure how to do that, follow the instructions below:

{% tabs %}
{% tab title="Direct Import" %}
* [VMware Workstation](https://docs.vmware.com/en/VMware-Workstation-Pro/15.0/com.vmware.ws.using.doc/GUID-DDCBE9C0-0EC9-4D09-8042-18436DA62F7A.html?hWord=N4IghgNiBcIJYFsAOB7ATgFwAQoG5hAF8g)
* [VMware vSphere](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-17BEDA21-43F6-41F4-8FB2-E01D275FE9B4.html)
* [VMware Fusion](https://docs.vmware.com/en/VMware-Fusion/11/com.vmware.fusion.using.doc/GUID-275EF202-CF74-43BF-A9E9-351488E16030.html)
* [Oracle VM VirtualBox](https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html)
{% endtab %}

{% tab title="Conversion" %}
* [KVM/QEMU](https://blog.ricosharp.com/posts/2019/Converting-ova-file-to-qcow2)
* [AWS](https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-image-import.html)
* [Hyper-V](get-virtual-appliance.md#hyper-v)
* [Proxmox](https://www.proxmox.com/)
{% endtab %}
{% endtabs %}

When importing the REMnux virtual appliance, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run. As a point of reference, most people find 4 GB RAM and 60 GB disk sufficient.

## Step 4: Start the REMnux Virtual Machine <a id="start-remnux-vm"></a>

Once you start your REMnux virtual machine, it will automatically log you into the REMnux environment.

There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted. When you need to elevate your privileges or access the REMnux virtual appliance remotely, note the follow default credentials:

{% hint style="success" %}
Username: `remnux`  
Password: `malware`
{% endhint %}

If necessary, [change the keyboard layout](../tips/remnux-config-tips.md#keyboard-layout-change) of your system to match your locale and setup.

## Step 5: Consider Special Hypervisor Requirements <a id="hypervisor-requirements"></a>

Depending on which hypervisor or environment you're using, you might need to take the following steps:

### VirtualBox

If running VirtualBox on Windows 10, be sure to [disable Hyper-V](https://forums.virtualbox.org/viewtopic.php?f=25&t=99390) using the command `bcdedit /set hypervisorlaunchtype off`. Do this even if Hyper-V appears disabled in the Windows Features listing. If you don't, you are likely to run into problems downloading files and updating REMnux.

If your REMnux window is too small when you boot it up the system in VirtualBox, activate the Scaling Mode for the VM via the VirtualBox menu View &gt; Scaling Mode.

If your REMnux virtual machine is unable to communicate over the network, check whether has a network interface other than the loopback \("lo"\) by running the `ifconfig` command. If a non-loopback interface is missing, perform the following steps to add it:

1. Run the `networkctl` command to determine the name of the adapter \("link"\) of type "ether". It might be named something like "enp0s17".
2. Set up the network interface by replacing _YOUR\_NIC_ in the following command with the name you've identified in the previous step \(e.g., "enp0s17\)": `sudo ip link set up YOUR_NIC`
3. Edit the /etc/netplan/01-netcfg.yaml file \(e.g., use the `code` command\). Under "ethernets:" replace the name there \(e.g, "ens33"\) with the name of your network card \(e.g., "enp0s17"\).
4. Reboot your REMnux virtual machine.

### VMware

VMware sometimes conflicts with the Ubuntu graphical environment, which by default uses [Wayland](https://wiki.ubuntu.com/Wayland) display protocol. The problems manifest themselves through the VM being unresponsive to keyboard and mouse; clipboard sharing and copy-and-paste VMware features might not be working, too.

If you encounter this issue, try configring your REMnux virtual machine to switch from Wayland to Xorg. The change should be unnoticeable to your user experience, but it might address the VMware issue. To make the switch, switch to the root user account \(`sudo -s`\) and edit the file /etc/gdm3/custom.conf. Uncomment this line:

```text
#WaylandEnable=false
```

So it says:

```text
WaylandEnable=false
```

Then reboot your virtual machine \(`reboot`\).

### Hyper-V

It's possible to import the pre-built REMnux virtual appliance into Hyper-V, but you'll need to take a few conversion steps. You'll need to extract the contents of the REMnux OVA file to obtain the enclosed VMDK file that captures the virtual disk of the distro, then convert it to the VHD format supported by Hyper-V:

1. Download the General OVA of the REMnux distro, as [outlined above](get-virtual-appliance.md#download-virtual-appliance).
2. Extract the downloaded OVA file using a tool such as "tar". One of the extracted files will have the .vmdk.gz name, such as remnux-v7-focal-disk1.vmdk.gz.
3. Decompress the extracted .vmdk.gz file using a tool such as "gunzip" to generate a file with the .vmdk extension.
4. Use [qemu-img](https://qemu.readthedocs.io/en/latest/tools/qemu-img.html) \(`qemu-img convert -O vhd`\) or [StarWind V2V Converter](https://www.starwindsoftware.com/starwind-v2v-converter) to convert the .vmdk file to the VHD format supported by Hyper-V.
5. Import the generated VHD file into Hyper-V.

### Remote Cloud, Such as AWS

The REMnux virtual appliance ships in "dedicated" installation mode, which automatically turns off the SSH daemon. This configuration is generally desirable when running REMnux in a local lab. If you're deploying the virtual appliance in a cloud environment, you might need to keep SSH enabled to remotely access your REMnux system. In that case:

1. Edit the /etc/remnux-config and change the mode from `dedicated` to `cloud`.
2. Enable the SSH daemon by running: `sudo systemctl enable ssh`.
3. Change the default user's password and otherwise strengthen the SSH authentication method according to your requirements and risk tolerance.
4. Reboot your REMnux system.

### KVM/QEMU

If you converted the REMnux virtual appliance to KVM/QEMU, install install the "[spice-vdagent](http://manpages.ubuntu.com/manpages/cosmic/man1/spice-vdagent.1.html)" package in the virtual machine to be able to resize the windows of your VM and copy/paste between it and your host.

### Proxmox

If you're planning to use the REMnux virtual appliance in Proxmox, [follow the steps in this article](https://www.itsfullofstars.de/2019/07/import-ova-as-proxmox-vm/) to import the OVA. Once done, consider taking the following steps using the Proxmox interface:

1. VM &gt; Hardware &gt; Display &gt; Set to -&gt; SPICE\(qxl\)
2. VM &gt; Hardware &gt; Option &gt; Spice Enhancements &gt; Video Streaming: all

## Step 6: Upgrade the REMnux Virtual Machine <a id="upgrade-remnux"></a>

After installing the REMnux virtual machine, run the following command inside the VM as a regular, non-root user to upgrade it to the latest version of the distro:

```text
remnux upgrade
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 7: Take a Snapshot of the Virtual Machine <a id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual machine, so you can return it to a known good state if the need arises.

