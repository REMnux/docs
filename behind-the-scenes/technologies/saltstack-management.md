# SaltStack Management

The REMnux distro uses [SaltStack](https://www.saltstack.com) to automate the installation and configuration of the tools that comprise the distro. This is accomplished using [Salt state files](https://docs.saltstack.com/en/getstarted/fundamentals/states.html), each one describing the steps necessary to set up the software component. These files are stored in [the REMnux/salt-states repository on Github](https://github.com/REMnux/salt-states), and are available for your review. Read on to learn how REMnux uses these State Files to manage the configuration of a REMnux system.

{% hint style="info" %}
REMnux uses SaltStack for locally managing the configuration of the system where the distro is installed. It doesn't use other SaltStack capabilities, such as remote command execution.
{% endhint %}

A state file can direct SaltStack to install a tool by supporting a variety of formats in which such tools might be packaged, including [Ubuntu packages](https://packages.ubuntu.com), [pip modules](https://pypi.org/project/pip/), Git repositories, [Ruby gems](https://rubygems.org), etc. Each state file represents one aspect of the state in which the system should be after SaltStack runs. The files follow the YAML markup language.

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

Here's an example of a Salt state file [oletools.sls](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/oletools.sls) to install [oletools](http://www.decalage.info/python/oletools), a set of Python tools for analyzing Microsoft Office documents. REMnux installs Python packages in isolated virtual environments to avoid dependency conflicts:

```text
include:
  - remnux.packages.python3-virtualenv
  - remnux.python3-packages.xlmmacrodeobfuscator

remnux-python3-packages-oletools-venv:
  virtualenv.managed:
    - name: /opt/oletools
    - venv_bin: /usr/bin/virtualenv
    - pip_pkgs:
      - pip>=24.1.3
      - setuptools>=70.0.0
    - require:
      - sls: remnux.packages.python3-virtualenv

remnux-python3-packages-oletools:
  pip.installed:
    - name: oletools
    - bin_env: /opt/oletools/bin/python3
    - upgrade: True
    - require:
      - virtualenv: remnux-python3-packages-oletools-venv
```

The state file first creates a virtual environment at `/opt/oletools` using `virtualenv.managed`, then installs the oletools package into that environment using `pip.installed`. This pattern isolates each tool's dependencies and avoids conflicts between packages.

## Salt State File to Configure a Tool

REMnux also uses Salt state files configure the environment and the tools installed as part of the distro. For example, here's a short excerpt from [the Salt state file that configures Ghidra](https://github.com/REMnux/salt-states/blob/master/remnux/config/ghidra/init.sls), which is a reverse-engineering tool that includes a disassembler and debugger. \(The installation of Ghidra is handled using a separate [ghidra.sls](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ghidra.sls) file.\)

```text
remnux-config-ghidra-file-preferences:
  file.managed:
    - name: {{ home }}/.ghidra/.ghidra_10.1.1_PUBLIC/preferences 
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

