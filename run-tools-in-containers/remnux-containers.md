# Docker Images of Malware Analysis Tools

The REMnux toolkit provides [Docker](https://www.docker.com) images of popular malware analysis tools that you can run on any compatible system even without installing the REMnux distro. These images reside in the [REMnux repository on Docker Hub](https://hub.docker.com/u/remnux), and are based on the files maintained in the [REMnux Github repository](https://github.com/REMnux/docker).

{% hint style="success" %}
In addition to the Docker images of individual tools, described below, you can run the [REMnux distro inside a pre-built Docker container](../install-distro/remnux-as-a-container.md).
{% endhint %}

Docker is installed as part of the REMnux distro. If you're planning to run REMnux Docker images on another system, you may need to [install Docker](https://docs.docker.com/get-docker/). The first time you run an [image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/) \(e.g., using the `docker run` command\), Docker will automatically download the image from Docker Hub, run it locally as an active [container](https://www.docker.com/resources/what-container). Your system will need to be connected to the internet to retrieve the image; afterwards, Docker will use a locally cached copy. You can use the `docker pull` command to update the cached version of the image. To update all local images from a Linux-like shell, run:

```text
docker images |cut -d' ' -f1 | grep -v REPOSITORY | xargs -I %s docker pull %s
```

The following Docker images of malware analysis tools are available as part of REMnux. If you have the expertise, consider adding to this collection by [contributing a Dockerfile](../get-involved/add-or-update-tools/contribute-dockerfile.md) to the REMnux toolkit.

## Thug Low-Interaction Honeyclient <a id="thug"></a>

[Thug](https://github.com/buffer/thug) is a low-interaction honeyclient for examining suspicious websites. This tool was created by Angelo Dell'Aera. It's licensed under [GNU General Public License \(GPL\) v2](https://github.com/buffer/thug/blob/master/LICENSE.txt). In addition to being available as a Docker image, [Thug is also installed](../discover-the-tools/explore+network+interactions/connecting.md#thug) as part of the REMnux distro.

One way to run Thug as a Docker image is to invoke it using the following command to open a shel in the container where you can run `thug` with the desired parameters, such as -F to enable file logging\).

```text
docker run --rm -it --entrypoint "/bin/bash" remnux/thug
```

The remnux/thug image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/thug).

## JSDetox JavaScript Analysis Tool <a id="jsdetox"></a>

[JSDetox](http://www.relentless-coding.com/projects/jsdetox) is a web-based tool for analyzing and deobfuscating JavaScript. It was created by [Sven Taute](https://twitter.com/sven_t) and is licensed under [GNU General Public License \(GPL\) v2](https://github.com/svent/jsdetox).

You can use the following command to launch the JSDetox Docker image, with the application listening localy on TCP port 3000. You can then connect to http://localhost:3000 using your web browser:

```text
docker run -d --rm --name jsdetox -p 3000:3000 remnux/jsdetox
```

To stop JSDetox, use  the command `docker stop jsdetox`.

The remnux/jsdetox image is hosted on [its Docker Hub page](https://hub.docker.com/r/remnux/jsdetox/).

## Rekall Memory Forensic and Incident Response Framework <a id="rekall"></a>

[Rekall](https://github.com/google/rekall) is a set of tools for extracting digital artifacts from memory and other aspects of a system when performing incident response. Its components were [written by multiple people](https://github.com/google/rekall/blob/master/AUTHORS.md), and are licensed under  [GNU General Public License \(GPL\) v2](https://github.com/google/rekall/blob/master/LICENSE.txt). 

To run Rekall, first create a directory where you'll store the files you plan to examine. Then, use a command like this to open a shell inside the container where you can run `rekall` and have your evidence directry mapped as `/home/nonroot/files` inside the container:

```text
docker run --rm -it -v <files_directory>:/home/nonroot/files remnux/rekall bash
```

The remnux/rekall image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/rekall).

## RetDec Retargetable Machine-Code Decompiler <a id="retdec"></a>

[RetDec](https://retdec.com) is a decompiler that supports a variety of file formats, include PE and ELF, and several 32 and 64-bit architectures. It was created by [Avast Software](https://www.avast.com), and is licensed under [MIT License](https://github.com/avast/retdec/blob/master/LICENSE) with [third-party components](https://github.com/avast/retdec/blob/master/LICENSE-THIRD-PARTY) that are distributed under their own licenses.

To run RetDec, create a directory where you'll store the files you plan to examine. Then,  open a shell inside the container where you can run RetDec commands and have your local directory mapped as `/tmp/files` inside the container:

```text
docker run -it --rm -v <files_directory>:/tmp/files remnux/retdec bash
```

The login credentials for the container are:

Username: `retdec`  
Password: `retdec`

{% hint style="info" %}
The commands provided by RetDec include start with the `retdec-` prefix and include retdec-decompiler.py, retdec-unpacker, and retdec-fileinfo.
{% endhint %}

The remnux/retdec image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/retdec).

## Radare2 Reverse-Engineering Framework <a id="radare2"></a>

[Radare2](https://www.radare.org/) is a reverse-engineering framework that includes a disassembler and analysis capabilities for a variety of executable formats and architectures. It's licensed under [GNU Lesser General Public License \(LGPL\) v3](https://github.com/radareorg/radare2/blob/master/COPYING).

To run Radare2, create a directory where you'll store the files you plan to examine. Then,  open a shell inside the container where you can run Radare2 commands and have your local directory mapped as `/home/nonroot/workdir` inside the container:

```text
docker run --rm -it --cap-drop=ALL --cap-add=SYS_PTRACE -v ~/workdir:/home/nonroot/workdir remnux/radare2
```

The remnux/radare2 image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/radare2).

