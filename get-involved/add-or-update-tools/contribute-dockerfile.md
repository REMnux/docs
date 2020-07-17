# Contribute a Dockerfile

Please contribute to the [REMnux collection of Docker images](../../run-tools-in-containers/remnux-containers.md) of malware analysis applications. You'll get a chance to experiment with [Docker](https://www.docker.com), become a master at setting up an application of your choice, and expand the set of tools that others can run for examining malicious software.

To get started, review:

1. [REMnux documentation section on Docker images.](../../run-tools-in-containers/remnux-containers.md)
2. [Docker documentation on Dockerfile creation.](https://docs.docker.com/engine/reference/builder/)
3. [Dockerfiles in the REMnux Docker repository on Github.](https://github.com/remnux/docker)
4. The details in this section below.

{% hint style="success" %}
Before creating the Dockerfile for the application you'd like to contribute to the REMnux toolkit, [reach out to Lenny Zeltser](https://zeltser.com/contact), the primary REMnux maintainer, to confirm that the application is a fit for REMnux.
{% endhint %}

## Creating a Dockerfile

A properly-formatted Dockerfile describes the steps necessary to build and configure your application inside a Docker container in a repeatable and unattended manner. To get a sense for the structure of such files, browse the [REMnux repository of Dockerfiles on Github](https://github.com/REMnux/docker/). To explain how to build such files, we'll use the [JSDetox Dockerfile](https://github.com/REMnux/docker/blob/master/jsdetox/Dockerfile) as an example.

The beginning of your Dockerfile should include comments that state which application is included in the image, who created the app and where it can be obtained in a traditional form. The comments should explain how the use of the image should run it. For instance:

```text
# This Docker image encapsulates the JSDetox malware analysis tool by @sven_t
# from http://www.relentless-coding.com/projects/jsdetox
#
# To run this image after installing Docker, use the following command:
# sudo docker run -d --rm --name jsdetox -p 3000:3000 remnux/jsdetox
# Then, connect to http://localhost:3000 using your web browser.
```

REMnux images typically use a minimal Docker image of Ubuntu 18.04 as a starting point, as designated by the `FROM` directive below. The `LABEL` directive specify meta data such as the maintainer and version of the Dockerfile:

```text
FROM ubuntu:18.04
LABEL maintainer="Lenny Zeltser (@lennyzeltser, www.zeltser.com)"
LABEL updated="1 May 2020"
```

The `USER` directive specifies the user inside the container that should perform the installation steps \("root"\). The `RUN` directive specifies the commands to run inside the container to install the software. Your Dockerfile file should include the `apt-get update` command, followed by `apt-get install -y` and a listing of the Ubuntu packages the application requires.The starting point for the image is a minimal Ubuntu installation, so assume that a given package is absent unless you explicitly install it:

```text
USER root
RUN apt-get update && apt-get install -y \
  git \
  ruby \
  ruby-dev \
  bundler \
  zlib1g-dev \
  build-essential && \
  rm -rf /var/lib/apt/lists/*
```

Note that the `RUN` command above links several commands together using `&&` and employs `\` to break this sequence of commands into multiple lines for readability. We're linking several commands like this to slightly minimize the size of the resulting Docker image file. This is also the reason why we include the `rm` command to get rid of the package listing.

The followng `RUN` directive sets up the non-root user creatively named "nonroot", so that commands and applications that don't require root provileges have a more restricted environment within which to run:

```text
RUN groupadd -r nonroot && \
  useradd -r -g nonroot -d /home/nonroot -s /sbin/nologin -c "Nonroot User" nonroot && \
  mkdir /home/nonroot && \
  chown -R nonroot:nonroot /home/nonroot
```

The next set of directives tells Docker to start running commands using the newly-set up "nonroot" user, defines the working directory to match that user's home directory and retrieves the code for the application we're installing \(JSDetox, in this case\):

```text
USER nonroot
WORKDIR /home/nonroot
RUN git clone https://github.com/svent/jsdetox.git
```

The following instructions will install the application using the `bundle install` command, according the JSDetox installation instructions. These steps need to run as "root" to have the ability to copy the application's files into protected locations:

```text
USER root
WORKDIR /home/nonroot/jsdetox
RUN sed "s/, '0.9.8'/, '0.12.3'/g" -i Gemfile
RUN bundle install
```

The final set of directives below tells Docker to switch back to using the "nonroot" user and sets the working directory to the location from which JSDetox should be launched. It also specifies which command Docker should run when this image is launched without any parameters:

```text
USER nonroot
EXPOSE 3000
WORKDIR /home/nonroot/jsdetox
CMD ./jsdetox -l $HOSTNAME 2>/dev/null
```

By default, JSDetox listens on localhost. To give us the opportunity to connect to JSDetox from outside of its container, the command above launches the tool with the `-l` parameter and specifies the $HOSTNAME varilable. This environment variable is automatically defined to match the hostname that Docker will assign when this container runs, which will allow JSDetox to listen on the network interface accessible from our underlying host.

## Building a Image from the Dockerfile

It’s difficult to create a Dockerfile, such as the one we reviewed above, in one step. Inevitably, some command will run in an unexpected manner, preventing the application from installing properly. Before documenting your steps in Dockerfile, consider launching the base Ubuntu container like this:

```text
docker run --rm -it ubuntu:18.04 bash
```

Then, manually type and write down the commands into the container's shell to install the desired application. Once you've validated that a specific sequence of commands works, start building a Dockerfile by adding your instructions one or two at a time to validate that they work as intended.

Once you've created a Dockerfile that contains the desired directives, go to the directory where the file is present and run the following command, where "image-name" is he name you'd like to assign to the image file you're building:

```text
docker build -t=image-name .
```

After Docker builds the image, you can run it using the following command to get a shell in the container where your application has been installed:

```text
docker run --rm -it image-name bash
```

Of course, "image-name" in the command above should correspond to the name you've assigned to the image. The `--rm` parameter directs Docker to automatically remove the container once it finishes running. This gets rid of any changes the application may have made to its local environment when it ran, but does not remove the cached image file that represents the app on your system. The `-it` parameter requests that Docker open an interactive session to the container so you can interact with it.

Once you have built and tested your Dockerfile, [share it with Lenny Zeltser](https://zeltser.com/contact), so he can review it and, if appropriate, add your contribution to the REMnux repository.

## Facilitating File System and Network Interactions

The container will be isolated from the host system: by default it will be able to communicate over the network in the outbound direction, but won't accept inbound traffic. Also, if the container is invoked with the `--rm` parameter, its contents will disappear after it stops running. When building the image, anticipate the user's need to communicate with the app inside the container over the network or to pass files in and out of the container.

### **Accessing Network Ports in the Container**

In the JSDetox example above, the application listens on TCP port 3000. In its default configuration, JSDetox listens on localhost, which would make its port inaccessible from outside its Docker container. This is why we launched JSDetox with the `-l $HOSTNAME` parameter. This directed the application to listen on the network interface that could be accessed from outside the container.

Unless the user explicitly requests access to the container's port when launching its image, no ports will be accessible from the underlying system. Fortunately, Docker allows us to use the `-p` parameter to specify that a specific port within the container should be accessible from outside the container. For example, to access JSDetox’ port 3000, the user needs to specify `-p 3000:3000`. This maps the container’s port 3000 to the underlying host’s port 3000, allowing the user to communicate with JSDetox by connecting to http://localhost:3000 using a web browser.

### **Sharing Files with the Container**

There is no need to share files with JSDetox inside the container by using the file system, because this application interacts with the user through the web browser. In contrast, some files expect the user to provide input or share output via the file system. Docker supports the `-v` parameter to share a directory between the underlying host and the container.

For example, let’s say we wanted to share a folder with the container running [Rekall](../../run-tools-in-containers/remnux-containers.md#rekall), which is available in the REMnux repository on Docker Hub. If the memory image file that you’d like to analyze is on your underlying host in the ~/files directory, you could share that directory with the Rekall container by specifying `-v ~/files:/home/nonroot/files` when running the application’s image:

```text
sudo docker run --rm -it -v ~/files:/home/nonroot/files remnux/rekall bash
```

This maps the local ~/files directory to the /home/nonroot/files directory inside the container. The Rekall image is built to run the user-designated command \(e.g., `bash`\) as the user "nonroot". To ensure that the non-root user has access to the underlying hosts ~/files directory, the user of the app will need to make that directory world-accessible \(i.e., `chmod a+xwr ~/files`\) before launching the container.

