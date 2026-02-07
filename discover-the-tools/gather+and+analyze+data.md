---
description: Discover the Tools
---

# Gather and Analyze Data

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
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**Notes**: virustotal-submit.py\
**State File**: [remnux.scripts.virustotal-submit](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/virustotal-submit.sls)

## virustotal-search

Search VirusTotal for file hashes.

**Website**: [https://blog.didierstevens.com/programs/virustotal-tools/](https://blog.didierstevens.com/programs/virustotal-tools/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
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
**Author**: Robert J. Hansen: [https://x.com/robertjhansen](https://x.com/robertjhansen)\
**License**: ISC License: [https://github.com/rjhansen/nsrllookup/blob/master/LICENSE](https://github.com/rjhansen/nsrllookup/blob/master/LICENSE)\
**State File**: [remnux.packages.nsrllookup](https://github.com/REMnux/salt-states/blob/master/remnux/packages/nsrllookup.sls)

## Yara

Identify and classify malware samples using Yara rules.

**Website**: [https://virustotal.github.io/yara/](https://virustotal.github.io/yara/)\
**Author**: [https://github.com/VirusTotal/yara/blob/master/AUTHORS](https://github.com/VirusTotal/yara/blob/master/AUTHORS)\
**License**: BSD 3-Clause "New" or "Revised" License: [https://github.com/VirusTotal/yara/blob/master/COPYING](https://github.com/VirusTotal/yara/blob/master/COPYING)\
**Notes**: yara\
**State File**: [remnux.packages.yara](https://github.com/REMnux/salt-states/blob/master/remnux/packages/yara.sls)

## ioc\_parser

Extract IOCs from security report PDFs.

**Website**: [https://github.com/buffer/ioc\_parser](https://github.com/buffer/ioc_parser)\
**Author**: Armin Buescher\
**License**: MIT License: [https://github.com/buffer/ioc\_parser/blob/master/LICENSE.txt](https://github.com/buffer/ioc_parser/blob/master/LICENSE.txt)\
**State File**: [remnux.python3-packages.ioc-parser](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/ioc-parser.sls)

## dnslib

Python library to encode/decode DNS wire-format packets.

**Website**: [https://github.com/paulc/dnslib](https://github.com/paulc/dnslib)\
**Author**: Paul Chakravarti\
**License**: BSD 2-Clause "Simplified" License: [https://github.com/paulc/dnslib/blob/master/LICENSE](https://github.com/paulc/dnslib/blob/master/LICENSE)\
**Notes**: Library - /opt/dnslib/bin/python3 - import dnslib\
**State File**: [remnux.python3-packages.dnslib](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/dnslib.sls)

