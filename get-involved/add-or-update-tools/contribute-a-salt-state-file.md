# Contribute a Salt State File

If there's a malware analysis tool you'd like to see as part of the REMnux distro, consider creating the Salt State file that would allow the tool to be included. The following steps explain how you can build such a file.

{% hint style="info" %}
Before starting this work, consider [reaching out to Lenny Zeltser](https://zeltser.com/contact) to confirm that it makes sense to include the tool as part of REMnux. Also, become familiar with the way REMnux uses [Salt Stack](../../behind-the-scenes/technologies/saltstack-management.md) to manage the installation and configuration of tools.
{% endhint %}

## 1. Install Git and Docker

Follow the steps appropriate for your Operating System to install [Git](https://git-scm.com) and [Docker](https://www.docker.com/products/docker-desktop) on your system.

## 2. Clone the REMnux/salt-state Repository

Get a copy of the current REMnux/salt-state repository, which contains the REMnux Salt State files. A common way to do this is to run:

```text
git clone https://github.com/REMnux/salt-states.git
```

## 3. Create the Salt State File

Determine in which subdirectory under salt-states/remnux your new Salt State file should reside. Common locations are:

* For Ubuntu packages: `packages`
* For Python packages: `python-packages`
* For tools distributed as compiled or JAR files: `tools`
* For scipts that aren't installable using a package manager: `scripts`

Instead of attempting to create a file from scratch, consider identifying a State File that operates similarly to what you have in mind, and copying its contents to form the basis of your new file.

{% hint style="success" %}
The State File should fully describe all dependencies of the software you're aiming to install. When crafting the file, assume that the installation will occur on a pristine, minimal system without any existing packages. Be sure to explicitly specify all the dependencies.
{% endhint %}

## 4. Test the Salt State File

Once the State File is ready, test it locally by running it in a Docker container. The easiest way to do it is to run the [dev-state.sh](https://github.com/REMnux/salt-states/blob/master/.ci/dev-state.sh) script, which is a part of the REMnux/salt-state repository in the .ci directory.

{% hint style="info" %}
The dev-state.sh script is a wrapper around Docker. It  retrieves and launches the baseline container "[teamdfir/sift-saltstack-tester](https://hub.docker.com/r/teamdfir/sift-saltstack-tester)" built for testing State Files for [SIFT Workstation](https://digital-forensics.sans.org/community/downloads) and REMnux distros. The container is just the base Ubuntu OS without any optional packages, plus Salt Stack. This minimal state allows you to confirm that the State File you'll be testing specifies all the dependencies for the new tool.
{% endhint %}

Once you're at the command promot inside the tester container, direct SaltStack to process your new Salt State file by running this command in the container:

```text
salt-call -l debug --local --retcode-passthrough --state-output=mixed state.sls STATE-PATH
```

In the command above, replace "STATE-PATH" with the Salt Stack path to your new file using dots instead of slashes. For example, if you were runing peframe.sls, which is in remnux/python-packages, you'd specify `remnux.python-packages.peframe`.

The command will produce verbose debug-level output, so you can diagnose any issues. Adjust your new Salt State file to address whichever problems arise, so the `salt-call` command completes successfully.

## 5. Add Metadata to the Salt State File

To make sure the tool is properly included in the REMnux tool listing, included the following metadata comments on top of your Salt State file to describe the tool:

```text
# Name: 
# Website: 
# Description: 
# Category: 
# Author: 
# License: 
# Notes: 
```

## 6. Create a Pull Request

Once you have a working, tested Salt State file in the local copy of the REMnux/salt-states repoistory, [create a GitHub pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) for that repo, so your file may be considered for inclusion in the REMnux distro. If the pull request isn't working, consider submitting the file to Lenny Zeltser [by email](https://zeltser.com/contact).

##  <a id="revise-existing-tool"></a>

