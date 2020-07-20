# Run REMnux in a Container

You can run the REMnux distro in a [Docker](https://www.docker.com) container by using a prebuilt image, hosted in [the REMnux repository on Docker Hub](https://hub.docker.com/repository/docker/remnux/remnux-distro).

If you have Docker installed, you can start the REMnux distro container in interactive mode using the following command, which will automatically download the distro image \(approximately 5 GB\) if your system doesn't already have it:

```text
docker run --rm -it remnux/remnux-distro /bin/bash
```

To map a local directory into the container's /home/remnux/files directory, you could use a command lile this by supplying the appropriate directory name like this:

```text
docker run --rm -it -v <local_directory>:/home/remnux/files remnux/remnux-distro /bin/bash
```

If you'd like to access the REMnux distro container using SSH, you can invoke it by mapping your system's TCP port 22 to the container's internal TCP port 22. One way to do this is to use the following command, which will open the SSH listener and run the container in the background:

```text
docker run -p 22:22 remnux/remnux-distro
```

If you're connecting to your REMnux container, you can access the REMnux graphical interface by [tunneling the GUI through SSH](../tips/remnux-config-tips.md#gui-cloud-remnux).

{% hint style="info" %}
If you're planning to use [Cutter](../discover-the-tools/statically+analyze+code/general.md#cutter) inside the container, you'll need to include the `--privileged` parameter when invoking the REMnux distro image in Docker.
{% endhint %}

For more details about Docker images available as part of the REMnux toolkit, see [Docker Images of Malware Analysis Tools](../run-tools-in-containers/remnux-containers.md).

