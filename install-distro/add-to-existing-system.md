# Add REMnux to an Existing System

You can add REMnux to an existing system based on Ubuntu 18.04 by following instructions below. This configuration doesn't modify your system's look and feel, so you won't have the experience of the full REMnux environment. To the full experience, consider using the [REMnux virtual appliance](get-virtual-appliance.md).

## Step 1: Get the REMnux Installer <a id="get-remnux-installer"></a>

After logging into your existing system based on Ubuntu 18.04, download the REMnux installer:

```text
wget https://REMnux.org/remnux-cli
```

Validate that the SHA-256 hash of the downloaded file to make sure it matches this expected value:

```text
79796900999447d4ba3e256304b60a6c53ba4f1b26d6cb3b1c4231eb947eda8a
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

{% hint style="warning" %}
Before running the REMnux installer on your existing system, please reboot it. This helps avoid issues with the system's state that might interfere with the installation.
{% endhint %}

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
To keep your REMnux environment up-to-date run the REMnux installer periodically as described 
{% endhint %}

## Step 5: Take a Snapshot of the Virtual Machine <a id="take-snapshot"></a>

If you installed REMnux inside a virtual machine, consider taking a snapshot of the VM, so you can return it to a known good state if the need arises.

