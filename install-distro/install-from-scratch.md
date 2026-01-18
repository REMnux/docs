# Install from Scratch

If [starting with a pre-built virtual appliance](get-virtual-appliance.md) is impractical or you prefer to customize all aspects of the system, you can build a dedicated REMnux environment from scratch by taking the following steps. This allows you to install the REMnux distro on a physical host or a virtual machine.

{% hint style="info" %}
REMnux is currently based on an x86/amd64 version of Ubuntu, and won't run on ARM processors such as Apple's M-series chips.
{% endhint %}

## Step 1: Install Ubuntu 24.04 <a href="#install-ubuntu" id="install-ubuntu"></a>

If you're looking to recreate the lightweight environment provided by the REMnux pre-built virtual appliance, start with the 64-bit Ubuntu 24.04 Server ISO installation file.

Download the latest Ubuntu 24.04 Server ISO image [from this Ubuntu page](https://releases.ubuntu.com/noble/).

* Be sure to select "64-bit PC (AMD64) server install image" as the file you'll download.
* As of this writing, [you can use this](https://releases.ubuntu.com/noble/ubuntu-24.04.3-live-server-amd64.iso) link, but if the link doesn't work, get it from the Ubuntu page.
* You can verify its integrity using the checksums provided on that Ubuntu download page.

If you're installing Ubuntu in a virtual machine, allocate resources based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run. For your reference, the [prebuilt REMnux virtual appliance](get-virtual-appliance.md) ships with 4 GB RAM and 100 GB disk.

Install Ubuntu 24.04 using the downloaded ISO installer:

1. Boot from the ISO and select "Try or Install Ubuntu Server".
2. Select your language and keyboard layout.
3. When prompted for the installation type, **select "Ubuntu Server (minimized)"**.
4. Configure the network. DHCP is typically fine; adjust if needed.
5. Skip the proxy configuration unless your environment requires it.
6. Accept the default Ubuntu archive mirror.
7. When configuring storage, **uncheck "Set up this disk as an LVM group"** to use a simpler partition layout.
8. When prompted for the profile setup, use the following to stay consistent with the default REMnux configuration:
   * Your name: `REMnux User`
   * Server's name: `remnux`
   * Username: `remnux`
   * Password: `malware`
9. Skip the Ubuntu Pro setup.
10. Don't install OpenSSH server unless you need remote access.
11. Don't select any additional snaps to install.
12. Wait for the installation to complete and reboot.

Boot into your new Ubuntu system. You should find yourself at the command prompt. Login using the credentials you specified during the Ubuntu installation.

{% hint style="info" %}
You don't need to separately update the OS or its packages. The REMnux installer handles that automatically.
{% endhint %}

## Step 2: Get the REMnux Installer <a href="#get-remnux-installer" id="get-remnux-installer"></a>

Download the REMnux installer from the REMnux website by running this command on your new Ubuntu system:

```
curl -O https://REMnux.org/remnux
```

Validate that the SHA-256 hash of the downloaded file to make sure it matches this expected value:

```
94673eb529ec6a363f332fb68c8e94bcd2ec2137746ccfce5acc45f65016f91b
```

To generate the hash of your file, run:

```
sha256sum remnux
```

Set up the REMnux installer by running these commands:

```
chmod +x remnux
sudo mv remnux /usr/local/bin
```

## Step 3: Run the REMnux Installer <a href="#run-remnux-installer" id="run-remnux-installer"></a>

You're now ready to install the REMnux distro.

If you're planning to run REMnux in a local lab, kick off the installation by running this command:

```
sudo remnux install
```

If you're deploying REMnux in a remote cloud environment and will need to keep the SSH daemon enabled for remotely accessing the system, use the following command instead to avoid disabling the SSH daemon. Remember to harden the system after it installs to avoid unauthorized logins:

```
sudo remnux install --mode=cloud
```

The installation will take about an hour, depending on your resources and internet connection.

{% hint style="info" %}
If the REMnux installer produces an error, diagnose the issue by running:

```
remnux results
```

This command shows installation results and highlights any failures.
{% endhint %}

## Step 4: Reboot the REMnux System <a href="#reboot-remnux" id="reboot-remnux"></a>

Once the REMnux installation finishes, reboot your new REMnux system by typing:

```
sudo reboot
```

After the reboot, REMnux will automatically log you in. There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted.

If necessary, [change the keyboard layout](../tips/remnux-config-tips.md#keyboard-layout-change) of your system to match your locale and setup.

{% hint style="success" %}
To keep your REMnux environment up-to-date run the REMnux installer periodically as described in the [Keep the Distro Up to Date](keep-the-distro-up-to-date.md) section.
{% endhint %}

## Step 5: Review Configuration Tweaks Specific to Your Hypervisor <a href="#hypervisor-tweaks" id="hypervisor-tweaks"></a>

Depending on the hypervisor you're using, you might need to implement a few configuration tweaks to address or preempt issues with your REMnux virtual machine. Please review the [Special Hypervisor Requirements](get-virtual-appliance.md#hypervisor-requirements) before considering your installation finalized.

## Step 6: Take a Snapshot of the Virtual Machine <a href="#take-snapshot" id="take-snapshot"></a>

If you installed REMnux inside a virtual machine, consider taking a snapshot of the VM, so you can return it to a known good state if the need arises.
