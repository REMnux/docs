# Add or Update Tools

One way to contribute to REMnux is to add or update the tools that are a part of the distro. To add a new tool:

1. First become familiar with the way REMnux uses [Salt Stack](../../behind-the-scenes/technologies/saltstack-management.md) and [Debian packages](../../behind-the-scenes/technologies/debian-packages.md) to install and configure tools.
2. Then consider [c](./#contributing-salt-state-file)reating a [Salt State file](contribute-a-salt-state-file.md) or a [Debian package](contribute-a-debian-package.md) for the tool by following instructions in this section of the documentation site.

{% hint style="info" %}
If you discovered an issue with the way an existing REMnux tool is installed or configured, you can help correct it by revising that tool's State File. To do that, follow the instructions for [contributing a new Salt State file,](contribute-a-salt-state-file.md) but instead of creating a new file, find the State File for the tool and adjust it.
{% endhint %}

