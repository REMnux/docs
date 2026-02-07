# REMnux Installer

The REMnux installer is a wrapper around [Cast](https://github.com/ekristen/cast) that provides a familiar interface for installing and upgrading the REMnux distro. Once installed, the tool is named `remnux` and resides in `/usr/local/bin`. You can examine its source code in the [REMnux/distro](https://github.com/REMnux/distro) repository on GitHub.

## High-Level Workflow

At a high level, the REMnux installer takes the following actions:

1. Installs or upgrades [Cast](https://github.com/ekristen/cast), verifying the download's integrity using a SHA256 checksum.
2. Cast retrieves the appropriate release of Salt state files from the [REMnux/salt-states](https://github.com/REMnux/salt-states) repository on GitHub. These state files describe how [SaltStack should install and configure the tools](saltstack-management.md).
3. Cast validates the retrieved state files using the REMnux [Cosign](https://github.com/sigstore/cosign) signature.
4. Cast runs SaltStack, directing it to execute state files that correspond to the specified installation mode.

{% hint style="info" %}
The REMnux installer is presently [incompatible with non-transparent proxies](../../tips/remnux-config-tips.md#behind-proxy).
{% endhint %}

## Installation Modes

The installer supports three modes, specified with the `--mode` option:

* **dedicated** (default): Sets up a full REMnux system with the REMnux look and feel. Use this for a [dedicated REMnux system](../../install-distro/install-from-scratch.md) in a local lab.
* **addon**: Installs REMnux tools without changing the system's look and feel. Use this to [add REMnux to an existing system](../../install-distro/add-to-existing-system.md).
* **cloud**: Like dedicated, but keeps the SSH daemon enabled for remote access. Use this for cloud-based deployments.

## State File Retrieval and Validation

Cast retrieves Salt state files as a compressed archive from the "releases" area of the REMnux/salt-states repository. After extracting the contents, it places them under `/var/cache/cast` in a subdirectory named according to the release version.

To validate the integrity of the retrieved archive, Cast uses the REMnux [Cosign](https://github.com/sigstore/cosign) signature. Each release of the state files is signed with the corresponding REMnux Cosign key, and Cast verifies the signature before applying the state files.

It's possible to [retrieve and invoke REMnux state files using SaltStack directly](state-files-without-the-remnux-installer.md), for example when experimenting with the installation without relying on the REMnux installer.

## Installing and Updating REMnux

To install or update your REMnux system to the latest version, run:

```text
sudo remnux install
```

You can also use `sudo remnux upgrade`, which is an alias for `install`.

To install a specific version of the state files, use the `--version` option:

```text
sudo remnux install --version=v2026.6.24
```

If the name of your current user isn't `remnux`, specify it with the `--user` option:

```text
sudo remnux install --user=YOUR_USERNAME
```

To see version and diagnostic information about your REMnux installation:

```text
remnux debug
```

To check the results of the last installation or update:

```text
remnux results
```
