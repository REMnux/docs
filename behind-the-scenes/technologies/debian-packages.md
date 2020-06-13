# Debian Packages

A common way of installing software on Linux distributions derived from [Debian](https://www.debian.org), including [Ubuntu](https://ubuntu.com), is to use the [Debian packaging format](https://help.ubuntu.com/community/SoftwarePackagingFormats#Debian_packages_.28.deb.29). Since REMnux is based on Ubuntu, it relies heavily on this format. As a result, many of the tools that SaltStack installs on REMnux are managed using the standard Ubuntu package management system called APT behind the scenes.

## Custom Debian Packages

Whenever possible, REMnux installs Debian-formatted packages from the standard Ubuntu repositories. In addition, there is a REMnux-specific repository of custom packages, which is [hosted on Launchpad](https://launchpad.net/~remnux/+archive/ubuntu/stable/+packages)--a website maintaned by Ubuntu's parent company.

As part of the REMnux installation, the r[emnux.sls](https://github.com/REMnux/salt-states/blob/master/remnux/repos/remnux.sls) Salt State file adds the REMnux package repository to the system, so it's available to the APT package manager. The installation also adds [other repositories](https://github.com/REMnux/salt-states/tree/master/remnux/repos) where some packages reside, including the one for [SIFT Workstation](https://digital-forensics.sans.org/community/downloads).

Once built and tested, custom Debian-based packages are digitally signed using the REMnux private key, and are upladed to Launchpad, which validates the signature and makes the available to REMnux systems via the APT package manager.

## Other Forms of Installation

In cases where the latest versions of malware analysis tools are not available as Debian-formatted packages, the distro installs the using other packaging formats such as:

* [pip](https://pypi.org/project/pip/) for Python
* [gems](https://rubygems.org) for Ruby on Rails
* [npm](https://www.npmjs.com) for Node.js

In some cases, REMnux directs SaltStack to install tools by directly downloading them from GitHub, their authors' websites, or other sources. This is done in situations where the author didn't package the tool using a standard format, and creating a custom Debian package was too time consuming.

{% hint style="info" %}
The Debian-based packaging format offers the highest reliability, because it requires that the package be fully self-contained and not rely on external resources for installation. Installing tools by downloading them from authors' websites is on the other end of the reliability spectrum, and is the least preferred method for managing tools on REMnux.
{% endhint %}

