---
description: REMnux Documentation
---

# REMnux: A Linux Toolkit for Malware Analysis

![](.gitbook/assets/remnux-banner-v7.png)

This site provides documentation for [REMnux](https://REMnux.org/)®, a Linux toolkit for reverse-engineering and analyzing malicious software. REMnux provides a curated collection of free tools created by the community. Analysts can use it to investigate malware without having to find, install, and configure the tools.

## Install the REMnux Distro

The heart of the toolkit is the REMnux Linux distribution based on [Ubuntu](https://ubuntu.com), which incorporates many tools that malware analysts use to:

* [Examine static properties of a suspicious file.](discover-the-tools/examine+static+properties/)
* [Statically analyze malicious code.](discover-the-tools/statically+analyze+code/)
* [Dynamically reverse-engineer malicious code.](discover-the-tools/dynamically+reverse-engineer+code/)
* [Perform memory forensics of an infected system.](discover-the-tools/perform+memory+forensics.md)
* [Explore network interactions for behavioral analysis.](discover-the-tools/explore+network+interactions/)
* [Investigate system-level interactions of malware.](discover-the-tools/investigate+system+interactions.md)
* [Analyze malicious documents.](discover-the-tools/analyze+documents/)
* [Gather and analyze threat data.](discover-the-tools/gather+and+analyze+data.md)

The [Discover the Tools](discover-the-tools/examine+static+properties/) section of this documentation site lists and describes the tools comprise the REMnux distro. To start using them, you can:

* [Download the virtual appliance](install-distro/get-virtual-appliance.md) of the REMnux distro.
* [Install the REMnux distro from scratch](install-distro/install-from-scratch.md) on a dedicated system.
* [Add the REMnux distro](install-distro/add-to-existing-system.md) to an existing machine.
* [Run the REMnux distro as a Docker container.](install-distro/remnux-as-a-container.md)

## Run Tools in Containers <a id="run-in-containers"></a>

The REMnux toolkit also offers [Docker images of popular malware analysis tools](run-tools-in-containers/remnux-containers.md), making it possible to run them as containers without having to install the tools directly on the system.

## Get Involved with the Project

You can participate in the REMnux project by:

* [Asking and answering questions](get-involved/ask-and-answer-questions.md) related to the distro and its tools.
* [Adding or updating tools](get-involved/add-or-update-tools/) that comprise the distribution.
* [Creating articles, blog posts, and videos](get-involved/write-about-the-tools.md) about the tools on REMnux.

## Learn More About REMnux

You can learn about:

* [People](behind-the-scenes/people.md) and [technologies](behind-the-scenes/technologies/) that make REMnux possible
* [REMnux configuration tips](tips/remnux-config-tips.md) for getting the most out of the distro
* [Tips for using the tools](tips/remnux-tool-tips.md) on REMnux

Many of the tools available in the REMnux toolkit are discussed in the SANS course [FOR610: Reverse Engineering Malware](https://sans.org/for610). Lenny Zeltser, the founder and primary maintainer of REMnux, is also the primary author of this course.

