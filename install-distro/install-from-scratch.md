# Install REMnux from Scratch

If [starting with a pre-built virtual appliance](get-virtual-appliance.md) is impractical or you prefer to customize all aspects of the system, you can build a dedicated REMnux environment from scratch by taking the following steps. This allows you to install the REMnux distro on a physical host or a virtual machine.

{% hint style="danger" %}
The following instructions are for the limited beta version of the upcoming v7 release of REMnux. See the [older documentation site](https://REMnux.org/docs) if you're interested in v6 version of REMnux.
{% endhint %}

## Step 1: Install Ubuntu 18.04 64-Bit Minimal <a id="install-ubuntu"></a>

If you're looking to recreate the lightweight environment provided by the REMnux pre-built virtual appliance, start with the 64-bit [MinimalCD version of Ubuntu 18.04](https://help.ubuntu.com/community/Installation/MinimalCD) \("Bionic Beaver"\).

Install Ubuntu. It's OK to follow default settings, but be sure to adjust them according to your needs.

{% hint style="success" %}
When the Ubuntu installer prompts you for details about the user it will create, select the following to stay consistent with the default configuration of REMnux:

Full name: `REMnux User`  
Username: `remnux`  
Password: `malware`
{% endhint %}

If you're installing Ubuntu in a virtual machine, allocate resources such as RAM and disk space based on what you have available. REMnux is a relatively lightweight distro, but the more you allocate to it, the faster it will run.

At the "Software selection" screen don't select any software and simply press "Continue." The REMnux installer will install the necessary packages in a later step.

Boot into your new Ubuntu system. You should find yourself at the command prompt. Login using the credentials you specified during the Ubuntu installation.

## Step 2: Get the REMnux Installer <a id="get-remnux-installer"></a>

Download the REMnux installer from the REMnux website by running this command on your new Ubuntu system:

```text
wget https://REMnux.org/remnux-cli
```

Validate that the SHA-256 hash of the downloaded file to make sure it matches this expected value:

```text
dc79a10e31eb795dfe749f35c45b1570033676f1a3df4882917ae24c807cdd5e
```

To generate the hash of your  file, run:

```text
sha256sum remnux-cli
```

Set up the REMnux installer by running these commands:

```text
mv remnux-cli remnux
chmod +x remnux
sudo mv remnux /usr/local/bin
```

## Step 2: Install GnuPG <a id="install-gnupg"></a>

The MinimalCD version of Ubuntu includes very few components. Install GnuPG, so that the REMnux installer can automatically validate the signature of the REMux configuration files it will download during the installation process. To install GnuPG, run:

```text
sudo apt install -y gnupg
```

## Step 3: Run the REMnux Installer <a id="run-remnux-installer"></a>

You're now ready to install the REMnux distro.

If you're planning to run REMnux in a local lab, kick off the installation by runing this command:

```text
sudo remnux install
```

If you're depoying REMnux in a remote cloud environment and will need to keep the SSH daemon enabled for remotely accessing the system, use the following command instead and remember to harden the system after it installs to avoid unauthorized logins:

```text
sudo remnux install --mode=cloud
```

The installation will take about an hour, depending on your resources and internet connection.

{% hint style="info" %}
If the REMnux installer produces an error, understand the issue by reviewing the saltstack.log file under /var/cache/remnux/cli in the subdirectory that matches the REMnux version you're installing. Pay particular attention to lines that start with`[ERROR]`. Sometimes problems occur due to network issues, in which case retrying the installation later might work.
{% endhint %}

## Step 4: Reboot the  REMnux System <a id="reboot-remnux"></a>

Once the REMnux installation finishes, reboot your new REMnux system by typing:

```text
sudo reboot
```

After the reboot, REMnux will automatically log you in. There is no logon screen for accessing the REMnux environment, because analysts generally use REMnux on a system to which physical access is already restricted.

{% hint style="success" %}
Run the following command once in a while to keep your REMnux environment up-to-date, so you benefit from the latest enhancements:

```text
remnux upgrade
```

You don't need to run this command now, since you've just installed a fresh version of the distro. When you are ready to upgrade, keep in mind that it requires an internet access.
{% endhint %}

## Step 5: Take a Snapshot of the Virtual Machine <a id="take-snapshot"></a>

If you installed REMnux inside a virtual machine, consider taking a snapshot of the VM, so you can return it to a known good state if the need arises.

