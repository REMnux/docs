# Add to an Existing System

You can add REMnux to an existing system based on Ubuntu 24.04 by following instructions below. This configuration doesn't modify your system's look and feel, so you won't have the experience of the full REMnux environment. For the full experience, consider using the [REMnux virtual appliance](get-virtual-appliance.md).

{% hint style="info" %}
REMnux is currently based on an x86/amd64 version of Ubuntu, and won't run on ARM processors such as Apple's M-series chips.
{% endhint %}

## Step 1: Get the REMnux Installer <a href="#get-remnux-installer" id="get-remnux-installer"></a>

After logging into your existing system based on Ubuntu 24.04, download the REMnux installer:

```
curl -O https://REMnux.org/remnux
```

Validate the SHA-256 hash of the downloaded file to make sure it matches this expected value:

```
15581da24c906126aba2c1e21001311d7a93d9d017c95597c662372248964661
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

Before proceeding, make sure your system doesn't have an active Ubuntu unattended upgrade in progress. One way to do this is check whether the "unattended-upgrade" process is active (`ps aux | grep unattended-upgrade`.) If the upgrade is active, let it finish or [disable it](https://askubuntu.com/questions/1098757/ubuntu-18-10-unattended-upgrades-shutdown-wait-for-signal#1099258), then reboot the system before installing REMnux.

## Step 2: Run the REMnux Installer <a href="#run-remnux-installer" id="run-remnux-installer"></a>

You're now ready to install the REMnux distro. To kick off the installation, run:

```
sudo remnux install --mode=addon
```

The `addon` mode will avoid modifications that can modify the look and feel of your existing system. As a result, you won't get the experience of the standard REMnux environment.

The installation will take about an hour, depending on your resources and internet connection.

{% hint style="info" %}
If the REMnux installer produces an error, diagnose the issue by running:

```
remnux results
```

This command shows installation results and highlights any failures.

If you need further help, you can open an issue in [the REMnux salt-states repo on Github](https://github.com/REMnux/salt-states/issues) and share the output of `remnux results` as well as your results.yaml and saltstack.log files.
{% endhint %}

## Step 3: Reboot the REMnux System <a href="#reboot-remnux" id="reboot-remnux"></a>

Once the REMnux installation finishes, reboot your new REMnux system by typing:

```
sudo reboot
```

Login to your system to start benefiting from the tools that the REMnux distro includes.

{% hint style="success" %}
To keep your REMnux environment up-to-date run the REMnux installer periodically as described in the [Keep the Distro Up to Date](keep-the-distro-up-to-date.md) section.
{% endhint %}

## Step 4: Take a Snapshot of the Virtual Machine <a href="#take-snapshot" id="take-snapshot"></a>

If you installed REMnux inside a virtual machine, consider taking a snapshot of the VM, so you can return it to a known good state if the need arises.
