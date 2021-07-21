# Contribute a Debian Package

The following steps describe how you can build and locally test a Debian-based package for a new tool, in case you'd like to contribute it to REMnux.

{% hint style="info" %}
Before starting this work, consider [reaching out to Lenny Zeltser](https://zeltser.com/contact) to confirm that it makes sense to include the tool as part of REMnux. Also, become familiar with the way REMnux uses [custom Debian packages](../../behind-the-scenes/technologies/debian-packages.md) to install tools when practical.
{% endhint %}

## 1. Set Up Your Environment

Start with a system based on Ubuntu and install the packages you'll need to build your custom package:

```text
sudo apt install -y debhelper python-all python-setuptools devscripts quilt ant autotools-dev software-properties-common git pbuilder ubuntu-dev-tools apt-file dh-make bzr-builddeb
```

Next, initialize [pbuilder](https://wiki.ubuntu.com/PbuilderHowto), which is the tool you'll use to build your package locally in a way that mimcs how Launchpad will build it. This helps make sure that once it's uploaded to Launchpad it will \(probably\) build there successfully:

```text
sudo pbuilder-dist bionic create
```

The command above prepares your pbuilder environment for building packages for Ubuntu 18.04, which is code-named "bionic."

Define the following shell variables, possibly by adding these definitions to your ~/.bashrc file, adjusting the code name of the distribution if building packages for Ubuntu that's not version 18.04 \(bionic\):

```text
export DEBFULLNAME="REMnux Distribution"
export DEBEMAIL="distro@remnux.org"
export DISTRIBUTION=bionic
```

{% hint style="success" %}
If you use your pbuilder environment later, its APT package listing will become outdated. To update the packages, run the following command:

```text
sudo pbuilder-dist bionic update
```
{% endhint %}

## 2. Create the Skeleton for the Package

The source files for the custom REMnux packages that have already been built are in the REMnux/distro repository on GitHub in the "ppasrc" subdirectory. Start by cloning that repo, then go to that subdirectory:

```text
git clone https://github.com/REMnux/distro.git
cd distro/ppasrc
```

This will make it easier for you to submit your new package files via a pull request to that repository, and it will offer a set of examples you can review when creating the new package.

Create a subdirectory that matches the name of your tool, then create a subdirectory there that includes the tool's name and version number like this:

```text
mkdir packagename
cd packagename
mkdir packagename-0.1.1
cd packagename-0.1.1
```

Place source code of the tool you're packaging into the current directory, then generate the set of file that you'll need to build the package and remove some unnecessary ones:

```text
	dh_make --single --native
	cd debian
	rm -f *.ex *.EX README*
```

The files that describe how the package should be built are in the "debian" subdirectory. 

## 3. Generate the Package

Edit several files in the "debian" subdirectory:

* `changelog` should say "focal" instead of "unstable" \(assuming "bionic" is the code name of the Ubuntu version for which you're building the package; adjust the package version number if necessary.
* `control` should specify "utils" as the Section; in that file, add the tool's Homepage, description, and specify Build-Depends \(which Debian packages are needed to build this one?\) and Depends \(which packages does it need to run?\).
* `install` should list the source and destination paths of any files that should be copied as part of the installation, one set per line.
* `copyright` should include the appropriate copyright and licensing details.
* `rules` might need some changes as well, based on what steps need to be taken to build the tool from its source code; the build process can automatically figure this out, so don't tinker with this file unless the build fails.

Now, attempt to build the package locally using your current environment:

```text
debuild -uc -us
```

The command line parameters above direct `debuild` not to sign the generated package, since you don't have the REMnux private key. The command will follow the configuration directives in the "debian" subdirectory and \(if it succeeds\) generate a Debian package file with the .deb extension as well as several files that describe how Launchpad can built such a .deb file on its own.

In theory, you could distribute the .deb file on your own and install it using APT, perhaps from a local file system. However, Launchpad doesn't accept prebuilt files like this. It needs to build its own .deb files using the other files that `debuild` generated.

## 4. Test the Build Process using pbuilder

Even if you were able to build the package on your system using your local environment, it might fail to build on Launchpad. One of these reasons is that Launchpad imposes several restrictions on the build environment, including the lack of any internet access. Therefore, if the building process downloaded dependencies, the downloads will fail on Launchpad, causing the build to fail as well.

To mimic the build environment on Launchpad, go to the directory where the generated files reside \(e.g., "packagename"\) and run:

```text
pbuilder-dist focal amd64 build packagename_0.1.1.dsc
```

Adjust the name of the .dsc file, which was fenerated by `debuild` in the previous step to match the name of your file. If necessary, change "bionic" to match the code name of the Ubuntu version for which you're building the package.

## 5. Create a Pull Request

Once you have a working, tested set of files for building the Debian package in the local copy of the REMnux/distro repoistory, [create a GitHub pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) for that repo, so the package may be considered for inclusion in the REMnux distro. If the pull request isn't working, consider sharing the files generated by `debuild` with Lenny Zeltser [by email](https://zeltser.com/contact).

