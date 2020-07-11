# Keep the Distro Up to Date

Keep your REMnux system up to date by running the following command once in a while, so you benefit from the latest enhancements. Be sure to first connect the system to the internet.

```text
remnux upgrade
```

Even if if the command above tells you, "No upgrades available," you can still refresh your current tools. The following operation will make sure that you're running the latest versions of the installed [Debian packages](../behind-the-scenes/technologies/debian-packages.md) and Python modules, without adding adding any new tools to your system:

```text
remnux update
```

To sum up, the `upgrade` option updates all the tools and adds new ones that might have been incorporated into the REMnux distro. The `update` command is a subset, and updates your existing Debian packages and Python modules.

{% hint style="info" %}
If you're running the REMnux distro in a virtual machine, consider taking a snapshot before upgrading or updating your VM, so you can revert to a good state if something goes wrong.
{% endhint %}

##  <a id="run-in-containers"></a>

