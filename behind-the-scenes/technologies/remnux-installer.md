# REMnux Installer

The REMnux installer is the tool that starts the installation or upgrade of the REMnux distro. This is a [Node.js](https://nodejs.org/) application distributed as a compiled Linux binary. Once installed, the tool is named `remnux` and resides in /usr/local/bin on REMnux. You can examine its source code in the [REMnux/remnux-cli](https://github.com/REMnux/remnux-cli) repository on GitHub.

## High-Level Workflow

At a high level, the REMnux installer takes the following actions:

1. Installs, if necessary, a recent version of [SaltStack](https://www.saltstack.com), which [manages the setup and configuraton of REMnux tools](saltstack-management.md).
2. Retrieves the appropriate release of REMnux Salt state files from the [REMnux/salt-states](https://github.com/REMnux/salt-states) repository on GitHub, which describe how SaltStack should install and configure the tools.
3. Validates that the retrieved state files are properly signed with the REMnux PGP key.
4. Runs SaltState, directing it to execute state files that correspond to specified installation or upgrade options.

## State File Retrieval and Validation

The REMnux installer retrieves Salt state files as a compressed archive from the "releases" area of the REMnux/salt-states repository. After extracting the contents, it places them under /var/cache/remnux/cli  in a subdirectory named according to the release version.

To validate the digital signature of the retrieved archive, the installer uses the REMnux public PGP key, which is embedded into the installer. To accommodate this, each release of the state files is signed with the corresponding REMnux private PGP key. The key ID is `28CD19DB`.

It's possible to [invoke retrieve and invoke REMnux' state files by using SaltStack directly](state-files-without-the-remnux-installer.md), perhaps when experimenting with the installation without relying on the REMnux installer.

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

