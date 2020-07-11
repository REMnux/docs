# Ask and Answer Questions

## Issues Updating the REMnux Distro <a id="issues-updating-remnux"></a>

If you receive an error [upgrading or updating the REMnux distro](../install-distro/keep-the-distro-up-to-date.md) when using the `remnux` command, first reboot your REMnux system, then try the operation again.

If rebooting doesn't update the problem, refresh your [APT package database](../behind-the-scenes/technologies/debian-packages.md)  by issuing the following commands, then trying the operation again:

```text
sudo apt update
sudo apt autoremove
sudo apt --fix-broken install
```

## Reporting and Resolving REMnux Issues <a id="reporting-and-resolving-issues"></a>

If you need help with some aspect of REMnux, please open an issue in "Issues" area of the REMnux repository on GitHub that is most relevant to the nature of your request:

* The functioning and configuration of tools as part of the distro: [REMnux/salt-states](https://github.com/REMnux/salt-states/issues)
* The use of the REMnux distro installer: [REMnux/remnux-cli](https://github.com/REMnux/remnux-cli/issues)
* The main REMnux.org website: [REMnux/website-source](https://github.com/REMnux/website-source/issues)
* Contents of this REMnux documentation site: [REMnux/docs-beta](https://github.com/REMnux/docs-beta)
* Docker images available as part of the REMnux toolkit: [REMnux/docker](https://github.com/REMnux/docker/issues)

If you're an experienced user of REMnux and related technologies, consider reviewing the locations above and sharing your expertise by helping resolve the issues.

