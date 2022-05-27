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

One way to run Thug as a Docker image is to invoke it using the following command to open a shel in the container where you can run `thug` with the desired parameters, such as -F to enable file logging).

```
docker run --rm -it --entrypoint "/bin/bash" remnux/thug
```

The password for the container's user `thug` is `thug`. The remnux/thug image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/thug).

## Binary Refinery <a href="#binaryrefinery" id="binaryrefinery"></a>

The [Binary Refinery](https://github.com/binref/refinery)™ is a collection of Python scripts that implement transformations of binary data such as compression and encryption. You can chain the tools as necessary to achieve your objective. This toolkit is authored by Jesko Hüttenhain and licensed under the [3-Clause BSD License](https://github.com/binref/refinery/blob/master/LICENSE).

To run Binary Refinery tools within the "remnux/binary-refinery" container, create a directory where you'll store your input files, e.g. \~/workdir. Then, use a command like this to launch the container and have your directory mapped as /home/nonroot/workdir inside the container:

```
docker run -it --rm -v ~/workdir:/home/nonroot/workdir remnux/binary-refinery
```

The binary-refinery Docker image is hosted in [the REMnux Docker Hub repository](https://hub.docker.com/repository/docker/remnux/binary-refinery).

For documentation about this toolkit, including the listing of its tools, see [https://binref.github.io](https://binref.github.io/) and [https://github.com/binref/refinery](https://github.com/binref/refinery).

## JSDetox JavaScript Analysis Tool <a href="#jsdetox" id="jsdetox"></a>

[JSDetox](http://www.relentless-coding.com/projects/jsdetox) is a browser-based tool for analyzing and deobfuscating JavaScript. It was created by [Sven Taute](https://twitter.com/sven\_t) and is licensed under [GNU General Public License (GPL) v2](https://github.com/svent/jsdetox).

You can use the following command to launch the JSDetox Docker image, with the application listening locally on TCP port 3000. You can then connect to http://localhost:3000 using your web browser:

```
docker run -d --rm --name jsdetox -p 3000:3000 remnux/jsdetox
```

To stop JSDetox, use  the command `docker stop jsdetox`. The remnux/jsdetox image is hosted on [its Docker Hub page](https://hub.docker.com/r/remnux/jsdetox/).

## de4js JavaScript Deobfuscator and Unpacker <a href="#de-4-js" id="de-4-js"></a>

[de4js](https://github.com/lelinhtinh/de4js) is a browser-based tool for deobfuscating and unpacking JavaScript. It was created by Zzbaivong and is licensed under [MIT License](https://github.com/lelinhtinh/de4js/blob/master/LICENSE). If you don't want to run de4js locally using the Docker image outlined below, you can use [the version hosted on its author's website](https://lelinhtinh.github.io/de4js/).

You can use the following command to launch the de4js Docker image, with the application listening locally on TCP port 4000. You can then connect to http://localhost:4000/de4js/ using your web browser:

```
 docker run -d --rm -p 4000:4000 -p 35729:35729 --name de4js remnux/de4js
```

{% hint style="warning" %}
It's important to remember the trailing slash as part of the de4js URL http://localhost:4000/de4js/.
{% endhint %}

To stop de4js, use  the command `docker stop de4js`. The remnux/de4js image is hosted on [its Docker Hub page](https://hub.docker.com/r/remnux/de4js/).

## Rekall Memory Forensic and Incident Response Framework <a href="#rekall" id="rekall"></a>

[Rekall](https://github.com/google/rekall) is a set of tools for extracting digital artifacts from memory and other aspects of a system when performing incident response. Its components were [written by multiple people](https://github.com/google/rekall/blob/master/AUTHORS.md), and are licensed under  [GNU General Public License (GPL) v2](https://github.com/google/rekall/blob/master/LICENSE.txt).&#x20;

To run Rekall, create a directory where you'll store the files you plan to examine. Then, use a command like this to open a shell inside the container where you can run `rekall` and have your evidence directry mapped as `/home/nonroot/files` inside the container:

```
docker run --rm -it -v <files_directory>:/home/nonroot/files remnux/rekall bash
```

The password for the container's user `nonroot` is `nonroot`. The remnux/rekall image is hosted on [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/rekall).

## RetDec Retargetable Machine-Code Decompiler <a href="#retdec" id="retdec"></a>

[RetDec](https://retdec.com) is a decompiler that supports a variety of file formats, include PE and ELF, and several 32 and 64-bit architectures. It was created by [Avast Software](https://www.avast.com), and is licensed under [MIT License](https://github.com/avast/retdec/blob/master/LICENSE) with [third-party components](https://github.com/avast/retdec/blob/master/LICENSE-THIRD-PARTY) that are distributed under their own licenses.

To run RetDec, create a directory where you'll store the files you plan to examine. Then,  open a shell inside the container where you can run RetDec commands and have your local directory mapped as `/tmp/files` inside the container:

```
docker run -it --rm -v <files_directory>:/tmp/files remnux/retdec bash
```

The password for the container's user `retdec` is `retdec`. The remnux/retdec image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/retdec).

{% hint style="info" %}
The commands provided by RetDec include start with the `retdec-` prefix and include retdec-decompiler.py, retdec-unpacker, and retdec-fileinfo.
{% endhint %}

## Rizin Reverse-Engineering Framework <a href="#rizin" id="rizin"></a>

[Rizin](https://rizin.re) is a reverse-engineering framework that includes a disassembler and analysis capabilities for a variety of executable formats and architectures. It's licensed under [GNU Lesser General Public License (LGPL) v3](https://github.com/rizinorg/rizin/blob/master/COPYING). This is a [fork of the Radare2 project](https://rizin.re/posts/faq/#why-did-you-fork-radare2).

To run Rizin, create a directory where you'll store the files you plan to examine. Then,  open a shell inside the container where you can run Rizin commands (`rizin` and others that start with `rz-`) and have your local directory mapped as `/home/nonroot/workdir` inside the container:

```
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/rizin
```

If you're planning to peform kernel-mode debugging, process tracing, or syscall tracing inside the container, then supply the parameters `--cap-drop=ALL --cap-add=SYS_PTRACE` when launching it.

The password for the container's user `nonroot` is `nonroot`. The remnux/rizin image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/rizin).

## Radare2 Reverse-Engineering Framework <a href="#radare2" id="radare2"></a>

[Radare2](https://www.radare.org/) is a reverse-engineering framework that includes a disassembler and analysis capabilities for a variety of executable formats and architectures. It's licensed under [GNU Lesser General Public License (LGPL) v3](https://github.com/radareorg/radare2/blob/master/COPYING).

To run Radare2, create a directory where you'll store the files you plan to examine. Then,  open a shell inside the container where you can run Radare2 commands and have your local directory mapped as `/home/nonroot/workdir` inside the container:

```
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/radare2
```

If you're planning to peform kernel-mode debugging, process tracing, or syscall tracing inside the container, then supply the parameters `--cap-drop=ALL --cap-add=SYS_PTRACE` when launching it.

The password for the container's user `nonroot` is `nonroot`. The remnux/radare2 image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/radare2).

## Viper Binary Analysis and Management Framework

[Viper](https://github.com/viper-framework/viper) is a framework for analyzing and managing your collection of malware samples. It was created by [Claudio Guarnieri](https://nex.sx/) and is licensed under [BSD 3-Clause License](https://github.com/viper-framework/viper/blob/master/LICENSE).

To run Viper, create a directory where you'll store your malware samples. Then, use a command like this to open a shell inside the container where you can run `viper` and have your samples directory mapped as `/home/nonroot/workdir` inside the container:

```
docker run -it --rm -v ~/workdir:/home/nonroot/workdir remnux/viper
```

To run the "clamav" Viper plugin, the clamav-daemon must be running in the container. You can enable it by running the following command in the container:

```
sudo service clamav-daemon start
```

The password for the container's user `nonroot` is `nonroot`. The remnux/viper image is hosted on its [its Docker Hub page](https://hub.docker.com/repository/docker/remnux/viper/).

## Ciphey Automatic Decoder and Decrypter <a href="#ciphey" id="ciphey"></a>

[Ciphey](https://github.com/Ciphey/Ciphey) is designed to automatically recognize and decode/decrypt common encoding and encryption techniques, as [outlined in its documentation](https://docs.ciphey.online/en/latest/ciphers.html). It was created by [Brandon Skerritt](https://twitter.com/brandon\_skerrit) and is licensed under [MIT License](https://github.com/Ciphey/Ciphey/blob/master/license). According the author, the tool uses "natural language processing & artifical intelligence, along with some common sense."

To run Ciphey using this Docker container, create a directory (e.g. \~/workdir) where you'll store your input file (e.g., input.txt). Then, use a command like this to run Ciphey and have your directory mapped into the container:

```
docker run -it --rm -v ~/workdir:/home/nonroot/workdir remnux/ciphey -f input.txt 
```

Or for a text input on the command-line run:

```
docker run -it --rm remnux/ciphey "=MXazlHbh5WQgUmchdHbh1EIy9mZgQXarx2bvRFI4VnbpxEIBBiO4VnbNVkU"
```

The [remnux/ciphey](https://hub.docker.com/repository/docker/remnux/ciphey/) image is hosted on its  [Docker Hub page](https://hub.docker.com/repository/docker/remnux/ciphey).
