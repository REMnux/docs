# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the REMnux virtual appliance in the OVA format, import it into your hypervisor, then [run the upgrade command](keep-the-distro-up-to-date.md) to make sure it's up-to-date.

## Step 1: Download the Virtual Appliance File <a id="download-virtual-appliance"></a>

The REMnux virtual appliance approximately 5 GB. It comes as an industry-standard OVA file, which you can import into your virtualization software.

Decide which OVA file to download by making two choices:

* _Will you use VirtualBox or another hypervisor?_ Unless you're using Oracle VM VirtualBox, get the general OVA file. If you're using VirtualBox, get the VirtualBox version. 
* _Do you prefer to Ubuntu 18.04 \(Bionic\) or 20.04 \(Focal\) as the base OS?_ The 20.04 version is newer, and will be supported longer.

Then download your preferred OVA file:

{% tabs %}
{% tab title="General OVA" %}
Download the [Ubuntu 18.04 \(Bionic\) OVA file](https://ufile.io/3jrlp4sl) or the [Ubuntu 20.04 \(Focal\) OVA file](https://ufile.io/s9woxw5y). This general version works with most hypervisors; if you're using VirtualBox, get the VirtualBox version.
{% endtab %}

{% tab title="VirtualBox OVA" %}
Download the [Ubuntu 18.04 \(Bionic\) OVA file](https://ufile.io/o6bc66wr) or the [Ubuntu 20.04 \(Focal\) OVA file](https://ufile.io/2mh8nsyo). This VirtualBox version is specifically for VirtualBox; get the general version if you're using other hypervisors.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Some browsers \([e.g., Brave](https://github.com/brave/brave-browser/issues/4413)\) change the extension of the OVA file after downloading it, possibly giving it the incorrect .ovf extension. If that happens, rename the file so it has the .ova extension before proceeding.
{% endhint %}

## Step 2: Confirm the Hash the OVA File <a id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

{% tabs %}
{% tab title="General OVA Hash" %}
General OVA file based on Ubuntu 18.04 \(Bionic\):

```text
bf08a6d2b0b4813131b704c1cfcb921320e81ae917c825fa5c01e2131e0409c0
```

General OVA file based on Ubuntu 20.04 \(Focal\):

```text
20e7547bcd0c0e6a3f572a5af3de679bce716be965e9def0665a22d5ea977750
```
{% endtab %}

{% tab title="VirtualBox OVA Hash" %}
VirtualBox OVA file based on Ubuntu 18.04 \(Bionic\):

```text
43f7e4fe7a58bd2012df5624423846307b4a028f655ad02cf40f929b6dc8231d
```

VirtualBox OVA File based on Ubuntu 20.04 \(Focal\):

```text
d023ad740843939c253ccd3d9d5f07170961874ff21fa24491b6a56af05dabcd
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
* [Hyper-V and Azure](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn873998%28v=ws.11%29?redirectedfrom=MSDN)
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

