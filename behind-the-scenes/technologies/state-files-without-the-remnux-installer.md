# State Files Without the REMnux Installer

The best way to install, upgrade, or update your REMnux system is usually to use the [REMnux installer](remnux-installer.md). However, sometimes you might want to invoke the underlying Salt state files directly, perhaps when experimenting with REMnux or when getting around some deficiency of the REMnux installer. 

## State File Groupings for REMnux Distro Installation <a id="state-file-bundles"></a>

The Salt state files for the REMnux distro are grouped into "bundles," so it's easier to trigger the installation or upgrade without directly referring to every individual tool's SaltStack state file:

* [addon.sls](https://github.com/REMnux/salt-states/blob/master/remnux/addon.sls) installs the state files for [adding REMnux to an existing system](../../install-distro/add-to-existing-system.md) without changing its look and feel. This corresponds to the `--mode=addon` parameter to the REMnux installer.
* [dedicated.sls](https://github.com/REMnux/salt-states/blob/master/remnux/dedicated.sls) installs the state files for [setting up a dedicated REMnux system](../../install-distro/install-from-scratch.md) in a local lab. This applies the same state files as addon.sls, but also invokes the "theme" state file to adjust the system's configuration for the full REMnux experience. This corresponds to the `--mode=dedicated` parameter to the REMnux installer, and is the default if `--mode` isn't specified.
* [cloud.sls](https://github.com/REMnux/salt-states/blob/master/remnux/cloud.sls) installs the state files for setting up a dedicated REMnux system in a cloud environment. This applies the same state files as dedicated.sls, except it doesn't disable the SSH daemon, which many people use for remote access. This corresponds to the `--mode=cloud` parameter to the REMnux installer

## Manually Installing SaltStack

If you decide to interact with REMnux' Salt state files without the REMnux installer, first make sure a recent version of SaltStack is installed by executing the following commands, assuming you're using Ubuntu 20.04 \(Focal\) as the base OS:

```text
sudo -s
wget -O - https://repo.saltproject.io/py3/ubuntu/20.04/amd64/latest/salt-archive-keyring.gpg | apt-key add -
echo "deb [arch=amd64] https://repo.saltproject.io/py3/ubuntu/20.04/amd64/latest focal main" | tee /etc/apt/sources.list.d/saltstack.list
apt update -y
apt install -y salt-minion git 
systemctl disable salt-minion
systemctl stop salt-minion
```

## Retrieving REMnux State Files

You can retrieve REMnux' Salt state files, by downloading the desired state file archive from [the "releases" area of the REMnux/salt-states repository](https://github.com/REMnux/salt-states/releases) or clone the repo like this:

```text
sudo git clone https://github.com/REMnux/salt-states.git /srv/salt
```

## Invoking SaltStack to Install State File Groupings

You can invoke SaltStack's `salt-call` utility to install the desired state file grouping. For example, for "dedicated" you'd use the command:

```text
sudo salt-call -l debug --local state.sls remnux.dedicated
```

The parameter `-l debug` to the `salt-call` command provides verbose debug-level output of the operation. You can skip this parameter if you don't want that level of detail.

By the way, if the name of your current user isn't `remnux`, you'll need to specify the following parameter to the `salt-call` command:

```text
pillar='{"remnux_user": "YOUR_USERNAME"}'
```

Replace `YOUR_USERNAME` with your username. This is equivalent to the `--user=YOUR_USERNAME` optional parameter to the REMnux installer. The REMnux installer automatically invokes `salt-call` by specifying the name of the currently-logged in user, but you'll need to specify this yourself if running `salt-call` directly.

