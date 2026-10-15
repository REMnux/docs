# Run REMnux as a Container

You can run the REMnux distro as a [Docker](https://www.docker.com) container by using a prebuilt image, hosted in [the REMnux repository on Docker Hub](https://hub.docker.com/repository/docker/remnux/remnux-distro).

## Local Interactive Shell

If you have Docker installed, you can start the REMnux distro container in interactive mode, as explained below. The following command will automatically download the distro image (approximately 6 GB to download and 14 GB on disk) if your system doesn't already have it.

To run the REMnux version built on top of Ubuntu 24.04 (Noble):

```
docker run --rm -it -u remnux remnux/remnux-distro:noble bash
```

{% hint style="info" %}
The image runs on Intel or AMD processors (amd64) and on 64-bit ARM processors (arm64), such as Apple's M-series chips. Docker downloads the image that matches your system. Some tools are unavailable on arm64, as listed at the end of this page.
{% endhint %}

To map a local directory into the container's /home/remnux/files directory, you could use a command like this, supplying the appropriate directory name:

```
docker run --rm -it -u remnux -v <local_directory>:/home/remnux/files remnux/remnux-distro:noble bash
```

The `--rm` parameter above directs Docker to create a transient container, which will stop running after you exit the shell. To keep the container active in the background even after you exit, don't supply `--rm`.

## SSH and Graphical Interface Access

To access the REMnux distro container using SSH, you can invoke it by mapping your system's TCP port 22 to the container's internal TCP port 22. One way to do this is to use the following command, which will open the SSH listener and run the container in the background.

To run the REMnux version built on top of Ubuntu 24.04 (Noble):

```
docker run -d -p 22:22 remnux/remnux-distro:noble
```

Once you've connected to your REMnux container using SSH, you can access the REMnux graphical interface by [tunneling the GUI through SSH](../tips/remnux-config-tips.md#gui-cloud-remnux).

## Tools Excluded from the Container

To minimize the container image size, the following tools are not included:

* **VS Code**: Access the container using VS Code's [Remote-SSH](https://code.visualstudio.com/docs/remote/ssh) extension from your host instead.
* **Wine and Wine-dependent tools**: scdbg, ssview, shellcode2exe-bat, and runsc.

To install these tools, run `remnux install --user remnux` in the container to upgrade to a full installation. Alternatively, selectively install packages using `apt update` followed by `apt install code`, `apt install scdbg`, etc.

## Tools Unavailable on ARM Systems

On arm64 systems, the container lacks the following tools, because REMnux supports them only on amd64:

* **binee**: Use speakeasy or qiling instead.
* **Bytehist**: No alternative identified.
* **edb**: Use gdb or radare2 instead.
* **js_unshroud**: No alternative identified.
* **Malcat Lite**: Use Ghidra or radare2 instead.
* **r2mcp**: No alternative identified.
* **RAR**: To extract RAR archives, use unrar or 7zz instead.
* **SpiderMonkey (Patched)**: Use js115 instead.
* **STPyV8**: No alternative identified.
* **thug**: Run thug on an amd64 system, for example in the remnux/thug container.
* **TrID**: Use `file` or Detect It Easy instead.

Some tools run with limits on arm64. Vivisect lacks its graphical interface, and peepdf-3 can't emulate JavaScript. Burp Suite's built-in browser doesn't run, and Ghidra can't open 7-Zip archives. To check any tool's availability and alternatives, look it up in [Discover the Tools](../discover-the-tools/examine+static+properties/).

For more details about Docker images available as part of the REMnux toolkit, see [Docker Images of Malware Analysis Tools](../run-tools-in-containers/remnux-containers.md).
