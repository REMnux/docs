# Run REMnux as a Container

You can run the REMnux distro as a [Docker](https://www.docker.com) container by using a prebuilt image, hosted in [the REMnux repository on Docker Hub](https://hub.docker.com/repository/docker/remnux/remnux-distro).

## Local Interactive Shell

If you have Docker installed, you can start the REMnux distro container in interactive mode, as explained below. The following command will automatically download the distro image \(approximately 4 GB\) if your system doesn't already have it.

To run the REMnux version built on top of Ununtu 18.04 \(bionic\), use the following command:

```text
docker run --rm -it -u remnux remnux/remnux-distro:bionic bash
```

To run the REMnux version built on top of Ununtu 20.04 \(focal\), use the following command instead:

```text
docker run --rm -it -u remnux remnux/remnux-distro:focal bash
```

To map a local directory into the container's /home/remnux/files directory, you could use a command lile this by supplying the appropriate directory name like this:

```text
docker run --rm -it -u remnux -v <local_directory>:/home/remnux/files remnux/remnux-distro bash
```

The `--rm` parameter above directs Docker to create a transient container, which will stop running after you exit the shell. To keep the container active in the background even after you exit, don't supply `--rm`. 

## SSH and Graphical Interface Access

To access the REMnux distro container using SSH, you can invoke it by mapping your system's TCP port 22 to the container's internal TCP port 22. One way to do this is to use the following command, which will open the SSH listener and run the container in the background.

To run the REMnux version built on top of Ununtu 18.04 \(bionic\), use:

```text
docker run -d -p 22:22 remnux/remnux-distro:bionic
```

To run the REMnux version built on top of Ununtu 20.04 \(focal\), use:

```text
docker run -d -p 22:22 remnux/remnux-distro:focal
```

Once you connected to your REMnux container using SSH, you can access the REMnux graphical interface by [tunneling the GUI through SSH](../tips/remnux-config-tips.md#gui-cloud-remnux).

For more details about Docker images available as part of the REMnux toolkit, see [Docker Images of Malware Analysis Tools](../run-tools-in-containers/remnux-containers.md).

