# Implement Enhancements

This page outlines enhancement ideas for REMnux. If you have the time and expertise to address implement them, please consider lending a hand.

## The REMnux Installer Should Determine the Upgrade Mode <a id="upgrade-should-determine-mode"></a>

When performing an upgrade, the REMnux installer isn't smart enought to automatically use [the "addon" mode](../install-distro/add-to-existing-system.md) on a system where the distro was originally installed using the "addon" mode. The user has to remember to specify `--mode=addon` when initiating the upgrade. People might forget to do this, and accidentally install the upgrade in [the "dedicated" mode](../install-distro/install-from-scratch.md), which will modify the look-and-feel of the system. 

The solution is to modify the REMnux installer \([source code file remnux-cli.js](https://github.com/REMnux/remnux-cli/blob/master/remnux-cli.js)\) to read the /etc/remnux-config file and automatically use the appropriate upgrade mode based on contents of the "mode" line, which looks like this if the system was installed using the "addon" mode:

```text
mode: addon
```

This functionality should also apply to the `update` feature of the REMnux installer, just like the `upgrade` feature explained above.

## Booting in VMware Might Display an SMBus Warning <a id="smbus-warning"></a>

The REMnux boots in a VMware environment, you might see the following SMBus warning briefly appear on the screen:

```text
piix4_smbus 000:00:07.3: SMBus Host Controller not enabled!
```

This notice doesn't affect the functioning of the distro, but it could generate a concern. To eliminate this warning, you can run the following commands in the virtual machine and then reboot it:

```text
sudo echo "blacklist i2c-piix4" >> /etc/modprobe.d/blacklist.conf
sudo update-initramfs -u
```

As an enhancement, it would be nice to crete a Salt State configuration file that automatically takes these actions when the distro is being installed in a VMware environment. One way to spot VMware would be to run the following command:

```text
dmidecode -s system-product-name | grep VMware
```

## The Installation of Thug is Time-Consuming <a id="thug-installation"></a>

At the moment, the installation of Thug requires compiling the tool's dependencies during install time, which can take 20 minutes. To speed up the process, it would be good to generate a Debian package for Thug.

## BinNavi Needs a Database in PostgreSQL <a id="binnavi-database"></a>

[BinNavi](https://github.com/google/binnavi), installed by [binnavi.sls](https://github.com/REMnux/salt-states/blob/master/remnux/tools/binnavi.sls), requires a PostgreSQL database to operate. The database application itself is already installed on REMnux via [postgresql.sls](https://github.com/REMnux/salt-states/blob/master/remnux/packages/postgresql.sls). It would be nice to craft a new Salt State file under r[emnux/theme ](https://github.com/REMnux/salt-states/tree/master/remnux/theme)to create a database for BinNavi with default credentials  `remnux`/`malware`.

