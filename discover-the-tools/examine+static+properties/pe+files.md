---
description: Examine Static Properties
---

# PE Files

## Manalyze

Perform static analysis of suspicious PE files.

**Website**: [https://github.com/JusticeRage/Manalyze](https://github.com/JusticeRage/Manalyze)  
**Author**: Ivan Kwiatkowski: [https://twitter.com/JusticeRage](https://twitter.com/JusticeRage)  
**License**: GNU General Public License \(GPL\) v3: [https://github.com/zrax/pycdc/blob/master/LICENSE](https://github.com/zrax/pycdc/blob/master/LICENSE)  
**Notes**: Run "manalyze" to invoke the tool. To update the tool's Yara rules to include ClamAV, run "sudo /usr/local/manalyze/yara\_rules/update\_clamav\_signatures.py". To query VirusTotal, add your API key to /usr/local/manalyze/manalyze.conf.  
**State File**: [remnux.tools.manalyze](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/manalyze.sls)

## PEframe

Statically analyze PE and Microsoft Office files.

**Website**: [https://github.com/guelfoweb/peframe](https://github.com/guelfoweb/peframe)  
**Author**: Gianni Amato: [https://twitter.com/guelfoweb](https://twitter.com/guelfoweb)  
**License**: Free, unknown license  
**Notes**: peframe  
**State File**: [remnux.python-packages.peframe](https://github.com/REMnux/salt-states/blob/master/./remnux/python-packages/peframe.sls)

## PE Tree

Examine contents and structure of PE files.

**Website**: [https://github.com/blackberry/pe\_tree](https://github.com/blackberry/pe_tree)  
**Author**: BlackBerry Limited: [https://twitter.com/BlackBerrySpark](https://twitter.com/BlackBerrySpark) and Tom Bonner: https//twitter.com/thomas\_bonner  
**License**: Apache License 2.0: [https://github.com/blackberry/pe\_tree/blob/master/LICENSE](https://github.com/blackberry/pe_tree/blob/master/LICENSE)  
**Notes**: pe-tree  
**State File**: [remnux.python-packages.pe-tree](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/pe-tree.sls)

## pecheck

Analyze static properties of PE files.

**Website**: [https://blog.didierstevens.com/2020/03/15/pecheck-py-version-0-7-10/](https://blog.didierstevens.com/2020/03/15/pecheck-py-version-0-7-10/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**State File**: [remnux.scripts.pecheck](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/pecheck.sls)

## pefile

Python library for analyzing static properties of PE files.

**Website**: [https://github.com/erocarrera/pefile](https://github.com/erocarrera/pefile)  
**Author**: Ero Carrera: [http://blog.dkbza.org](http://blog.dkbza.org)  
**License**: MIT License: [https://github.com/erocarrera/pefile/blob/master/LICENSE](https://github.com/erocarrera/pefile/blob/master/LICENSE)  
**Notes**: [https://github.com/erocarrera/pefile/blob/wiki/UsageExamples.md\#introduction](https://github.com/erocarrera/pefile/blob/wiki/UsageExamples.md#introduction)  
**State File**: [remnux.python-packages.pefile](https://github.com/REMnux/salt-states/blob/master/./remnux/python-packages/pefile.sls)

## pedump

Statically analyze PE files.

**Website**: [https://github.com/zed-0xff/pedump](https://github.com/zed-0xff/pedump)  
**Author**: Andrey "Zed" Zaikin  
**License**: MIT License: [https://github.com/zed-0xff/pedump/blob/master/LICENSE.txt](https://github.com/zed-0xff/pedump/blob/master/LICENSE.txt)  
**State File**: [remnux.rubygems.pedump](https://github.com/REMnux/salt-states/blob/master/./remnux/rubygems/pedump.sls)

## pev

Analyze PE files and extract strings from them

**Website**: [http://pev.sourceforge.net](http://pev.sourceforge.net)  
**Author**: Fernando Mercês, Jardel Weyrich  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/merces/pev/blob/master/LICENSE](https://github.com/merces/pev/blob/master/LICENSE)  
**Notes**: pestr, readpe, pedis, pehash, pescan  
**State File**: [remnux.packages.pev](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/pev.sls)

## PortEx

Statically analyze PE files.

**Website**: [https://github.com/katjahahn/PortEx](https://github.com/katjahahn/PortEx)  
**Author**: Karsten Hahn: [https://twitter.com/struppigel](https://twitter.com/struppigel)  
**License**: Apache License 2.0: [https://github.com/katjahahn/PortEx/blob/master/LICENSE](https://github.com/katjahahn/PortEx/blob/master/LICENSE)  
**Notes**: portex  
**State File**: [remnux.packages.portex](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/portex.sls)

## StringSifter

Automatically rank strings based on their relevance to the analysis of suspicious Windows executables.

**Website**: [https://github.com/fireeye/stringsifter](https://github.com/fireeye/stringsifter)  
**Author**:  FireEye Inc.  
**License**: Apache License 2.0: [https://github.com/fireeye/stringsifter/blob/master/LICENSE](https://github.com/fireeye/stringsifter/blob/master/LICENSE)  
**Notes**: flarestrings  
**State File**: [remnux.python-packages.stringsifter](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/stringsifter.sls)

## bearparser

Parse PE file contents.

**Website**: [https://github.com/hasherezade/bearparser/wiki](https://github.com/hasherezade/bearparser/wiki)  
**Author**: hasherezade: [hasherezade@op.pl](https://twitter.com/hasherezade)  
**License**: BSD 2-Clause "Simplified" License: [https://github.com/hasherezade/bearparser/blob/master/LICENSE](https://github.com/hasherezade/bearparser/blob/master/LICENSE)  
**Notes**: bearcommander  
**State File**: [remnux.packages.bearparser](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/bearparser.sls)

