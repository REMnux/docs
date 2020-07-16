# Docker Images of Malware Analysis Tools

The REMnux toolkit provides [Docker](https://www.docker.com) images of popular malware analysis tools that you can run on any compatible system even without installing the REMnux distro. These images reside in the [REMnux repository on Docker Hub](https://hub.docker.com/u/remnux), and are based on the configuration files maintained in the [REMnux Github repository](https://github.com/REMnux/docker).

Docker is installed as part of the REMnux distro. If you're planning to run REMnux Docker images on another system, you may need to [install Docker](https://docs.docker.com/get-docker/). The first time you run an [image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/) \(e.g., using the `docker run` command\), Docker will automatically download the image from Docker Hub, run it locally as an active [container](https://www.docker.com/resources/what-container). Your system will need to be connected to the internet to retrieve the image; afterwards, Docker will use a locally cached copy. You can use the `docker pull` command to update the cached version of the image. To update all local images from a Linux-like shell, run:

```text
docker images |cut -d' ' -f1 | grep -v REPOSITORY | xargs -I %s docker pull %s
```

The following Docker images of malware analysis tools are available as part of REMnux. If you have the expertise, consider adding to this collection by [contributing a Dockerfile](../get-involved/add-or-update-tools/contribute-a-dockerfile.md) to the REMnux toolkit.

## Thug Low-Interaction Honeyclient <a id="thug"></a>

[Thug](https://github.com/buffer/thug) is a low-interaction honeyclient for examining suspicious website using this low-interaction honeyclient. This tool was created by Angelo Dell'Aera. It's licensed under [GNU General Public License \(GPL\) v2](https://github.com/buffer/thug/blob/master/LICENSE.txt). In addition to being available as a Docker image, [Thug is also installed](../discover-the-tools/explore+network+interactions/connecting.md#thug) as part of the REMnux distro.

One way to run Thug as a Docker image is to invoke it using the following command. It will enter you into the docker where you can run `thug` with the desired parameters, such as -F to enable file logging\).

```text
docker run --rm -it --entrypoint "/bin/bash" remnux/thug
```

For more details and execution options see the [remnux/thug page on Docker Hub](https://github.com/REMnux/docker/tree/master/thug).

## More to come...

