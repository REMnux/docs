# Keep the Distro Up to Date

## Upgrading and Updating the REMnux Distro <a id="upgrading-updating-remnux"></a>

Unless you've installed REMnux in the `addon` mode, the distro disabled automated Ubuntu update mechanisms for the OS. This allows you to control how and when your REMnux system attempts to initiate network connections, and avoids issues when REMnux on an isolated network.

Keep your REMnux system up to date by running the following command once in a while as a regular, non-root user, so you benefit from the latest enhancements. Be sure to first connect the system to the internet.

```text
remnux upgrade
```

Even if if the command above tells you, "No upgrades available," you can still refresh your current tools. The following command will make sure that you're running the latest versions of the installed [Debian packages](../behind-the-scenes/technologies/debian-packages.md) and Python modules, without adding adding any new tools to your system:

```text
remnux update
```

To sum up, the `upgrade` option updates all the tools and adds new ones that might have been incorporated into the REMnux distro. The `update` command is a subset, and updates your existing Debian packages and Python modules.

{% hint style="success" %}
If you're running the REMnux distro in a virtual machine, consider taking a snapshot before upgrading or updating your VM, so you can revert to a good state if something goes wrong.
{% endhint %}

## Issues Upgrading and Updating the REMnux Distro <a id="issues-upgrading-updating-remnux"></a>

If you receive an error upgrading or updating the REMnux distro when using the `remnux` command, first make sure that you're running the command as a regular, non-root user. Also, try rebooting your system and trying the operation again.

If you still run into problems, refresh your [APT package database](../behind-the-scenes/technologies/debian-packages.md)  by issuing the following commands, then try the operation again:

```text
sudo apt update
sudo apt autoremove
sudo apt --fix-broken install
```

If the issue persists, diagnose the problem by reviewing the saltstack.log file under /var/cache/remnux/cli in the subdirectory that matches the REMnux state-files version you're installing. Search for the log file for result: false messages and look at the surrounding 5 lines or the 8 lines above each message to see the state file that caused the issue. \(`grep -i -C 5 'result: false'` or `grep -i -B 8 'result: false'`\).

##  <a id="run-in-containers"></a>

