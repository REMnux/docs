# Docker Images of Malware Analysis Tools

The REMnux toolkit provides [Docker](https://www.docker.com) images of popular malware analysis tools that you can run on any compatible system even without installing the REMnux distro. These images reside in the [REMnux repository on Docker Hub](https://hub.docker.com/u/remnux), and are based on the configuration files maintained in the [REMnux Github repository](https://github.com/REMnux/docker).

Docker is installed as part of the REMnux distro. If you're planning to run REMnux Docker images on another system, you may need to [install Docker](https://docs.docker.com/get-docker/). The first time you run an [image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/) \(e.g., using the `docker run` command\), Docker will automatically download the image from Docker Hub, run it locally as an active [container](https://www.docker.com/resources/what-container). Your system will need to be connected to the internet to retrieve the image; afterwards, Docker will use a locally cached copy. You can use the `docker pull` command to update the cached version of the image. To update all local images from a Linux-like shell, run:

```text
docker images |cut -d' ' -f1 | grep -v REPOSITORY | xargs -I %s docker pull %s
```

The following Docker images of malware analysis tools are available as part of REMnux. If you have the expertise, consider adding to this collection by [contributing a Dockerfile](../get-involved/add-or-update-tools/contribute-a-dockerfile.md) to the REMnux toolkit.

## Thug Low-Interaction Honeyclient <a id="thug"></a>

[Thug](https://github.com/buffer/thug) is a low-interaction honeyclient for examining suspicious websites. This tool was created by Angelo Dell'Aera. It's licensed under [GNU General Public License \(GPL\) v2](https://github.com/buffer/thug/blob/master/LICENSE.txt). In addition to being available as a Docker image, [Thug is also installed](../discover-the-tools/explore+network+interactions/connecting.md#thug) as part of the REMnux distro.

One way to run Thug as a Docker image is to invoke it using the following command to open a shel in the container where you can run `thug` with the desired parameters, such as -F to enable file logging\).

```text
docker run --rm -it --entrypoint "/bin/bash" remnux/thug
```

For more details and execution options see the [remnux/thug page on Docker Hub](https://github.com/REMnux/docker/tree/master/thug).

## JSDetox JavaScript Analysis Tool <a id="jsdetox"></a>

[JSDetox](http://www.relentless-coding.com/projects/jsdetox) is a web-based tool for analyzing and deobfuscating JavaScript. It was created by [Sven Taute](https://twitter.com/sven_t) and is licensed under [GNU General Public License \(GPL\) v2](https://github.com/svent/jsdetox).

You can use the following command to launch the JSDetox Docker image, with the application listening localy on TCP port 3000. You can then connect to http://localhost:3000 using your web browser:

```text
docker run -d --rm --name jsdetox -p 3000:3000 remnux/jsdetox
```

To stop JSDetox, use  the command `docker stop jsdetox`. For more details, see the [remnux/jsdetox page on Docker Hub](https://hub.docker.com/r/remnux/jsdetox/).

## Rekall Memory Forensic and Incident Response Framework <a id="rekall"></a>

[Rekall](https://github.com/google/rekall) is a set of tools for extracting digital artifacts from memory and other aspects of a system when performing incident response. Its components were [written by multiple people](https://github.com/google/rekall/blob/master/AUTHORS.md), and are licensed under  [GNU General Public License \(GPL\) v2](https://github.com/google/rekall/blob/master/LICENSE.txt). 

To run Rekall, first created a directory where you'll store the forensic evidence and make it world-accessible \(e.g, `chmod a+xwr`\). Then, use a command like this to open a shell inside the Docker container where you can run `rekall` and have your evidence directry mapped as `/home/nonroot/files` inside the container:

```text
docker run --rm -it -v <evidence_directory>:/home/nonroot/files remnux/rekall bash
```

For more dtails, see the [remnux/rekall page on Docker Hub](https://hub.docker.com/repository/docker/remnux/rekall).

## More to come...

