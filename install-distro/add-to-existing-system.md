# Add REMnux to an Existing System

You can add REMnux to an existing system based on Ubuntu 18.04 by following instructions below. This configuration doesn't modify your system's look and feel, so you won't have the experience of the full REMnux environment. To the full experience, consider using the [REMnux virtual appliance](get-virtual-appliance.md).

{% hint style="danger" %}
The following instructions are for the limited beta version of the upcoming v7 release of REMnux. See the [older documentation site](https://REMnux.org/docs) if you're interested in v6 version of REMnux.
{% endhint %}

## Step 1: Get the REMnux Installer <a id="get-remnux-installer"></a>

After logging into your existing system based on Ubuntu 18.04, download the REMnux installer:

```text
wget https://REMnux.org/remnux-cli
```

Validate that the SHA-256 of the downloaded file matches the expected value:

```text
ef887858f75e1f182406d520d7544f855b61dcf581979db441bc755cb35a6d4f
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

## Step 3: Run the REMnux Installer <a id="run-remnux-installer"></a>

You're now ready to install the REMnux distro. To kick off the installation, run:

```text
sudo remnux install --mode=addon
```

The `addon` mode will avoid modifications that can modify the look and feel of your existing system. As a result, you won't get the experience of the standard REMnux environment..

The installation will take about an hour, depending on your resources and internet connection.

{% hint style="info" %}
If the REMnux installer produces an error, understand the issue by reviewing the saltstack.log file under /var/cache/remnux/cli in the subdirectory that matches the REMnux version you're installing. Pay particular attention to lines that start with`[ERROR]`. Sometimes problems occur due to network issues, in which case retrying the installation later might work.
{% endhint %}

## Step 4: Reboot the  REMnux System <a id="reboot-remnux"></a>

Once the REMnux installation finishes, reboot your new REMnux system by typing:

```text
sudo reboot
```

Login to your system to start benefiting from the tools that the REMnux distro includes.

{% hint style="success" %}
Run the following command once in a while to keep your REMnux environment up-to-date, so you benefit from the latest enhancements:

```text
sudo remnux upgrade --mode=addon
```

You don't need to run this command now, since you've just installed a fresh version of the distro. When you are ready to upgrade, keep in mind that it requires an internet access. Remember to specify `--mode=addon` to avoid modifying the look and feel of your system.
{% endhint %}

## Step 5: Take a Snapshot of the Virtual Machine <a id="take-snapshot"></a>

If you installed REMnux inside a virtual machine, consider taking a snapshot of the VM, so you can return it to a known good state if the need arises.

