# Implement Enhancements

This page outlines enhancement ideas for REMnux. If you have the time and expertise to address implement them, please consider lending a hand.

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

[BinNavi](https://github.com/google/binnavi), installed by [binnavi.sls](https://github.com/REMnux/salt-states/blob/master/remnux/tools/binnavi.sls), requires a PostgreSQL database to operate. The database application itself is already installed on REMnux via [postgresql.sls](https://github.com/REMnux/salt-states/blob/master/remnux/packages/postgresql.sls). It would be nice to craft a new Salt State file under [remnux/theme ](https://github.com/REMnux/salt-states/tree/master/remnux/theme)to create a database for BinNavi with default credentials  `remnux`/`malware`.

