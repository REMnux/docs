---
description: Examine Static Properties
---

# General

## TrID

Identify file type using signatures.

**Website**: [https://mark0.net/soft-trid-e.html](https://mark0.net/soft-trid-e.html)  
**Author**: Marco Pontello  
**License**: Free, unknown license  
**Notes**: trid, tridupdate  
**State File**: [remnux.tools.trid](https://github.com/REMnux/salt-states/blob/master/remnux/tools/trid.sls)

## Yara Rules

Statically scan a file to identify common malicious capabilities.

**Website**: [https://github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules)  
**Author**: A group of IT security researchers: [https://twitter.com/yararules](https://twitter.com/yararules)  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/Yara-Rules/rules/blob/master/LICENSE](https://github.com/Yara-Rules/rules/blob/master/LICENSE)  
**Notes**: To scan a file using these rules, you can use the wrapper around Yara: `yara-rules FILE`, where `FILE` is the path to the file you wish to scan.  
**State File**: [remnux.tools.yara-rules](https://github.com/REMnux/salt-states/blob/master/remnux/tools/yara-rules.sls)

## ExifTool

Tool to read from, write to, and edit EXIF metadata of various file types

**Website**: [https://exiftool.org/](https://exiftool.org/)  
**Author**: Phil Harvey  
**License**: "This is free software; you can redistribute it and/or modify it under the same terms as Perl itself": [https://exiftool.org/\#license](https://exiftool.org/#license)  
**Notes**: exiftool  
**State File**: [remnux.perl-packages.exiftool](https://github.com/REMnux/salt-states/blob/master/remnux/perl-packages/exiftool.sls)

## DroidLysis

Perform static analysis of Android applications.

**Website**: [https://github.com/cryptax/droidlysis](https://github.com/cryptax/droidlysis)  
**Author**: cryptax  
**License**: MIT License: [https://github.com/cryptax/droidlysis/blob/master/LICENSE](https://github.com/cryptax/droidlysis/blob/master/LICENSE)  
**Notes**: droidlysis  
**State File**: [remnux.python3-packages.droidlysis](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/droidlysis.sls)

## zipdump.py

Analyze zip-compressed files.

**Website**: [https://blog.didierstevens.com/2020/07/27/update-zipdump-py-version-0-0-20/](https://blog.didierstevens.com/2020/07/27/update-zipdump-py-version-0-0-20/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**State File**: [remnux.scripts.zipdump](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/zipdump.sls)

## numbers-to-string.py <a id="numbers-to-string"></a>

Convert decimal numbers to strings.

**Website**: [https://blog.didierstevens.com/2020/12/12/update-numbers-to-string-py-version-0-0-11/](https://blog.didierstevens.com/2020/12/12/update-numbers-to-string-py-version-0-0-11/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**State File**: [remnux.scripts.numbers-to-string](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/numbers-to-string.sls)

## re-search.py

Search the file for built-in regular expressions of common suspicious artifacts.

**Website**: [https://blog.didierstevens.com/2021/05/23/update-re-search-py-version-0-0-17/](https://blog.didierstevens.com/2021/05/23/update-re-search-py-version-0-0-17/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**State File**: [remnux.scripts.re-search](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/re-search.sls)

## disitool

Manipulate embedded digital signatures.

**Website**: [https://blog.didierstevens.com/programs/disitool/](https://blog.didierstevens.com/programs/disitool/)  
**Author**: Didier Stevens  
**License**: Public Domain  
**Notes**: disitool.py  
**State File**: [remnux.scripts.disitool](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/disitool.sls)

## Name-That-Hash

Identify dfferent types of hashes.

**Website**: [https://github.com/HashPals/Name-That-Hash](https://github.com/HashPals/Name-That-Hash)  
**Author**: randon / Bee: [https://twitter.com/bee\_sec\_san](https://twitter.com/bee_sec_san)  
**License**: GNU General Public License \(GPL\) v3.0: \([https://github.com/HashPals/Name-That-Hash/blob/main/LICENSE](https://github.com/HashPals/Name-That-Hash/blob/main/LICENSE)\)  
**Notes**: nth  
**State File**: [remnux.python3-packages.name-that-hash](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/name-that-hash.sls)

## Hash ID

Identify dfferent types of hashes.

**Website**: [https://github.com/blackploit/hash-identifier](https://github.com/blackploit/hash-identifier)  
**Author**: Zion3R  
**License**: GNU General Public License \(GPL\) v3  
**Notes**: hash-id.py  
**State File**: [remnux.scripts.hash-identifier](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/hash-identifier.sls)

## signsrch

Find patterns of common encryption, compression, or encoding algorithms

**Website**: [http://aluigi.altervista.org/mytoolz.htm](http://aluigi.altervista.org/mytoolz.htm)  
**Author**: Luigi Auriemma  
**License**: Free, unknown license  
**State File**: [remnux.packages.signsrch](https://github.com/REMnux/salt-states/blob/master/remnux/packages/signsrch.sls)

## ssdeep

Compute Context Triggered Piecewise Hashes \(CTPH\), also known as fuzzy hashes.

**Website**: [https://ssdeep-project.github.io/ssdeep/index.html](https://ssdeep-project.github.io/ssdeep/index.html)  
**Author**: Jesse Kornblum, Helmut Grohne, Tsukasa OI  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/ssdeep-project/ssdeep/blob/master/COPYING](https://github.com/ssdeep-project/ssdeep/blob/master/COPYING)  
**State File**: [remnux.packages.ssdeep](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ssdeep.sls)

## 7-Zip

Compress and decompress files using a variety of algorithms.

**Website**: [https://www.7-zip.org](https://www.7-zip.org)  
**Author**: Igor Pavlov  
**License**: GNU Lesser General Public License \(LGPL\)  
**Notes**: 7z, 7za, 7zr  
**State File**: [remnux.packages.7zip](https://github.com/REMnux/salt-states/blob/master/remnux/packages/7zip.sls)

## wxHexEditor

Hex editor

**Website**: [https://sourceforge.net/projects/wxhexeditor/](https://sourceforge.net/projects/wxhexeditor/)  
**Author**: Unknown  
**License**: GNU General Public License \(GPL\) v2: [https://sourceforge.net/p/wxhexeditor/code/HEAD/tree/trunk/docs/GPL.txt](https://sourceforge.net/p/wxhexeditor/code/HEAD/tree/trunk/docs/GPL.txt)  
**State File**: [remnux.packages.wxhexeditor](https://github.com/REMnux/salt-states/blob/master/remnux/packages/wxhexeditor.sls)

## ClamAV

Scan files for malware signatures.

**Website**: [https://www.clamav.net](https://www.clamav.net)  
**Author**: [https://www.clamav.net/about](https://www.clamav.net/about)  
**License**: GNU General Public License \(GPL\): [https://www.clamav.net/about](https://www.clamav.net/about)  
**Notes**: clamscan, freshclam  
**State File**: [remnux.packages.clamav-daemon](https://github.com/REMnux/salt-states/blob/master/remnux/packages/clamav-daemon.sls)

## bulk\_extractor

Extract interesting strings from binary files.

**Website**: [https://github.com/simsong/bulk\_extractor/](https://github.com/simsong/bulk_extractor/)  
**Author**: [https://github.com/simsong/bulk\_extractor/blob/master/AUTHORS](https://github.com/simsong/bulk_extractor/blob/master/AUTHORS)  
**License**: Portions Public Domain, portions MIT License: [https://github.com/simsong/bulk\_extractor/blob/master/LICENSE.md](https://github.com/simsong/bulk_extractor/blob/master/LICENSE.md)  
**State File**: [remnux.packages.bulk-extractor](https://github.com/REMnux/salt-states/blob/master/remnux/packages/bulk-extractor.sls)

## Hachoir

View, edit, and carve contents of various binary file types.

**Website**: [https://github.com/vstinner/hachoir](https://github.com/vstinner/hachoir)  
**Author**: [https://hachoir.readthedocs.io/en/latest/authors.html](https://hachoir.readthedocs.io/en/latest/authors.html)  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/vstinner/hachoir/blob/master/COPYING](https://github.com/vstinner/hachoir/blob/master/COPYING)  
**Notes**: hachoir-grep, hachoir-metadata, hachoir-strip, hachoir-wx  
**State File**: [remnux.python3-packages.hachoir](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/hachoir.sls)

## Sleuth Kit

Analyze disk images and recover files from them.

**Website**: [https://www.sleuthkit.org/sleuthkit](https://www.sleuthkit.org/sleuthkit)  
**Author**: Brian Carrier, and others  
**License**: IBM Public License, Common Public License, GNU General Public License \(GPL\) v2: [https://www.sleuthkit.org/sleuthkit/licenses.php](https://www.sleuthkit.org/sleuthkit/licenses.php)  
**Notes**: For a listing of commands, see [http://wiki.sleuthkit.org/index.php?title=TSK\_Tool\_Overview](http://wiki.sleuthkit.org/index.php?title=TSK_Tool_Overview)  
**State File**: [remnux.packages.sleuthkit](https://github.com/REMnux/salt-states/blob/master/remnux/packages/sleuthkit.sls)

## binwalk

Extract and analyze firmware images.

**Website**: [https://github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)  
**Author**: Craig Heffner, ReFirmLabs  
**License**: IBM Public License, Common Public License, GNU General Public License \(GPL\) v2: [https://www.sleuthkit.org/sleuthkit/licenses.php](https://www.sleuthkit.org/sleuthkit/licenses.php)  
**Notes**: MIT License: [https://github.com/ReFirmLabs/binwalk/blob/master/LICENSE](https://github.com/ReFirmLabs/binwalk/blob/master/LICENSE)  
**State File**: [remnux.packages.binwalk](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binwalk.sls)

## file

Identify file type using "magic" numbers.

**Website**: [http://astron.com/pub/file/README](http://astron.com/pub/file/README)  
**Author**: Ian F. Darwin, Christos Zoulas  
**License**: BSD 2-Clause "Alike" License: [https://github.com/file/file/blob/master/COPYING](https://github.com/file/file/blob/master/COPYING)  
**State File**: [remnux.packages.file](https://github.com/REMnux/salt-states/blob/master/remnux/packages/file.sls)

