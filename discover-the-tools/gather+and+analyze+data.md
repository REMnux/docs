---
description: Discover the Tools
---

# Gather and Analyze Data

## Automater

Gather OSINT data about IPs, domains, and hashes.

**Website**: [https://github.com/digitalsleuth/TekDefense-Automater](https://github.com/digitalsleuth/TekDefense-Automater)\
**Author**: 1aN0rmus and digitalsleuth\
**License**: MIT License: [https://github.com/digitalsleuth/TekDefense-Automater/blob/master/LICENSE](https://github.com/digitalsleuth/TekDefense-Automater/blob/master/LICENSE)\
**Notes**: automater\
**State File**: [remnux.python3-packages.automater](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/automater.sls)


## dissect

Perform a variety of forensics and incident response tasks using this DFIR framework and toolset.

**Website**: [https://github.com/fox-it/dissect](https://github.com/fox-it/dissect)\
**Author**: Dissect Team: dissect@fox-it.com\
**License**: GNU Affero General Public License v3: https://github.com/fox-it/dissect/blob/main/LICENSE\
**Notes**: acquire, target-fs, rdump, rgeoip, target-query, target-shell, target-dump, target-info, target-reg, target-dd, target-mount\
**State File**: [remnux.python3-packages.dissect](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/dissect.sls)

## time-decode

Decode and encode date and timestamps.

**Website**: [https://github.com/digitalsleuth/time\_decode](https://github.com/digitalsleuth/time_decode)\
**Author**: Corey Forman\
**License**: MIT License: [https://github.com/digitalsleuth/time\_decode/blob/master/LICENSE](https://github.com/digitalsleuth/time_decode/blob/master/LICENSE)\
**State File**: [remnux.python3-packages.time-decode](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/time-decode.sls)

## malwoverview

Query public repositories of malware data (e.g., VirusTotal, HybridAnalysis).

**Website**: [https://github.com/alexandreborges/malwoverview](https://github.com/alexandreborges/malwoverview)\
**Author**: Alexandre Borges\
**License**: GNU General Public License v3: [https://github.com/alexandreborges/malwoverview/blob/master/LICENSE](https://github.com/alexandreborges/malwoverview/blob/master/LICENSE)\
**Notes**: malwoverview, add API keys to \~/.malwapi.conf\
**State File**: [remnux.python3-packages.malwoverview](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/malwoverview.sls)

## ipwhois

Retrieve and parse whois data for IP addresses.

**Website**: [https://github.com/secynic/ipwhois](https://github.com/secynic/ipwhois)\
**Author**: Philip Hane\
**License**: BSD 2-Clause "Simplified" License: [https://github.com/secynic/ipwhois/blob/master/LICENSE.txt](https://github.com/secynic/ipwhois/blob/master/LICENSE.txt)\
**Notes**: ipwhois\_cli.py, ipwhois\_utils\_cli.py\
**State File**: [remnux.python3-packages.ipwhois](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/ipwhois.sls)

## VirusTotal API

Query and interact with VirusTotal using a command-line interface.

**Website**: [https://github.com/VirusTotal/vt-py](https://github.com/VirusTotal/vt-py)\
**Author**: VirusTotal\
**License**: Apache 2.0 ([https://github.com/VirusTotal/vt-py/blob/master/LICENSE)](https://github.com/VirusTotal/vt-py/blob/master/LICENSE))\
**Notes**: Only available on older version of REMnux based on Ubuntu 20.04 (Focal).\
**State File**: [remnux.python3-packages.virustotal-api](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/virustotal-api.sls)



## ioc\_writer

Python library that allows for basic creation and editing of OpenIOC objects.

**Website**: [https://github.com/mandiant/ioc\_writer](https://github.com/mandiant/ioc_writer)\
**Author**: William Gibb\
**License**: Apache License 2.0: [https://github.com/mandiant/ioc\_writer/blob/master/LICENSE](https://github.com/mandiant/ioc_writer/blob/master/LICENSE)\
**State File**: [remnux.python-packages.ioc-writer](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/ioc-writer.sls)

## shodan

Query Shodan, a search engine for internet-connected devices.

**Website**: [https://github.com/achillean/shodan-python/](https://github.com/achillean/shodan-python/)\
**Author**: John Matherly\
**License**: Custom, free license: [https://github.com/achillean/shodan-python/blob/master/LICENSE](https://github.com/achillean/shodan-python/blob/master/LICENSE)\
**State File**: [remnux.python-packages.shodan](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/shodan.sls)

## PyPDNS

Python library to query passive DNS services that follow the Passive DNS - Common Output Format

**Website**: [https://github.com/CIRCL/PyPDNS](https://github.com/CIRCL/PyPDNS)\
**Author**: Raphael Vinot, Alexandre Dulaunoy, CIRCL - Computer Incident Response Center Luxembourg\
**License**: Free, custom license: [https://github.com/CIRCL/PyPDNS/blob/master/LICENSE](https://github.com/CIRCL/PyPDNS/blob/master/LICENSE)\
**State File**: [remnux.python-packages.pypdns](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/pypdns.sls)

## pdnstool

Query passive DNS databases for DNS data.

**Website**: [https://github.com/chrislee35/passivedns-client](https://github.com/chrislee35/passivedns-client)\
**Author**: Chris Lee\
**License**: MIT License: [https://github.com/chrislee35/passivedns-client/blob/master/LICENSE.txt](https://github.com/chrislee35/passivedns-client/blob/master/LICENSE.txt)\
**State File**: [remnux.rubygems.pdnstool](https://github.com/REMnux/salt-states/blob/master/remnux/rubygems/pdnstool.sls)

## DeXRAY

Extract and decode data from antivirus quarantine files.

**Website**: [https://www.hexacorn.com/blog/category/software-releases/dexray/](https://www.hexacorn.com/blog/category/software-releases/dexray/)\
**Author**: Hexacorn\
**License**: Free; copyright by Hexacorn.com: [https://hexacorn.com/d/DeXRAY.pl](https://hexacorn.com/d/DeXRAY.pl)\
**Notes**: dexray\
**State File**: [remnux.scripts.dexray](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/dexray.sls)


## virustotal-submit

Submit files to VirusTotal.

**Website**: [https://blog.didierstevens.com/programs/virustotal-tools/](https://blog.didierstevens.com/programs/virustotal-tools/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**Notes**: virustotal-submit.py\
**State File**: [remnux.scripts.virustotal-submit](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/virustotal-submit.sls)

## virustotal-search

Search VirusTotal for file hashes.

**Website**: [https://blog.didierstevens.com/programs/virustotal-tools/](https://blog.didierstevens.com/programs/virustotal-tools/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**Notes**: virustotal-search.py\
**State File**: [remnux.scripts.virustotal-search](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/virustotal-search.sls)

## Scalpel

Carve contents out of binary files, such as partitions.

**Website**: [https://github.com/sleuthkit/scalpel](https://github.com/sleuthkit/scalpel)\
**Author**: Golden G. Richard III, Vassil Roussev\
**License**: Apache License 2.0: [https://github.com/sleuthkit/scalpel/blob/master/LICENSE-2.0.txt](https://github.com/sleuthkit/scalpel/blob/master/LICENSE-2.0.txt)\
**State File**: [remnux.packages.scalpel](https://github.com/REMnux/salt-states/blob/master/remnux/packages/scalpel.sls)

## nsrllookup

Look up MD5 file hashes in the NIST National Software Reference Library (NSRL).

**Website**: [https://github.com/rjhansen/nsrllookup](https://github.com/rjhansen/nsrllookup)\
**Author**: Robert J. Hansen: [https://twitter.com/robertjhansen](https://twitter.com/robertjhansen)\
**License**: ISC License: [https://github.com/rjhansen/nsrllookup/blob/master/LICENSE](https://github.com/rjhansen/nsrllookup/blob/master/LICENSE)\
**State File**: [remnux.packages.nsrllookup](https://github.com/REMnux/salt-states/blob/master/remnux/packages/nsrllookup.sls)

## Yara

Identify and classify malware samples using Yara rules.

**Website**: [https://virustotal.github.io/yara/](https://virustotal.github.io/yara/)\
**Author**: [https://github.com/VirusTotal/yara/blob/master/AUTHORS](https://github.com/VirusTotal/yara/blob/master/AUTHORS)\
**License**: BSD 3-Clause "New" or "Revised" License: [https://github.com/VirusTotal/yara/blob/master/COPYING](https://github.com/VirusTotal/yara/blob/master/COPYING)\
**Notes**: yara\
**State File**: [remnux.packages.yara](https://github.com/REMnux/salt-states/blob/master/remnux/packages/yara.sls)

## ioc_parser

Extract IOCs from security report PDFs.

**Website**: [https://github.com/buffer/ioc_parser](https://github.com/buffer/ioc_parser)\
**Author**: Armin Buescher\
**License**: MIT License: [https://github.com/buffer/ioc_parser/blob/master/LICENSE.txt](https://github.com/buffer/ioc_parser/blob/master/LICENSE.txt)\
**State File**: [remnux.python3-packages.ioc-parser](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/ioc-parser.sls)
