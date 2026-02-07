---
description: Discover the Tools
---

# General Utilities

## REMnux Installer

Install and update the REMnux distro.

**Website**: [https://github.com/REMnux/distro/blob/master/files/remnux-installer.sh](https://github.com/REMnux/distro/blob/master/files/remnux-installer.sh)\
**Author**: Lenny Zeltser\
**License**: Public Domain\
**Notes**: This is a wrapper around the Cast installer that the script uses behind the scenes. To run the tool on REMnux, type `remnux`\
**State File**: [remnux.tools.remnux-installer](https://github.com/REMnux/salt-states/blob/master/remnux/tools/remnux-installer.sls)





## myip

Determine the IP address of the default network interface.

**Website**: [https://github.com/REMnux/distro/blob/master/files/myip](https://github.com/REMnux/distro/blob/master/files/myip)\
**Author**: Lenny Zeltser, with input from the community\
**License**: Public Domain\
**State File**: [remnux.scripts.myip](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/myip.sls)

## texteditor.py

Edit text files from the command line using search-and-replace commands.

**Website**: [https://blog.didierstevens.com/2021/07/05/new-tool-texteditor-py/](https://blog.didierstevens.com/2021/07/05/new-tool-texteditor-py/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.texteditor](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/texteditor.sls)

## sortcanon.py

Sort text files using canonicalization functions built into this tool.

**Website**: [https://blog.didierstevens.com/2022/06/18/new-tool-sortcanon-py/](https://blog.didierstevens.com/2022/06/18/new-tool-sortcanon-py/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.sortcanon](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/sortcanon.sls)

## OpenSSH

Initiate and receive SSH and SFTP connections.

**Website**: [https://www.openssh.com](https://www.openssh.com)\
**Author**: [https://github.com/openssh/openssh-portable/blob/master/CREDITS](https://github.com/openssh/openssh-portable/blob/master/CREDITS)\
**License**: BSD licence: [https://github.com/openssh/openssh-portable/blob/master/LICENCE](https://github.com/openssh/openssh-portable/blob/master/LICENCE)\
**Notes**: sftp, ssh, sshd \<start|stop|status>, etc.\
**State File**: [remnux.packages.openssh](https://github.com/REMnux/salt-states/blob/master/remnux/packages/openssh.sls)

## 7-Zip

Compress and decompress files using a variety of algorithms.

**Website**: [https://www.7-zip.org](https://www.7-zip.org)\
**Author**: Igor Pavlov\
**License**: GNU Lesser General Public License (LGPL)\
**Notes**: 7-Zip standard: 7z, 7za, 7zr. For latest alpha version, use 7zz instead of 7z.\
**State File**: [remnux.packages.7zip](https://github.com/REMnux/salt-states/blob/master/remnux/packages/7zip.sls)

## Firefox

Web browser.

**Website**: [https://www.mozilla.org/firefox/](https://www.mozilla.org/firefox/)\
**Author**: Mozilla Corporation\
**License**: Mozilla Public License (MPL): [https://www.mozilla.org/en-US/MPL/#source-code](https://www.mozilla.org/en-US/MPL/#source-code)\
**Notes**: firefox\
**State File**: [remnux.packages.firefox](https://github.com/REMnux/salt-states/blob/master/remnux/packages/firefox.sls)


## Info-ZIP

Compress and decompress files using the zip algorithm.

**Website**: [http://infozip.sourceforge.net](http://infozip.sourceforge.net)\
**Author**: Ed Gordon, Mark Adler, Jean-loup Gailly, David Kirschbaum, Rich Wales, etc.\
**License**: Free, custom license\
**Notes**: zip, unzip\
**State File**: [remnux.packages.unzip](https://github.com/REMnux/salt-states/blob/master/remnux/packages/unzip.sls)

## cabextract

Extract Microsoft cabinet (cab) files.

**Website**: [https://www.cabextract.org.uk](https://www.cabextract.org.uk)\
**Author**: [https://www.cabextract.org.uk/#credits](https://www.cabextract.org.uk/#credits)\
**License**: GNU General Public License (GPL)\
**State File**: [remnux.packages.cabextract](https://github.com/REMnux/salt-states/blob/master/remnux/packages/cabextract.sls)

## nasm

An x86-64 assembler.

**Website**: [https://www.nasm.us](https://www.nasm.us)\
**Author**: H. Peter Anvin, Cyrill Gorcunov, Chang Seok Bae, Jim Kukunas, Frank B. Kotler, etc.: [https://github.com/netwide-assembler/nasm/blob/master/AUTHORS](https://github.com/netwide-assembler/nasm/blob/master/AUTHORS)\
**License**: BSD 2-Clause "Simplified" License: [https://github.com/netwide-assembler/nasm/blob/master/LICENSE](https://github.com/netwide-assembler/nasm/blob/master/LICENSE)\
**State File**: [remnux.packages.nasm](https://github.com/REMnux/salt-states/blob/master/remnux/packages/nasm.sls)


## SQLite

Manage and interact with SQL database files.

**Website**: [http://www.sqlite.org](http://www.sqlite.org)\
**Author**: D. Richard Hipp, Dan Kennedy, Joe Mistachkin: [https://www.sqlite.org/crew.html](https://www.sqlite.org/crew.html)\
**License**: Public Domain: [https://www.sqlite.org/copyright.html](https://www.sqlite.org/copyright.html)\
**Notes**: sqlite3\
**State File**: [remnux.packages.sqlite](https://github.com/REMnux/salt-states/blob/master/remnux/packages/sqlite.sls)

## unrar-free

Decompress files using a variety of algorithms.

**Website**: [https://www.rarlab.com](https://www.rarlab.com)\
**Author**: Ben Asselstine, Eugene Roshal, Christian Scheurer, Johannes Winkelmann\
**License**: GNU General Public License (GPL) v2+\
**Notes**: unrar\
**State File**: [remnux.packages.unrar](https://github.com/REMnux/salt-states/blob/master/remnux/packages/unrar.sls)

## RAR

Compress and decompress files using a variety of algorithms.

**Website**: [https://www.rarlab.com](https://www.rarlab.com)\
**Author**: Alexander Roshal\
**License**: Shareware: "Anyone may use this software during a test period of 40 days. Following this test period of 40 days or less, if you wish to continue to use RAR, you must purchase a license." For details, see [https://www.rarlab.com/license.htm](https://www.rarlab.com/license.htm).\
**Notes**: rar\
**State File**: [remnux.packages.rar](https://github.com/REMnux/salt-states/blob/master/remnux/packages/rar.sls)

## Docker

Run and manage containers.

**Website**: [https://www.docker.com](https://www.docker.com)\
**Author**: Docker Inc.\
**License**: Apache License 2.0: [https://github.com/moby/moby/blob/master/LICENSE](https://github.com/moby/moby/blob/master/LICENSE)\
**State File**: [remnux.packages.docker](https://github.com/REMnux/salt-states/blob/master/remnux/packages/docker.sls)

## Nautilus

Graphical file manager.

**Website**: [https://gitlab.gnome.org/GNOME/nautilus](https://gitlab.gnome.org/GNOME/nautilus)\
**Author**: [https://gitlab.gnome.org/Teams](https://gitlab.gnome.org/Teams)\
**License**: GNU General Public License (GPL) v3: [https://gitlab.gnome.org/GNOME/nautilus/-/blob/master/LICENSE](https://gitlab.gnome.org/GNOME/nautilus/-/blob/master/LICENSE)\
**State File**: [remnux.packages.nautilus](https://github.com/REMnux/salt-states/blob/master/remnux/packages/nautilus.sls)


## Wine

Run Windows applications.

**Website**: [https://www.winehq.org](https://www.winehq.org)\
**Author**: [https://wiki.winehq.org/Acknowledgements](https://wiki.winehq.org/Acknowledgements)\
**License**: GNU Lesser General Public License (LGPL) v2.1 or later: [https://wiki.winehq.org/Licensing](https://wiki.winehq.org/Licensing)\
**Notes**: wine\
**State File**: [remnux.packages.wine](https://github.com/REMnux/salt-states/blob/master/remnux/packages/wine.sls)

## cURL

Interact with servers via supported protocols, including HTTP, HTTPS, FTP, IMAP, etc. using this command-line tool.

**Website**: [https://curl.se](https://curl.se)\
**Author**: Daniel Stenberg and contributors: [https://curl.se/docs/thanks.html](https://curl.se/docs/thanks.html)\
**License**: Free, custom license: [https://curl.se/docs/copyright.html](https://curl.se/docs/copyright.html)\
**Notes**: curl\
**State File**: [remnux.packages.curl](https://github.com/REMnux/salt-states/blob/master/remnux/packages/curl.sls)


## IBus

Adjust input methods for the GUI.

**Website**: [https://github.com/ibus/ibus](https://github.com/ibus/ibus)\
**Author**: Peng Huang, Takao Fujiwara\
**License**: GNU Lesser General Public License (LGPL) v2.1: [https://github.com/ibus/ibus/blob/master/COPYING](https://github.com/ibus/ibus/blob/master/COPYING)\
**Notes**: ibus-setup\
**State File**: [remnux.packages.ibus](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ibus.sls)

## GNOME Calculator

Calculator.

**Website**: [https://wiki.gnome.org/Apps/Calculator](https://wiki.gnome.org/Apps/Calculator)\
**Author**: [https://github.com/GNOME/gnome-calculator/graphs/contributors](https://github.com/GNOME/gnome-calculator/graphs/contributors)\
**License**: GNU General Public License (GPL) v3: [https://github.com/GNOME/gnome-calculator/blob/mainline/COPYING](https://github.com/GNOME/gnome-calculator/blob/mainline/COPYING)\
**Notes**: galculator\
**State File**: [remnux.packages.galculator](https://github.com/REMnux/salt-states/blob/master/remnux/packages/galculator.sls)


## myjson-filter.py

Filter data formatted using the JSON format used by Didier Stevens' tools.

**Website**: [https://blog.didierstevens.com/2022/04/09/new-tool-myjson-filter-py/](https://blog.didierstevens.com/2022/04/09/new-tool-myjson-filter-py/)\
**Author**: Didier Stevens: https://twitter.com/DidierStevens\
**License**: Public Domain\
**State File**: [remnux.scripts.myjson-filter](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/myjson-filter.sls)

## Cast

Install and manage SaltStack-based Linux distributions.

**Website**: [https://github.com/ekristen/cast](https://github.com/ekristen/cast)\
**Author**: Erik Kristensen\
**License**: MIT License: [https://github.com/ekristen/cast/blob/main/LICENSE](https://github.com/ekristen/cast/blob/main/LICENSE)\
**Notes**: cast\
**State File**: [remnux.packages.cast](https://github.com/REMnux/salt-states/blob/master/remnux/packages/cast.sls)

## PowerShell Core

Run PowerShell scripts and commands.

**Website**: [https://github.com/powershell/powershell](https://github.com/powershell/powershell)\
**Author**: Microsoft Corporation\
**License**: MIT License: [https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt](https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt)\
**Notes**: pwsh\
**State File**: [remnux.packages.powershell](https://github.com/REMnux/salt-states/blob/master/remnux/packages/powershell.sls)
