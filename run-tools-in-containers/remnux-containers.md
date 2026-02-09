# Docker Images of Malware Analysis Tools

The REMnux toolkit provides [Docker](https://www.docker.com) images of popular malware analysis tools that you can run on any compatible system even without installing the REMnux distro. These images reside in the [REMnux repository on Docker Hub](https://hub.docker.com/u/remnux), and are based on the files maintained in the [REMnux Github repository](https://github.com/REMnux/docker).

{% hint style="success" %}
In addition to the Docker images of individual tools, described below, you can run the [REMnux distro inside a pre-built Docker container](../install-distro/remnux-as-a-container.md).
{% endhint %}

Docker is installed as part of the REMnux distro. If you're planning to run REMnux Docker images on another system, you may need to [install Docker](https://docs.docker.com/get-docker/). The first time you run an [image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/) (e.g., using the `docker run` command), Docker will automatically download the image from Docker Hub, run it locally as an active [container](https://www.docker.com/resources/what-container). Your system will need to be connected to the internet to retrieve the image; afterwards, Docker will use a locally cached copy. You can use the `docker pull` command to update the cached version of the image. To update all local images from a Linux-like shell, run:

```
docker images |cut -d' ' -f1 | grep -v REPOSITORY | xargs -I %s docker pull %s
```

The following Docker images of malware analysis tools are available as part of REMnux. If you have the expertise, consider adding to this collection by [contributing a Dockerfile](../get-involved/add-or-update-tools/contribute-dockerfile.md) to the REMnux toolkit.

## Thug Low-Interaction Honeyclient <a href="#thug" id="thug"></a>

[Thug](https://github.com/buffer/thug) is a low-interaction honeyclient for examining suspicious websites. This tool was created by Angelo Dell'Aera. It's licensed under [GNU General Public License (GPL) v2](https://github.com/buffer/thug/blob/master/LICENSE.txt). In addition to being available as a Docker image, [Thug is also installed](../discover-the-tools/explore+network+interactions/connecting.md#thug) as part of the REMnux distro.

One way to run Thug as a Docker image is to invoke it using the following command to open a shell in the container where you can run `thug` with the desired parameters, such as -F to enable file logging).

```
docker run --rm -it --entrypoint "/bin/bash" remnux/thug
```

The password for the container's user `thug` is `thug`. The remnux/thug image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/thug).

## Binary Refinery <a href="#binaryrefinery" id="binaryrefinery"></a>

The [Binary Refinery](https://github.com/binref/refinery)™ is a collection of Python scripts that implement transformations of binary data such as compression and encryption. You can chain the tools as necessary to achieve your objective. This toolkit is authored by Jesko Hüttenhain and licensed under the [3-Clause BSD License](https://github.com/binref/refinery/blob/master/LICENSE).

To run Binary Refinery tools within the "remnux/binary-refinery" container, create a directory where you'll store your input files, e.g. \~/workdir. Then, use a command like this to launch the container and have your directory mapped as /home/nonroot/workdir inside the container:

```
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/binary-refinery
```

The binary-refinery Docker image is hosted in [the REMnux Docker Hub repository](https://hub.docker.com/repository/docker/remnux/binary-refinery).

For documentation about this toolkit, including the listing of its tools, see [https://binref.github.io](https://binref.github.io/) and [https://github.com/binref/refinery](https://github.com/binref/refinery).

## RetDec Retargetable Machine-Code Decompiler <a href="#retdec" id="retdec"></a>

[RetDec](https://github.com/avast/retdec) is a decompiler that supports a variety of file formats, including PE and ELF, and several 32 and 64-bit architectures. It was created by [Avast Software](https://www.avast.com), and is licensed under [MIT License](https://github.com/avast/retdec/blob/master/LICENSE) with [third-party components](https://github.com/avast/retdec/blob/master/LICENSE-THIRD-PARTY) that are distributed under their own licenses.

To run RetDec, create a directory where you'll store the files you plan to examine. Then, open a shell inside the container where you can run RetDec commands and have your local directory mapped as `/home/retdec/workdir` inside the container:

```
docker run --rm -it -v ~/workdir:/home/retdec/workdir remnux/retdec
```

The password for the container's user `retdec` is `retdec`. The remnux/retdec image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/retdec).

{% hint style="info" %}
The commands provided by RetDec start with the `retdec-` prefix and include retdec-decompiler, retdec-unpacker, and retdec-fileinfo.
{% endhint %}

## Rizin Reverse-Engineering Framework <a href="#rizin" id="rizin"></a>

[Rizin](https://rizin.re) is a reverse-engineering framework that includes a disassembler and analysis capabilities for a variety of executable formats and architectures. It's licensed under [GNU Lesser General Public License (LGPL) v3](https://github.com/rizinorg/rizin/blob/master/COPYING). This is a [fork of the Radare2 project](https://rizin.re/posts/faq/#why-did-you-fork-radare2).

To run Rizin, create a directory where you'll store the files you plan to examine. Then, open a shell inside the container where you can run Rizin commands (`rizin` and others that start with `rz-`) and have your local directory mapped as `/home/nonroot/workdir` inside the container:

```
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/rizin
```

If you're planning to perform kernel-mode debugging, process tracing, or syscall tracing inside the container, then supply the parameters `--cap-drop=ALL --cap-add=SYS_PTRACE` when launching it.

The password for the container's user `nonroot` is `nonroot`. The remnux/rizin image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/rizin).

## Radare2 Reverse-Engineering Framework <a href="#radare2" id="radare2"></a>

[Radare2](https://www.radare.org/) is a reverse-engineering framework that includes a disassembler and analysis capabilities for a variety of executable formats and architectures. It's licensed under [GNU Lesser General Public License (LGPL) v3](https://github.com/radareorg/radare2/blob/master/COPYING).

To run Radare2, create a directory where you'll store the files you plan to examine. Then, open a shell inside the container where you can run Radare2 commands and have your local directory mapped as `/home/nonroot/workdir` inside the container:

```
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/radare2
```

If you're planning to perform kernel-mode debugging, process tracing, or syscall tracing inside the container, then supply the parameters `--cap-drop=ALL --cap-add=SYS_PTRACE` when launching it.

The password for the container's user `nonroot` is `nonroot`. The remnux/radare2 image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/radare2).
