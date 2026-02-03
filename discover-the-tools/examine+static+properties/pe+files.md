---
description: Examine Static Properties
---

# PE Files

## Manalyze

Perform static analysis of suspicious PE files.

**Website**: [https://github.com/JusticeRage/Manalyze](https://github.com/JusticeRage/Manalyze)\
**Author**: Ivan Kwiatkowski: [https://x.com/JusticeRage](https://x.com/JusticeRage)\
**License**: GNU General Public License (GPL) v3: [https://github.com/JusticeRage/Manalyze/blob/master/LICENSE.txt](https://github.com/JusticeRage/Manalyze/blob/master/LICENSE.txt)\
**Notes**: Run "manalyze" to invoke the tool. To update the tool's Yara rules to include ClamAV, run "sudo python3 /usr/share/manalyze/yara_rules/update_clamav_signatures.py". To query VirusTotal, add your API key to /etc/manalyze/manalyze.conf.\
**State File**: [remnux.packages.manalyze](https://github.com/REMnux/salt-states/blob/master/remnux/packages/manalyze.sls)




## PEframe

Statically analyze PE and Microsoft Office files.

**Website**: [https://github.com/digitalsleuth/peframe](https://github.com/digitalsleuth/peframe)\
**Author**: Gianni Amato: [https://x.com/guelfoweb](https://x.com/guelfoweb)\
**License**: Free, unknown license\
**Notes**: peframe\
**State File**: [remnux.python3-packages.peframe](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/peframe.sls)



## dllcharacteristics.py

Read and set DLL characteristics of a PE file.

**Website**: [https://github.com/accidentalrebel/dllcharacteristics.py](https://github.com/accidentalrebel/dllcharacteristics.py)\
**Author**: Karlo Licudine: [https://x.com/accidentalrebel](https://x.com/accidentalrebel)\
**License**: GNU General Public License (GPL) v3.0: [https://github.com/accidentalrebel/dllcharacteristics.py/blob/master/LICENSE](https://github.com/accidentalrebel/dllcharacteristics.py/blob/master/LICENSE)\
**State File**: [remnux.scripts.dllcharacteristics](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/dllcharacteristics.sls)


## pefile

Python library for analyzing static properties of PE files.

**Website**: [https://github.com/erocarrera/pefile](https://github.com/erocarrera/pefile)\
**Author**: Ero Carrera: [http://blog.dkbza.org](http://blog.dkbza.org)\
**License**: MIT License: [https://github.com/erocarrera/pefile/blob/master/LICENSE](https://github.com/erocarrera/pefile/blob/master/LICENSE)\
**Notes**: [https://github.com/erocarrera/pefile/blob/wiki/UsageExamples.md#introduction](https://github.com/erocarrera/pefile/blob/wiki/UsageExamples.md#introduction)\
**State File**: [remnux.python3-packages.pefile](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/pefile.sls)

## PE Tree

Examine contents and structure of PE files.

**Website**: [https://github.com/blackberry/pe_tree](https://github.com/blackberry/pe_tree)\
**Author**: BlackBerry Limited: [https://x.com/BlackBerrySpark](https://x.com/BlackBerrySpark) and Tom Bonner: [https://x.com/thomas_bonner](https://x.com/thomas_bonner)\
**License**: Apache License 2.0: [https://github.com/blackberry/pe_tree/blob/master/LICENSE](https://github.com/blackberry/pe_tree/blob/master/LICENSE)\
**Notes**: pe-tree\
**State File**: [remnux.python3-packages.pe-tree](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/pe-tree.sls)


## pedump

Statically analyze PE files and extract their components (e.g., resources).

**Website**: [https://github.com/zed-0xff/pedump](https://github.com/zed-0xff/pedump)\
**Author**: Andrey "Zed" Zaikin\
**License**: MIT License: [https://github.com/zed-0xff/pedump/blob/master/LICENSE.txt](https://github.com/zed-0xff/pedump/blob/master/LICENSE.txt)\
**State File**: [remnux.rubygems.pedump](https://github.com/REMnux/salt-states/blob/master/remnux/rubygems/pedump.sls)

## pev

Analyze PE files and extract strings from them.

**Website**: [https://github.com/mentebinaria/readpe](https://github.com/mentebinaria/readpe)\
**Author**: Fernando Merces, Jardel Weyrich\
**License**: GNU General Public License (GPL) v2: [https://github.com/mentebinaria/readpe/blob/master/LICENSE](https://github.com/mentebinaria/readpe/blob/master/LICENSE)\
**Notes**: pestr, readpe, pedis, pehash, pescan, peldd, peres\
**State File**: [remnux.packages.pev](https://github.com/REMnux/salt-states/blob/master/remnux/packages/pev.sls)



## PortEx

Statically analyze PE files.

**Website**: [https://github.com/katjahahn/PortEx](https://github.com/katjahahn/PortEx)\
**Author**: Karsten Hahn: [https://x.com/struppigel](https://x.com/struppigel)\
**License**: Apache License 2.0: [https://github.com/katjahahn/PortEx/blob/master/LICENSE](https://github.com/katjahahn/PortEx/blob/master/LICENSE)\
**Notes**: portex\
**State File**: [remnux.packages.portex](https://github.com/REMnux/salt-states/blob/master/remnux/packages/portex.sls)


## bearparser

Parse PE file contents.

**Website**: [https://github.com/hasherezade/bearparser/wiki](https://github.com/hasherezade/bearparser/wiki)\
**Author**: hasherezade: [https://x.com/hasherezade](https://x.com/hasherezade)\
**License**: BSD 2-Clause "Simplified" License: [https://github.com/hasherezade/bearparser/blob/master/LICENSE](https://github.com/hasherezade/bearparser/blob/master/LICENSE)\
**Notes**: bearcommander\
**State File**: [remnux.packages.bearparser](https://github.com/REMnux/salt-states/blob/master/remnux/packages/bearparser.sls)


## debloat

Remove junk contents from bloated Windows executables.

**Website**: [https://github.com/Squiblydoo/debloat](https://github.com/Squiblydoo/debloat)\
**Author**: Squiblydoo: [https://x.com/SquiblydooBlog](https://x.com/SquiblydooBlog)\
**License**: BSD 3-Clause License: [https://github.com/Squiblydoo/debloat/blob/main/LICENSE](https://github.com/Squiblydoo/debloat/blob/main/LICENSE)\
**Notes**: Run the command-line version as `debloat` or the GUI version as `debloat-gui`\
**State File**: [remnux.python3-packages.debloat](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/debloat.sls)


## readpe (formerly pev)

Analyze PE files and extract strings from them.

**Website**: [https://github.com/mentebinaria/readpe](https://github.com/mentebinaria/readpe)\
**Author**: Fernando Merces, Jardel Weyrich\
**License**: GNU General Public License (GPL) v2: [https://github.com/mentebinaria/readpe/blob/master/LICENSE](https://github.com/mentebinaria/readpe/blob/master/LICENSE)\
**Notes**: readpe, pestr, pedis, pehash, pescan, pesec, peldd, pepack, peres, ofs2rva, rva2ofs\
**State File**: [remnux.packages.pev](https://github.com/REMnux/salt-states/blob/master/remnux/packages/pev.sls)

## pecheck.py

Analyze static properties of PE files.

**Website**: [https://blog.didierstevens.com/2020/03/15/pecheck-py-version-0-7-10/](https://blog.didierstevens.com/2020/03/15/pecheck-py-version-0-7-10/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.didier-stevens-scripts](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/didier-stevens-scripts.sls)



## disitool.py

Extract, delete, copy, and inject digital signatures in PE files.

**Website**: [https://blog.didierstevens.com/programs/disitool/](https://blog.didierstevens.com/programs/disitool/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.didier-stevens-scripts](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/didier-stevens-scripts.sls)
