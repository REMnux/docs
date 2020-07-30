# Keep the Distro Up to Date

## Upgrading and Updating the REMnux Distro <a id="upgrading-updating-remnux"></a>

Keep your REMnux system up to date by running the following command once in a while, so you benefit from the latest enhancements. Be sure to first connect the system to the internet.

```text
remnux upgrade
```

{% hint style="info" %}
It's a good idea to reboot your system before upgrading it. This helps avoid issues with the system's state that might interfere with the upgrade.
{% endhint %}

Even if if the command above tells you, "No upgrades available," you can still refresh your current tools. The following operation will make sure that you're running the latest versions of the installed [Debian packages](../behind-the-scenes/technologies/debian-packages.md) and Python modules, without adding adding any new tools to your system:

```text
remnux update
```

To sum up, the `upgrade` option updates all the tools and adds new ones that might have been incorporated into the REMnux distro. The `update` command is a subset, and updates your existing Debian packages and Python modules.

{% hint style="success" %}
If you're running the REMnux distro in a virtual machine, consider taking a snapshot before upgrading or updating your VM, so you can revert to a good state if something goes wrong.
{% endhint %}

## Issues Upgrading and Updating the REMnux Distro <a id="issues-upgrading-updating-remnux"></a>

If you receive an error upgrading or updating the REMnux distro when using the `remnux` command, first reboot your REMnux system, then try the operation again. This often fixes the issue.

If rebooting doesn't update the problem, refresh your [APT package database](../behind-the-scenes/technologies/debian-packages.md)  by issuing the following commands, then trying the operation again:

```text
sudo apt update
sudo apt autoremove
sudo apt --fix-broken install
```

##  <a id="run-in-containers"></a>

