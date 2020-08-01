# Get the Virtual Appliance

The easiest way to get the REMnux distro is to download the REMnux virtual appliance in the OVA format, import it into your hypervisor, then [run the upgrade command](keep-the-distro-up-to-date.md) to make sure it's up-to-date. The virtual appliance is based on Ununtu 18.04.

## Step 1: Download the Virtual Appliance File <a id="download-virtual-appliance"></a>

The REMnux virtual appliance just over 54 GB. It comes as the industry-standard OVA file, which you can import into your virtualization software.

Pick one OVA file to download: Unless you're using Oracle VM VirtualBox, get the general OVA file. If you're using VirtualBox, get the VirtualBox version.

{% tabs %}
{% tab title="General OVA Link" %}
Download the REMnux general OVA file from one of these locations:

* [Uploadfiles.io](https://ufile.io/gq4plfnf) \(primary\)
* Google Drive \(mirror\)
{% endtab %}

{% tab title="VirtualBox OVA Link" %}
Download the REMnux VirtualBox OVA from one of these locations:

* [Uploadfiles.io](https://ufile.io/525nlqcz) \(primary\)
* Google Drive \(mirror\)
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Some browsers change the extension of the REMnux OVA file after downloading it, possibly giving it the incorrect `.ovf` extension. If that happens, rename the file so it has the `.ova` extension before proceeding.
{% endhint %}

## Step 2: Confirm the Hash the OVA File <a id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

{% tabs %}
{% tab title="General OVA Hash" %}
```text
0fd090c1a7f60db557c4004308fb6fa7f72531a1777278c93f50979d0ed55994
```
{% endtab %}

{% tab title="VirtualBox VM Hash" %}
```text
711be9f5966980991f8fb07ba789c993afd9ea0bfeb992b10bd3da1164ba431b
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

When importing the REMnux virtual appliance, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run.

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

If your REMnux window is too small when you boot it up the system in VirtualBox, increase its scaling from 100% by going to the VirtualBox menu `View` &gt; `Virtual Screen 1`. The best scaling factor depends on the size and resolution of your physical screen, but `Scale to 200%` often works well.

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

## Step 5: Upgrade the REMnux Virtual Machine <a id="upgrade-remnux"></a>

After installing the REMnux virtual machine, run the following command inside the VM to upgrade it to the latest version of the distro:

```text
remnux upgrade
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 6: Take a Snapshot of the Virtual Machine <a id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual machine, so you can return it to a known good state if the need arises.

