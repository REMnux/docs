# SaltStack Management

The REMnux distro uses [SaltStack](https://www.saltstack.com) to automate the installation and configuration of the tools that comprise the distro. This is accomplished using [Salt state files](https://docs.saltstack.com/en/getstarted/fundamentals/states.html), each one describing the steps necessary to set up the software component. These files are stored in [the REMnux/salt-states repository on Github](https://github.com/REMnux/salt-states), and are available for your review. Read on to learn how REMnux uses these State Files to manage the configuration of a REMnux system.

{% hint style="info" %}
REMnux uses SaltStack for locally managing the configuration of the system where the distro is installed. It doesn't use other SaltStack capabilities, such as remote command execution.
{% endhint %}

A state file can direct SaltStack to install a tool by supporting a variety of formats in which such tools migh be packages, including [Ubuntu packages](https://packages.ubuntu.com), [pip modules](https://pypi.org/project/pip/), Git repositories, [Ruby gems](https://rubygems.org), etc. Each state file represents one aspect of the state in which the system should be after SaltStack runs. The files follow the YAML markup language.

## Salt State File to Install an Ubuntu Package <a id="state-file-ubuntu-package"></a>

For example, here's the Salt state file [edb-debgger.sls](https://github.com/REMnux/salt-states/blob/master/remnux/packages/edb-debugger.sls) for installing [edb](https://github.com/eteran/edb-debugger), a powerful debugger for examining ELF binaries:

```text
include:
  - remnux.repos.remnux
  - remnux.packages.xterm
  
edb-debugger:
  pkg.installed:
    - pkgrepo: remnux
    - require:
      - sls: remnux.packages.xterm
```

The line `edb-debugger:` specifies the name of the Ubuntu package that SaltStack should install. The `pkgrepo: remnux` line specifies that SaltStack will find this package in the Ubuntu package repository named "remnux." The `require` statement explains that this package depends on "xterm." The distro also includes state files that explain SaltStack should install [the remnux repository](https://github.com/REMnux/salt-states/blob/master/remnux/repos/remnux.sls) and [the xterm package](https://github.com/REMnux/salt-states/blob/master/remnux/packages/xterm.sls).

## Salt State File to Install a pip Package <a id="state-file-pip"></a>

Here's an example of a Salt state file [pyzipper.sls](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/pyzipper.sls) to install [pyzipper](https://github.com/danifus/pyzipper), a Python library for interacting with Zip file archives. SaltStack will use the Python 3 version of pip \(pip3\), which is installed using [remnux.packages.python3-pip](https://github.com/REMnux/salt-states/blob/master/remnux/packages/python3-pip.sls), to install pyzipper from the standard PyPI repository of Python software:

```text
include:
  - remnux.packages.python3-pip
  - remnux.python3-packages.pycryptodomex

remnux-python-packages-pyzipper:
  pip.installed:
    - name: pyzipper
    - bin_env: /usr/bin/python3
    - require:
      - sls: remnux.packages.python3-pip
      - sls: remnux.python3-packages.pycryptodomex
```

Since pyzipper depends on the "pycryptodomex" package, which might not be automatically installed by pip, the state file above explicitly specifies [the state file of pycryptodomex](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/pycryptodomex.sls) as a dependency.

## Salt State File to Configure a Tool

REMnux also uses Salt state files configure the environment and the tools installed as part of the distro. For example, here's a short excerpt from [the Salt state file that configures Ghidra](https://github.com/REMnux/salt-states/blob/master/remnux/config/ghidra/init.sls), which is a reverse-engineering tool that includes a disassembler and debugger. \(The installation of Ghira is handled using a separate [ghidra.sls](https://github.com/REMnux/salt-states/blob/master/remnux/tools/ghidra.sls) file.\)

```text
remnux-config-ghidra-file-preferences:
  file.managed:
    - name: {{ home }}/.ghidra/.ghidra_9.1.2_PUBLIC/preferences 
    - source: salt://remnux/config/ghidra/preferences
    - replace: False
    - user: {{ user }}
    - group: {{ user }}
    - makedirs: True
    - require:
      - user: remnux-user-{{ user }}
    - watch:
      - file: remnux-config-ghidra-gdt-owner
```

In the example above:

* [`file.managed`](https://docs.saltstack.com/en/latest/ref/states/all/salt.states.file.html#salt.states.file.managed) specifies the desired state of the Ghidra "preferences" file, located in the user's home directory. 
* `source` of the file is [the version of "preferences" in the GitHub repository](https://github.com/REMnux/salt-states/blob/master/remnux/config/ghidra/preferences) where this state file resides; this directs SaltStack to copy this file to the location specified by `name`. 
* `replace`  directs SaltStack not to replace the file if it already exists.
* `user` and `group` specify that the file should be owned by the user and the user's group.
* `makedirs` direct SaltStack to create the directory structure so the file can be placed in the location specified by `name`.

The state file instructions above rely on the values `home` and `user`, which are set earlier in the file:

```text
{%- set user = salt['pillar.get']('remnux_user', 'remnux') -%}
{%- if user == "root" -%}
  {%- set home = "/root" -%}
{%- else %}
  {%- set home = "/home/" + user -%}
{%- endif -%}
```

This excerpt from the Ghidra configuration state file uses the "[pillars](https://docs.saltstack.com/en/master/ref/modules/all/salt.modules.pillar.html#salt.modules.pillar.get)" feature of SaltStack, which gives SaltStack access to named values defined before the state file has a chance to run. In this case, the state file sets the `user` value by retrieving the pillar variable named `remnux_user`, which is normally set by [the REMnux installer](remnux-installer.md); if it's not available, SaltStack is directed to use the default value "remnux." Further, depending on the `user` value, the state file sets the `home` value to point to the user's home directory.

