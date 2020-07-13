# Get the REMnux Virtual Appliance

The easiest way to get the REMnux distro is usually to download the REMnux virtual appliance, then [run the upgrade command](keep-the-distro-up-to-date.md) to make sure it's up-to-date. The virtual appliance is based on Ununtu 18.04.

## Step 1: Download the Virtual Appliance File <a id="download-virtual-appliance"></a>

The REMnux virtual appliance comes as the industry-standard OVA file, which you can import into your virtualization software. The file is just approximately 5 GB.

[Download the REMnux OVA file from Box.com via this link.](https://app.box.com/s/x4667hph6xeuo3yyy6ycj82x01t8zv9m)

{% hint style="danger" %}
The download link above is for the beta version of the upcoming v7 release of REMnux. See the [older documentation site](https://REMnux.org/docs) if you're interested in v6 version of REMnux.
{% endhint %}

## Step 2: Confirm the Hash the File <a id="confirm-hash"></a>

Validate the SHA-256 hash of the downloaded file using a tool such as `sha256sum` or `shasum` to make sure it matches this expected value:

```text
8130cee63f084847bb59a84160057836c75f752b506c7b9366c3060574b6359a
```

## Step 3: Import the OVA File <a id="import-ova-file"></a>

Use your virtualization software to import the downloaded OVA file. If you're not sure how to do that, follow the instructions below:

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
{% endtab %}
{% endtabs %}

When importing the REMnux virtual appliance, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run.

## Step 4: Start the REMnux Virtual Appliance

Once you start your REMnux virtual appliance, it will automatically log you into the REMnux environment.

There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted. When you need to elevate your privileges or access the REMnux virtual appliance remotely, note the follow default credentials:

{% hint style="success" %}
Username: `remnux`  
Password: `malware`
{% endhint %}

Depending on which hypervisor or environment you're using, you might need to take a few steps:

### VirtualBox

When you start your imported virtual machine, it won't have a network interface card besides the loopback adapter. To correct this:

Determine the name of your VM's network adapter by looking running the following command and identifying the adapter of type "ether." Its name will look something like "enp0s17":

```text
networkctl
```

Set up the network interface by replacing "YOUR\_NIC" in the following command with the name you've identified in the previous step:

```text
sudo ip link set up YOUR_NIC
```

Edit /etc/netplan/01-netcfg.yaml and under `ethernets:` replace the name there \(e.g, "ens33"\) with the name of your network card \(e.g., enp0s17\). Then reboot.

Next, [install VirtualBox Guest Additions](https://linuxize.com/post/how-to-install-virtualbox-guest-additions-in-ubuntu/) in your VM. Start by adding an optical drive to your virtual machine using VirtualBox and mount the Guest Additions ISO file. In the virtual machine use the `mount` command to see the directory where the virtual CD was mounted, then go there, and run this command:

```text
sudo sh ./VBoxLinuxAdditions.run
```

Reboot.

### KVM/QEMU

If you converted the virtual appliance to KVM/QEMU, install install the "[spice-vdagent](http://manpages.ubuntu.com/manpages/cosmic/man1/spice-vdagent.1.html)" package to be able to resize the windows of your virtual machine and copy/paste between it and your host.

### Remote Cloud

The REMnux virtual appliance ships in "dedicated" installation mode, which automatically turns off SSH daemon. This configuration is generally desirable when running REMnux in a local lab. If you're deploying the virtual appliance in a cloud environment, you might need to keep SSH enabled to remotely access your REMnux system. In that case:

1. Edit the /etc/remnux-config and change the mode from `dedicated` to `cloud`.
2. Enable the SSH daemon by running: `sudo systemctl enable ssh`.
3. Change the default user's password and otherwise strengthen the SSH authentication method according to your requirements and risk tolerance.
4. Reboot the REMnux system.

## Step 5: Upgrade the REMnux Virtual Appliance <a id="upgrade-remnux"></a>

After installing the REMnux virtual appliance, run the following command inside the VM to upgrade it to the latest version of the distro:

```text
remnux upgrade
```

For more details about keeping your REMnux environment current, so you benefit from the latest enhancements, see the [Keeping REMnux Up to Date](keep-the-distro-up-to-date.md) section.

## Step 6: Take a Snapshot of the Virtual Appliance <a id="take-snapshot"></a>

Consider taking a snapshot of your REMnux virtual appliance, so you can return it to a known good state if the need arises.

