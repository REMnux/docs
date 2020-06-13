# REMnux Installer

The REMnux installer is the tool that starts the installation or upgrade of the REMnux distro. This is a [Node.js](https://nodejs.org/) application distributed as a compiled Linux binary. Once installed, the tool is named `remnux` and resides in /usr/local/bin on REMnux. You can examine its source code in the [REMnux/remnux-cli](https://github.com/REMnux/remnux-cli) repository on GitHub.

## High-Level Workflow

At a high level, the REMnux installer takes the following actions:

1. Installs, if necessary, a recent version of [SaltStack](https://www.saltstack.com), which [manages the setup and configuraton of REMnux tools](saltstack-management.md).
2. Retrieves the appropriate release of REMnux Salt State files from the [REMnux/salt-states](https://github.com/REMnux/salt-states) repository on GitHub, which describe how Salt Stack should install and configure the tools.
3. Validates that the retrieved Salt State files are properly signed with the REMnux PGP key.
4. Runs Salt State, directing it to execute Salt State files that correspond to specified installation or upgrade options.

## Salt State File Retrieval and Validation

The REMnux installer retrieves Salt State files as a compressed archive from the "releases" area of the REMnux/salt-states repository. After extracting the contents, it places them under /var/cache/remnux/cli  in a subdirectory named according to the release version.

To validate the digital signature of the retrieved archive, the installer uses the REMnux public PGP key, which is embedded into the installer. To accommodate this, each Salt State release is signed with the corresponding REMnux private PGP key. The key ID is 28CD19DB.

## State File Groupings for REMnux Distro Installation <a id="state-file-bundles"></a>

The Salt State files for the REMnux distro are grouped into two "bundles," so it's easier to trigger the installation or upgrade without directly referring to every individual tool's Salt State file:

* [addon.sls](https://github.com/REMnux/salt-states/blob/master/remnux/addon.sls) installs the State Files appropriate for [adding REMnux to an existing system](../../install-distro/add-to-existing-system.md) without changing its look and feel. This corresponds to the `--mode=addon` parameter to the REMnux installer.
* [dedicated.sls](https://github.com/REMnux/salt-states/blob/master/remnux/dedicated.sls) installs the State Files appripriate for [setting up a dedicated REMnux system](../../install-distro/install-from-scratch.md). This applies the same State Files as addon.sls, but also invokes the "theme" State File to adjust the system's configuration for the full REMnux experience. This corresponds to the `--mode=dedicated` parameter to the REMnux installer, and is the default if `--mode` isn't specified.

It's possible to invoke these State File grouping using SaltStack directly, perhaps when experimenting with the installation without relying on the REMnux installer. To do this, first make sure a recent version of SaltStack is installed by executing the following commands after using `sudo` to switch to the root account:

```text
wget -O - https://repo.saltstack.com/apt/ubuntu/18.04/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add -
echo "deb http://repo.saltstack.com/apt/ubuntu/18.04/amd64/2019.2 bionic main" | sudo tee /etc/apt/sources.list.d/saltstack.list
apt update -y
apt install -y salt-minion git 
systemctl disable salt-minion
systemctl stop salt-minion
echo "file_client: local" > /etc/salt/minion
```

Next, download the desired Salt Stack archive from the "releases" area of the REMnux/salt-states repository or clone the repo like this:

```text
sudo git clone https://github.com/REMnux/salt-states.git /srv/salt
```

Finally, invoke Salt Stack to install the desired Salt State file grouping. For "dedicated" use the command:

```text
sudo salt-call --local state.sls remnux.dedicated
```

For "addon" use the command:

```text
sudo salt-call --local state.sls remnux.addon
```

You can supply the parameter `-l debug` to the `sudo-call` command to see verbose debug-level output of the installation.

{% hint style="info" %}
If the name of your current user isn't `remnux`, you'll need to specify the following parameter to the `salt-call` command:

```text
pillar='{"remnux_user": "YOUR_USERNAME"}'
```

Replace `YOUR_USERNAME` with your username. This is equivalent to the `--user=YOUR_USERNAME` optional parameter to the REMnux installer. The REMnux installer automatically invokes `salt-call` by specifying the name of the currently-logged in user, but you'll need to specify this yourself if running `salt-call` directly.
{% endhint %}

## REMnux Installer Upgrades

Once you've installed the REMnux distro, you shouldn't need to manually upgrade the REMnux installer. It will update itself when you upgrade the distro. It will do this because of the corresponding [remnux-cli.sls](https://github.com/REMnux/salt-states/blob/master/remnux/tools/remnux-cli.sls) Salt State file.

If you feel the need to upgrade the REMnux installer by hand, follow the [steps in the beginning of the Install REMnux from Scratch page](../../install-distro/install-from-scratch.md#get-remnux-installer).

## REMnux Distro Upgrades

If you already have the REMnux distro installed, you can run the following command to see which releases were published after you last installed or upgraded your distro:

```text
remnux list-upgrades
```

If you're curious to see the version that you currently have installed, you can list it using:

```text
remnux version
```

To upgrade your system to the latest version, run the command:

```text
sudo remnux upgrade
```

