# Keep the Distro Up to Date

## Upgrading and Updating the REMnux Distro <a href="#upgrading-updating-remnux" id="upgrading-updating-remnux"></a>

Unless you've installed REMnux in the `addon` mode, the distro disables automated Ubuntu update mechanisms for the OS. This allows you to control how and when your REMnux system attempts to initiate network connections, and avoids issues when running REMnux on an isolated network.

Keep your REMnux system up to date by running the following command once in a while as a regular, non-root user, so you benefit from the latest enhancements. Be sure to first connect the system to the internet. You don't need to separately update the OS or its packages. The REMnux installer handles that automatically.

```
remnux install
```

{% hint style="success" %}
If you're running the REMnux distro in a virtual machine, consider taking a snapshot before upgrading or updating your VM, so you can revert to a good state if something goes wrong.
{% endhint %}

## Issues Updating the REMnux Distro <a href="#issues-upgrading-updating-remnux" id="issues-upgrading-updating-remnux"></a>

If you receive an error upgrading or updating the REMnux distro, diagnose the problem by running:

```
remnux results
```

Also, consider rebooting your system and trying the operation again.

If the issue persists, you can open an issue in [the REMnux salt-states repo on GitHub](https://github.com/REMnux/salt-states/issues) and share the output of `remnux results` as well as your results.yaml and saltstack.log files.
