# Install from Scratch

If [starting with a pre-built virtual appliance](get-virtual-appliance.md) is impractical or you prefer to customize all aspects of the system, you can build a dedicated REMnux environment from scratch by taking the following steps. This allows you to install the REMnux distro on a physical host or a virtual machine.

{% hint style="info" %}
REMnux is based on an x86/amd64 version of Ubuntu, and won't run on an ARM processor such as Apple M1.
{% endhint %}



## Step 1: Install Ubuntu 20.04 <a href="#install-ubuntu" id="install-ubuntu"></a>

If you're looking to recreate the lightweight environment provided by the REMnux pre-built virtual appliance, start with the 64-bit minimal Ubuntu 20.04 ISO installation file.

[Download the Ubuntu 20.04 mini ISO image.](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso) SHA-256 hash of the file should be:

```
0e79e00bf844929d40825b1f0e8634415cda195ba23bae0b041911fde4dfe018
```

Install Ubuntu 20.04 using the downloaded ISO installer. It's OK to follow default settings, but be sure to adjust them according to your needs.

If you're installing Ubuntu in a virtual machine, allocate resources based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run. For your refrence, the [prebuilt REMnux virtual appliance](get-virtual-appliance.md) ships with 4 GB RAM and 60 GB disk.

{% hint style="success" %}
When the Ubuntu installer prompts you for details about the user it will create, select the following to stay consistent with the default configuration of REMnux:

Full name: `REMnux User`\
Username: `remnux`\
Password: `malware`
{% endhint %}

At the "Software selection" screen don't select any software and simply press "Continue." The REMnux installer will install the necessary packages in a later step.

Boot into your new Ubuntu system. You should find yourself at the command prompt. Login using the credentials you specified during the Ubuntu installation.

## Step 2: Get the REMnux Installer <a href="#get-remnux-installer" id="get-remnux-installer"></a>

Download the REMnux installer from the REMnux website by running this command on your new Ubuntu system:

```
wget https://REMnux.org/remnux-cli
```

Validate that the SHA-256 hash of the downloaded file to make sure it matches this expected value:

```
23c7f4eefa7599ea2c4156f083906ea5fd99df18f306e4bb43eec0430073985a
```

To generate the hash of your  file, run:

```
sha256sum remnux-cli
```

Set up the REMnux installer by running these commands:

```
mv remnux-cli remnux
chmod +x remnux
sudo mv remnux /usr/local/bin
```

## Step 2: Install GnuPG <a href="#install-gnupg" id="install-gnupg"></a>

The minimal version of Ubuntu includes very few components. Install GnuPG, so that the REMnux installer can automatically validate the signature of the REMux configuration files it will download during the installation process. To install GnuPG, run:

```
sudo apt install -y gnupg
```

## Step 3: Run the REMnux Installer <a href="#run-remnux-installer" id="run-remnux-installer"></a>

You're now ready to install the REMnux distro.

If you're planning to run REMnux in a local lab, kick off the installation by runing this command:

```
sudo remnux install
```

If you're depoying REMnux in a remote cloud environment and will need to keep the SSH daemon enabled for remotely accessing the system, use the following command instead to avoid disabling the SSH daemon. Remember to harden the system after it installs to avoid unauthorized logins:

```
sudo remnux install --mode=cloud
```

The installation will take about an hour, depending on your resources and internet connection.

{% hint style="info" %}
If the REMnux installer produces an error, diagnose the issue by reviewing the saltstack.log file under /var/cache/remnux/cli in the subdirectory that matches the REMnux state-files version you're installing. Search for the log file for `result: false` messages and look at the surrounding 5 lines or the 8 lines above each message to see the state file that caused the issue. (`grep -i -C 5 'result: false'` or `grep -i -B 8 'result: false'`).
{% endhint %}

## Step 4: Reboot the  REMnux System <a href="#reboot-remnux" id="reboot-remnux"></a>

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
