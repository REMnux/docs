# Contribute a Dockerfile

The following steps describe how you can create a Dockerfile for a malware analysis tool and contribute it to the [REMnux collection of Docker images](../../run-tools-in-containers/remnux-containers.md).

To get started, review:

1. [REMnux documentation on Docker images.](../../run-tools-in-containers/remnux-containers.md)
2. [Docker documentation on Dockerfile creation.](https://docs.docker.com/engine/reference/builder/)
3. [Dockerfiles in the REMnux Docker repository on GitHub.](https://github.com/remnux/docker)
4. The details below.

{% hint style="info" %}
Before starting this work, consider [reaching out to Lenny Zeltser](https://zeltser.com/contact) to confirm that it makes sense to include the tool as part of the REMnux collection of Docker images.
{% endhint %}

## 1. Install Git and Docker

Follow the steps appropriate for your operating system to install [Git](https://git-scm.com) and [Docker](https://www.docker.com/products/docker-desktop) on your system.

Clone the REMnux/docker repository, which contains the existing Dockerfiles:

```text
git clone https://github.com/REMnux/docker.git
```

Browse the existing Dockerfiles in the repository to see how other tools are packaged. Instead of creating a file from scratch, consider using an existing Dockerfile as a starting point for your own.

## 2. Create the Dockerfile

Create a subdirectory named after your tool in the local copy of the repository, and add a `Dockerfile` inside it. A REMnux Dockerfile follows a consistent structure. The sections below explain each part, using the [radare2 Dockerfile](https://github.com/REMnux/docker/blob/master/radare2/Dockerfile) as the primary example.

### Header Comments

Begin the file with comments that state the tool's name, website, description, author, license, and usage instructions:

```text
# Name: radare2
# Website: https://www.radare.org/n/radare2.html
# Description: Examine binary files, including disassembling and debugging.
# Category: Dynamically Reverse-Engineer Code: General
# Author: https://github.com/radareorg/radare2/blob/master/AUTHORS.md
# License: GNU Lesser General Public License (LGPL) v3: https://github.com/radareorg/radare2/blob/master/COPYING
# Notes: r2, rasm2, rabin2, rahash2, rafind2, r2agent
#
# To run this image after installing Docker, use the command below, replacing
# "~/workdir" with the path to your working directory on the underlying host.
# Before running the docker, create ~/workdir on your host.
#
# docker run --rm -it --cap-drop=ALL --cap-add=SYS_PTRACE -v ~/workdir:/home/nonroot/workdir remnux/radare2
#
# Then run "r2" or other Radare2 commands inside the container.
```

### Base Image and Labels

Use a `FROM` directive to specify the base image, followed by `LABEL` directives for maintainer information and the date of the last update:

```text
FROM ubuntu:20.04
LABEL maintainer="Lenny Zeltser (@lennyzeltser, www.zeltser.com)"
LABEL updated="13 Apr 2022"
LABEL updated_by="Corey Forman"
```

{% hint style="success" %}
New Dockerfiles should use a current Ubuntu LTS base image such as `ubuntu:24.04`. Some existing images in the repository use older versions.
{% endhint %}

### Locale Settings

Set the locale environment variables so that tools don't encounter encoding issues:

```text
ENV LANG C.UTF-8
ENV LANGUAGE C.UTF-8
ENV LC_ALL C.UTF-8
```

### Build Arguments

Use `ARG` to define version numbers as build-time variables. This makes it easy to update the tool version later without changing multiple lines:

```text
ARG R2VER=5.6.6
```

### Package Installation

Install the Ubuntu packages your tool requires using `apt-get`. Chain commands with `&&` and clean up the package cache in the same `RUN` layer to minimize the image size. The `\` character breaks the package list across multiple lines for readability. Assume that a given package is absent unless you explicitly install it, since the base image is a minimal Ubuntu installation:

```text
USER root
RUN apt-get update && apt-get install -y \
  sudo \
  wget \
  git && \
  rm -rf /var/lib/apt/lists/*
```

### Non-Root User Creation

Create a non-root user so that the tool runs with restricted privileges. The following block creates the user, sets up a home directory and working directory, and grants passwordless sudo access:

```text
RUN groupadd -r nonroot && \
  useradd -m -d /home/nonroot -g nonroot -s /usr/sbin/nologin -c "Nonroot User" nonroot && \
  mkdir -p /home/nonroot/workdir && \
  chown -R nonroot:nonroot /home/nonroot && \
  usermod -a -G sudo nonroot && echo 'nonroot:nonroot' | chpasswd && \
  echo "nonroot ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/nonroot
```

### Application Installation

The installation steps vary by tool. The radare2 Dockerfile downloads a `.deb` package from a GitHub release and installs it using `dpkg`. The `ARG` variable defined earlier keeps the version number in one place:

```text
RUN wget -O /tmp/radare2_${R2VER}_amd64.deb https://github.com/radareorg/radare2/releases/download/${R2VER}/radare2_${R2VER}_amd64.deb && \
  dpkg -i /tmp/radare2_${R2VER}_amd64.deb && \
  r2pm init && \
  r2pm update && \
  rm /tmp/radare2_${R2VER}_amd64.deb
```

### Final Directives

The closing directives switch to the non-root user, set the working directory, declare a volume for file sharing, expose network ports, and specify the default command:

```text
USER nonroot
ENV HOME /home/nonroot
WORKDIR /home/nonroot/workdir
VOLUME ["/home/nonroot/workdir"]
EXPOSE 8080
CMD ["/bin/bash"]
```

{% hint style="info" %}
`CMD` specifies a default command that can be overridden when the user launches the container. `ENTRYPOINT` specifies a command that always runs, with any arguments passed at launch appended to it. For example, the [thug Dockerfile](https://github.com/REMnux/docker/blob/master/thug/Dockerfile) uses `ENTRYPOINT ["thug"]` so users can pass URLs directly: `docker run --rm remnux/thug http://example.com`. Most REMnux images use `CMD ["/bin/bash"]` to provide an interactive shell by default.
{% endhint %}

{% hint style="success" %}
Simple Python tools can use a `python:3-slim` base image instead of Ubuntu. For an example, see the [binary-refinery Dockerfile](https://github.com/REMnux/docker/blob/master/binary-refinery/Dockerfile), which installs the tool using `pip` directly.
{% endhint %}

## 3. Build and Test the Image

It's difficult to create a working Dockerfile in one step. When developing your Dockerfile, consider launching a base container interactively to figure out the installation commands:

```text
docker run --rm -it ubuntu:24.04 bash
```

Manually type and test each installation command inside the container's shell. Once you've validated that a specific sequence of commands works, transcribe them into your Dockerfile.

{% hint style="success" %}
This prototyping workflow saves time: launch the base container, figure out the steps interactively, then write them into the Dockerfile one or two directives at a time.
{% endhint %}

Once your Dockerfile is ready, go to the directory where it resides and build the image, replacing "image-name" with the name you'd like to assign:

```text
docker build -t image-name .
```

After Docker builds the image, run it to verify that the tool works:

```text
docker run --rm -it image-name bash
```

Test the following inside the container:

* The tool runs and produces expected output.
* The non-root user is active (check with `whoami`).
* Volume mounting works: run with `-v ~/workdir:/home/nonroot/workdir` and verify files are accessible.

## 4. Handle File and Network Interactions

The container is isolated from the host system: by default it can communicate over the network in the outbound direction, but won't accept inbound traffic. If the container is invoked with the `--rm` parameter, its contents disappear after it stops running. When building the image, anticipate the user's need to communicate with the application inside the container over the network or to pass files in and out of the container.

### Accessing Network Ports in the Container

If the tool listens on a network port, the user must explicitly expose it when launching the container using the `-p` parameter. For example, radare2 includes `r2agent`, which provides a web interface on port 8080. To access this from outside the container, the user specifies `-p 8080:8080`:

```text
docker run --rm -it -p 8080:8080 remnux/radare2
```

This maps the container's port 8080 to the underlying host's port 8080, allowing the user to connect by browsing to `http://localhost:8080`. Use the `EXPOSE` directive in the Dockerfile to document which ports the application uses, and include the `-p` flag in the usage instructions in the header comments.

### Sharing Files with the Container

Some tools expect the user to provide input or retrieve output via the file system. Docker supports the `-v` parameter to share a directory between the underlying host and the container. For example, to share a working directory with the radare2 container:

```text
docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/radare2
```

This maps the local `~/workdir` directory to `/home/nonroot/workdir` inside the container. Use the `VOLUME` directive in the Dockerfile to declare the expected mount point. To ensure the non-root user inside the container has access to the shared directory, the user may need to make it world-accessible (`chmod a+xwr ~/workdir`) before launching the container.

## 5. Create a Pull Request

Once you have a working, tested Dockerfile in the local copy of the REMnux/docker repository, [create a GitHub pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for that repo, so your Dockerfile may be considered for inclusion in the REMnux collection. Your pull request should include a directory named after the tool, containing the Dockerfile.

If the pull request isn't working, consider submitting the file to Lenny Zeltser [by email](https://zeltser.com/contact).

{% hint style="info" %}
After accepting the pull request, the REMnux maintainer handles building and publishing the Docker image to [Docker Hub](https://hub.docker.com/u/remnux). You don't need to push the image yourself.
{% endhint %}
