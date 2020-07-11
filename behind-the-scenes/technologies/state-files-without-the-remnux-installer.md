# State Files Without the REMnux Installer

The best way to install, upgrade, or update your REMnux system is usually to use the [REMnux installer](remnux-installer.md). However, sometimes you might want to invoke the underlying SaltStack state files directly, perhaps when experimenting with REMnux or when getting around some deficiency of the REMnux installer.  To do this, first make sure a recent version of SaltStack is installed by executing the following commands:

```text
sudo -s
wget -O - https://repo.saltstack.com/apt/ubuntu/18.04/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add -
deb [arch=amd64] http://repo.saltstack.com/apt/ubuntu/18.04/amd64/3000 bionic main | sudo tee /etc/apt/sources.list.d/saltstack.list
apt update -y
apt install -y salt-minion git 
systemctl disable salt-minion
systemctl stop salt-minion
exit
```

Next, download the desired state file archive from the "releases" area of the REMnux/salt-states repository or clone the repo like this:

```text
sudo git clone https://github.com/REMnux/salt-states.git /srv/salt
```

Finally, invoke SaltStack's `salt-call` utility to install the desired state file grouping. For "dedicated" use the command:

```text
sudo salt-call -l debug --local state.sls remnux.dedicated
```

For "addon" use the command:

```text
sudo salt-call -l debug --local state.sls remnux.addon
```

The parameter `-l debug` to the `salt-call` command provides verbose debug-level output of the operation. You can skip this parameter if you don't want that level of detail.

By the way, if the name of your current user isn't `remnux`, you'll need to specify the following parameter to the `salt-call` command:

```text
pillar='{"remnux_user": "YOUR_USERNAME"}'
```

Replace `YOUR_USERNAME` with your username. This is equivalent to the `--user=YOUR_USERNAME` optional parameter to the REMnux installer. The REMnux installer automatically invokes `salt-call` by specifying the name of the currently-logged in user, but you'll need to specify this yourself if running `salt-call` directly.

