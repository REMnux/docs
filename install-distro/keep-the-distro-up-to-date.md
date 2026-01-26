# Keep the Distro Up to Date

## Upgrading and Updating the REMnux Distro <a href="#upgrading-updating-remnux" id="upgrading-updating-remnux"></a>

Unless you've installed REMnux in the `addon` mode, the distro disabled automated Ubuntu update mechanisms for the OS. This allows you to control how and when your REMnux system attempts to initiate network connections, and avoids issues when REMnux on an isolated network.

Keep your REMnux system up to date by running the following command once in a while as a regular, non-root user, so you benefit from the latest enhancements. Be sure to first connect the system to the internet. You don't need to separately update the OS or its packages. The REMnux installer handles that automatically.

```
remnux install
```

{% hint style="success" %}
If you're running the REMnux distro in a virtual machine, consider taking a snapshot before upgrading or updating your VM, so you can revert to a good state if something goes wrong.
{% endhint %}

## Issues Updating the REMnux Distro <a href="#issues-upgrading-updating-remnux" id="issues-upgrading-updating-remnux"></a>

If you receive an error upgrading or updating the REMnux distro when using the `remnux` command, first make sure that you're running the command as a regular, non-root user. Also, try rebooting your system and trying the operation again.

If you still run into problems, refresh your [APT package database](../behind-the-scenes/technologies/debian-packages.md) by issuing the following commands, then try the operation again:

```
apt update
apt autoremove
apt --fix-broken install
```

If the issue persists, diagnose the problem by running:

```
remnux results
```

This command shows installation results and highlights any failures. If you need further help, you can open an issue in [the REMnux salt-states repo on Github](https://github.com/REMnux/salt-states/issues) and share out output of `remnux results` as well as your results.yml and saltstack.log file.
