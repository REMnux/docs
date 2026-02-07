# Contribute a Debian Package

The following steps describe how you can build and locally test a Debian-based package for a new tool, in case you'd like to contribute it to REMnux. You can perform these steps on macOS, Linux, or Windows using Docker.

{% hint style="info" %}
Before starting this work, consider [reaching out to Lenny Zeltser](https://zeltser.com/contact) to confirm that it makes sense to include the tool as part of REMnux. Also, become familiar with the way REMnux uses [custom Debian packages](../../behind-the-scenes/technologies/debian-packages.md) to install tools when practical.
{% endhint %}

## 1. Install Git and Docker

Follow the steps appropriate for your operating system to install [Git](https://git-scm.com) and [Docker](https://www.docker.com/products/docker-desktop) on your system.

REMnux provides a Docker image called `remnux/package-builder` that contains all the tools needed to build Debian packages, including `debhelper`, `dpkg-buildpackage`, and related utilities. You don't need to install any packaging tools on your local system.

{% hint style="success" %}
The tag `noble` corresponds to Ubuntu 24.04, which is the current target for REMnux packages. If you need to build for a different Ubuntu version, replace `noble` with the appropriate codename in the commands throughout this guide.
{% endhint %}

## 2. Create the Package Files

The source files for custom REMnux packages are in the REMnux/distro repository on GitHub in the `ppasrc` subdirectory. Start by cloning that repo and navigating to that subdirectory:

```text
git clone https://github.com/REMnux/distro.git
cd distro/ppasrc
```

The existing packages here serve as templates for your new one. Instead of creating files from scratch, identify a package that operates similarly to the tool you're packaging and use it as a starting point. Choose a template based on what kind of tool you're packaging:

* **Compiled from source code** (e.g., `xorsearch`): The tool has C or similar source code and a Makefile. Place the source files alongside the `debian/` directory; the build process compiles them during package creation.
* **Pre-compiled binary** (e.g., `flare-floss`): A single executable placed directly into `/usr/bin`. Place the binary alongside the `debian/` directory.
* **JAR file with wrapper script** (e.g., `baksmali`): A Java archive installed to `/opt/` with a shell script in `/usr/bin` that invokes it. Place the `.jar` file and wrapper script alongside the `debian/` directory.

Create a directory structure that follows the naming convention `PACKAGE/PACKAGE-VERSION-DISTRO/`, then copy the `debian/` directory from your chosen template:

```text
mkdir -p mypackage/mypackage-1.0.0-noble
cp -r flare-floss/flare-floss-3.1-noble/debian mypackage/mypackage-1.0.0-noble/
mkdir -p mypackage/mypackage-1.0.0-noble/debian/source
```

Place the tool's files (source code, binaries, or wrapper scripts) into the `mypackage-1.0.0-noble/` directory next to the `debian/` folder. The `install` file inside `debian/` will reference these files to specify where they get installed on the system.

## 3. Customize the Debian Files

The `debian/` subdirectory contains the files that describe how the package should be built and installed. Customize each file based on the examples below.

### changelog

Specifies the package version, target distribution, and release notes. The formatting and whitespace are significant—use `date -R` to generate the timestamp in the required format.

```text
mypackage (1.0.0-noble) noble; urgency=medium

  * Initial release.

 -- REMnux Distribution <distro@remnux.org>  Wed, 05 Feb 2026 12:00:00 -0500
```

Note that the version string includes the distribution codename (e.g., `1.0.0-noble`) and the distribution field also says `noble`. The line beginning with ` -- ` must start with exactly one space.

### control

Defines package metadata, build dependencies, runtime dependencies, and the description.

For a compiled package like `xorsearch`:

```text
Source: xorsearch
Section: utils
Priority: optional
Maintainer: REMnux Distribution <distro@remnux.org>
Build-Depends: debhelper (>= 8.0.0)
Standards-Version: 3.9.4
Homepage: https://blog.didierstevens.com/programs/xorsearch/

Package: xorsearch
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: Locate and decode strings obfuscated using common techniques.
```

For a JAR-based package like `baksmali` that needs Java at runtime:

```text
Source: baksmali
Section: utils
Priority: optional
Maintainer: REMnux Distribution <distro@remnux.org>
Build-Depends: debhelper (>= 10)
Standards-Version: 4.1.2
Homepage: https://bitbucket.org/JesusFreke/smali/src/master/

Package: baksmali
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, default-jre
Description: Disassembler for the dex format used by Dalvik, Android's Java VM implementation.
```

Set `Maintainer` to `REMnux Distribution <distro@remnux.org>` for all packages, not your personal name. For new packages, use `Build-Depends: debhelper (>= 10)` and `Standards-Version: 4.1.2`. Use `Architecture: any` for most packages, or `Architecture: amd64` if the tool only supports 64-bit x86 systems. List runtime dependencies in the `Depends` field (e.g., `default-jre` for Java tools). List build-time dependencies in `Build-Depends`.

### install

Lists source-to-destination file mappings, one per line. The source path is relative to the package directory (next to the `debian/` folder); the destination is relative to the system root.

For a compiled package that also installs data files:

```text
rules.txt usr/share/xorsearch
```

For a pre-compiled binary:

```text
floss usr/bin
```

For a JAR with a wrapper script:

```text
baksmali-2.4.0.jar opt/baksmali
baksmali usr/bin
```

Note that compiled packages typically have their binary installed automatically by the Makefile, so the `install` file only lists additional files. Pre-compiled binaries and JAR packages rely on `install` to place all their files.

### copyright

Includes the upstream license and a GPL-3.0+ declaration for the Debian packaging files.

```text
Format: https://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
Upstream-Name: mypackage
Source: https://github.com/author/mypackage

Files: *
Copyright: 2026 Author Name
License: MIT
 https://github.com/author/mypackage/blob/main/LICENSE

Files: debian/*
Copyright: 2026 REMnux Distribution <distro@remnux.org>
License: GPL-3.0+
```

Adjust the upstream license to match the tool's actual license.

### rules

Controls the build process. For most packages, the default is sufficient:

```text
#!/usr/bin/make -f

%:
	dh $@
```

Only modify this file if the build requires custom steps beyond what the Makefile or `install` file handles.

### compat

Specifies the debhelper compatibility level. Use `9` or `10`:

```text
10
```

### source/format

Specifies the source package format. Use `3.0 (native)` for REMnux packages:

```text
3.0 (native)
```

{% hint style="info" %}
If you copied the `debian/` directory from an existing package, delete the `debian/files` file if it's present. This file is a build artifact and should not be included in your submission.
{% endhint %}

## 4. Build and Test Using Docker

Build the package by running the following command from the root of the `distro` repository. This mounts the repository into the container and runs `dpkg-buildpackage` in the package directory:

```text
docker run --rm -v "$(pwd)":/distro remnux/package-builder:noble bash -c "cd /distro/ppasrc/mypackage/mypackage-1.0.0-noble && dpkg-buildpackage -us -uc"
```

{% hint style="success" %}
The `$(pwd)` syntax works on macOS and Linux. On Windows, replace `"$(pwd)"` with the full path to your `distro` directory, for example: `-v "C:\Users\you\distro":/distro`.
{% endhint %}

The `-us -uc` flags tell `dpkg-buildpackage` not to sign the package, since only the REMnux maintainer has the signing key. If the build succeeds, it will generate a `.deb` file and several other files in the parent directory (`ppasrc/mypackage/`).

{% hint style="success" %}
Use `dpkg-deb --info` inside Docker to verify the generated package, since this is a Linux tool that may not be available on your host system:

```text
docker run --rm -v "$(pwd)":/distro remnux/package-builder:noble dpkg-deb --info /distro/ppasrc/mypackage/mypackage_1.0.0-noble_amd64.deb
```
{% endhint %}

After testing, clean up the `.deb` files from the repository before committing, since they are not excluded by `.gitignore`. Other build artifacts such as `.changes`, `.buildinfo`, and `.tar.xz` files are already gitignored. The `.dsc` files present in the repository are signed versions committed by the maintainer—do not include unsigned `.dsc` files in your pull request.

{% hint style="info" %}
If the build fails, common causes include:

* **Missing build dependencies**: Add them to `Build-Depends` in the `control` file.
* **Incorrect install paths**: Verify the file paths in the `install` file match the actual files in your package directory.
* **Makefile issues**: If the source code's Makefile uses non-standard targets, you may need to add override rules in the `rules` file.
* **Permission errors**: Ensure scripts and binaries have the correct executable permissions before building.
{% endhint %}

## 5. Create a Pull Request

Once you have a working, tested set of package files in the local copy of the REMnux/distro repository, [create a GitHub pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for that repo, so the package may be considered for inclusion in the REMnux distro.

Your pull request should include the `PACKAGE/PACKAGE-VERSION-DISTRO/` directory with the tool's files and the `debian/` subdirectory. Do not include build artifacts such as `.deb`, `.changes`, `.buildinfo`, or unsigned `.dsc` files.

If the pull request isn't working, consider submitting the files to Lenny Zeltser [by email](https://zeltser.com/contact).

{% hint style="info" %}
After accepting the pull request, the REMnux maintainer handles signing the package and uploading it to the [Launchpad PPA](https://launchpad.net/~remnux/+archive/ubuntu/stable/+packages). You don't need to interact with Launchpad as a contributor.
{% endhint %}

If the tool also needs a Salt State file for installation on the REMnux system, see [Contribute a Salt State File](contribute-a-salt-state-file.md) for instructions on creating one.
