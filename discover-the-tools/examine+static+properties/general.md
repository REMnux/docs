---
description: Examine Static Properties
---

# General

## TrID

Identify file type using signatures.

**Website**: [https://mark0.net/soft-trid-e.html](https://mark0.net/soft-trid-e.html)\
**Author**: Marco Pontello\
**License**: Free, unknown license\
**Notes**: trid, tridupdate\
**State File**: [remnux.tools.trid](https://github.com/REMnux/salt-states/blob/master/remnux/tools/trid.sls)

## Magika

Identify file type using signatures.

**Website**: [https://google.github.io/magika](https://google.github.io/magika/)\
**Author**: Google\
**License**: Apache License 2.0 ([https://github.com/google/magika/blob/main/LICENSE](https://github.com/google/magika/blob/main/LICENSE))\
**State File**: [remnux.python3-packages.magika](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/magika.sls)

## Yara Rules

Scan a file with YARA rules to identify capabilities and behaviors (packer detection, anti-debug, networking).

**Website**: [https://github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules)\
**Author**: A group of IT security researchers: [https://x.com/yararules](https://x.com/yararules)\
**License**: GNU General Public License (GPL) v2: [https://github.com/Yara-Rules/rules/blob/master/LICENSE](https://github.com/Yara-Rules/rules/blob/master/LICENSE)\
**Notes**: To scan a file using these rules, you can use the wrapper around Yara: `yara-rules FILE`, where `FILE` is the path to the file you wish to scan. For malware family identification, also try `yara-forge FILE`.\
**State File**: [remnux.tools.yara-rules](https://github.com/REMnux/salt-states/blob/master/remnux/tools/yara-rules.sls)



## Detect-It-Easy

Determine types of files and examine file properties.

**Website**: [https://github.com/horsicq/Detect-It-Easy](https://github.com/horsicq/Detect-It-Easy)\
**Author**: hors: [https://x.com/horsicq](https://x.com/horsicq)\
**License**: MIT License: [https://github.com/horsicq/Detect-It-Easy/blob/master/LICENSE](https://github.com/horsicq/Detect-It-Easy/blob/master/LICENSE)\
**Notes**: GUI tool: `die`, command-line tool: `diec`.\
**State File**: [remnux.tools.detect-it-easy](https://github.com/REMnux/salt-states/blob/master/remnux/tools/detect-it-easy.sls)


## ExifTool

Tool to read from, write to, and edit EXIF metadata of various file types.

**Website**: [https://exiftool.org/](https://exiftool.org/)\
**Author**: Phil Harvey\
**License**: "This is free software; you can redistribute it and/or modify it under the same terms as Perl itself": [https://exiftool.org/#license](https://exiftool.org/#license)\
**Notes**: exiftool\
**State File**: [remnux.perl-packages.exiftool](https://github.com/REMnux/salt-states/blob/master/remnux/perl-packages/exiftool.sls)


## DroidLysis

Perform static analysis of Android applications.

**Website**: [https://github.com/cryptax/droidlysis](https://github.com/cryptax/droidlysis)\
**Author**: cryptax\
**License**: MIT License: [https://github.com/cryptax/droidlysis/blob/master/LICENSE](https://github.com/cryptax/droidlysis/blob/master/LICENSE)\
**Notes**: droidlysis\
**State File**: [remnux.python3-packages.droidlysis](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/droidlysis.sls)

## msitools <a href="#msitools" id="msitools"></a>

Create, inspect and extract Windows Installer (.msi) files.

**Website**: [https://wiki.gnome.org/msitools](https://wiki.gnome.org/msitools)\
**Author**: Paolo Bonzini, Marc-Andre Lureau: [https://gitlab.gnome.org/GNOME/msitools/-/blob/master/AUTHORS](https://gitlab.gnome.org/GNOME/msitools/-/blob/master/AUTHORS)\
**License**: GNU Lesser General Public License (LGPL) v2.1 or later: [https://gitlab.gnome.org/GNOME/msitools/-/blob/master/copyright](https://gitlab.gnome.org/GNOME/msitools/-/blob/master/copyright)\
**State File**: [remnux.packages.msitools](https://github.com/REMnux/salt-states/blob/master/remnux/packages/msitools.sls)

## numbers-to-string.py <a href="#numbers-to-string" id="numbers-to-string"></a>

Convert decimal numbers to strings.

**Website**: [https://blog.didierstevens.com/2020/12/12/update-numbers-to-string-py-version-0-0-11/](https://blog.didierstevens.com/2020/12/12/update-numbers-to-string-py-version-0-0-11/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.numbers-to-string](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/numbers-to-string.sls)

## re-search.py

Search the file for built-in regular expressions of common suspicious artifacts.

**Website**: [https://blog.didierstevens.com/2021/05/23/update-re-search-py-version-0-0-17/](https://blog.didierstevens.com/2021/05/23/update-re-search-py-version-0-0-17/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.re-search](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/re-search.sls)

## disitool

Manipulate embedded digital signatures.

**Website**: [https://blog.didierstevens.com/programs/disitool/](https://blog.didierstevens.com/programs/disitool/)\
**Author**: Didier Stevens\
**License**: Public Domain\
**Notes**: disitool.py\
**State File**: [remnux.scripts.disitool](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/disitool.sls)

## Name-That-Hash

Identify different types of hashes.

**Website**: [https://github.com/HashPals/Name-That-Hash](https://github.com/HashPals/Name-That-Hash)\
**Author**: Brandon / Bee: [https://x.com/bee_sec_san](https://x.com/bee_sec_san)\
**License**: GNU General Public License (GPL) v3.0: ([https://github.com/HashPals/Name-That-Hash/blob/main/LICENSE)](https://github.com/HashPals/Name-That-Hash/blob/main/LICENSE))\
**Notes**: nth\
**State File**: [remnux.python3-packages.name-that-hash](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/name-that-hash.sls)


## Hash ID

Identify different types of hashes.

**Website**: [https://github.com/blackploit/hash-identifier](https://github.com/blackploit/hash-identifier)\
**Author**: Zion3R\
**License**: GNU General Public License (GPL) v3\
**Notes**: hash-id.py\
**State File**: [remnux.scripts.hash-identifier](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/hash-identifier.sls)

## signsrch

Find patterns of common encryption, compression, or encoding algorithms.

**Website**: [http://aluigi.altervista.org/mytoolz.htm](http://aluigi.altervista.org/mytoolz.htm)\
**Author**: Luigi Auriemma\
**License**: Free, unknown license\
**State File**: [remnux.packages.signsrch](https://github.com/REMnux/salt-states/blob/master/remnux/packages/signsrch.sls)


## ssdeep

Compute Context Triggered Piecewise Hashes (CTPH), also known as fuzzy hashes.

**Website**: [https://ssdeep-project.github.io/ssdeep/index.html](https://ssdeep-project.github.io/ssdeep/index.html)\
**Author**: Jesse Kornblum, Helmut Grohne, Tsukasa OI\
**License**: GNU General Public License (GPL) v2: [https://github.com/ssdeep-project/ssdeep/blob/master/COPYING](https://github.com/ssdeep-project/ssdeep/blob/master/COPYING)\
**State File**: [remnux.packages.ssdeep](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ssdeep.sls)

## 7-Zip

Compress and decompress files using a variety of algorithms.

**Website**: [https://www.7-zip.org](https://www.7-zip.org)\
**Author**: Igor Pavlov\
**License**: GNU Lesser General Public License (LGPL)\
**Notes**: 7-Zip standard: 7z, 7za, 7zr. For latest alpha version, use 7zz instead of 7z.\
**State File**: [remnux.packages.7zip](https://github.com/REMnux/salt-states/blob/master/remnux/packages/7zip.sls)

## wxHexEditor

Hex editor.

**Website**: [https://sourceforge.net/projects/wxhexeditor/](https://sourceforge.net/projects/wxhexeditor/)\
**Author**: Unknown\
**License**: GNU General Public License (GPL) v2: [https://sourceforge.net/p/wxhexeditor/code/HEAD/tree/trunk/docs/GPL.txt](https://sourceforge.net/p/wxhexeditor/code/HEAD/tree/trunk/docs/GPL.txt)\
**State File**: [remnux.packages.wxhexeditor](https://github.com/REMnux/salt-states/blob/master/remnux/packages/wxhexeditor.sls)


## ClamAV

Scan files for malware signatures.

**Website**: [https://www.clamav.net](https://www.clamav.net)\
**Author**: [https://www.clamav.net/about](https://www.clamav.net/about)\
**License**: GNU General Public License (GPL): [https://www.clamav.net/about](https://www.clamav.net/about)\
**Notes**: clamscan, freshclam\
**State File**: [remnux.packages.clamav-daemon](https://github.com/REMnux/salt-states/blob/master/remnux/packages/clamav-daemon.sls)

## Hachoir

View, edit, and carve contents of various binary file types.

**Website**: [https://github.com/vstinner/hachoir](https://github.com/vstinner/hachoir)\
**Author**: [https://hachoir.readthedocs.io/en/latest/authors.html](https://hachoir.readthedocs.io/en/latest/authors.html)\
**License**: GNU General Public License (GPL) v2: [https://github.com/vstinner/hachoir/blob/master/COPYING](https://github.com/vstinner/hachoir/blob/master/COPYING)\
**Notes**: hachoir-grep, hachoir-metadata, hachoir-strip, hachoir-wx\
**State File**: [remnux.python3-packages.hachoir](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/hachoir.sls)

## Sleuth Kit

Analyze disk images and recover files from them.

**Website**: [https://www.sleuthkit.org/sleuthkit](https://www.sleuthkit.org/sleuthkit)\
**Author**: Brian Carrier, and others\
**License**: IBM Public License, Common Public License, GNU General Public License (GPL) v2: [https://www.sleuthkit.org/sleuthkit/licenses.php](https://www.sleuthkit.org/sleuthkit/licenses.php)\
**Notes**: For a listing of commands, see [http://wiki.sleuthkit.org/index.php?title=TSK\_Tool\_Overview](http://wiki.sleuthkit.org/index.php?title=TSK\_Tool\_Overview)\
**State File**: [remnux.packages.sleuthkit](https://github.com/REMnux/salt-states/blob/master/remnux/packages/sleuthkit.sls)

## binwalk

Extract and analyze firmware images.

**Website**: [https://github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)\
**Author**: Craig Heffner, ReFirmLabs\
**License**: IBM Public License, Common Public License, GNU General Public License (GPL) v2: [https://www.sleuthkit.org/sleuthkit/licenses.php](https://www.sleuthkit.org/sleuthkit/licenses.php)\
**Notes**: MIT License: [https://github.com/ReFirmLabs/binwalk/blob/master/LICENSE](https://github.com/ReFirmLabs/binwalk/blob/master/LICENSE)\
**State File**: [remnux.packages.binwalk](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binwalk.sls)

## file

Identify file type using "magic" numbers.

**Website**: [http://astron.com/pub/file/README](http://astron.com/pub/file/README)\
**Author**: Ian F. Darwin, Christos Zoulas\
**License**: BSD 2-Clause Simplified License: [https://github.com/file/file/blob/master/COPYING](https://github.com/file/file/blob/master/COPYING)\
**State File**: [remnux.packages.file](https://github.com/REMnux/salt-states/blob/master/remnux/packages/file.sls)


## bulk_extractor

Extract interesting strings from binary files.

**Website**: [https://github.com/simsong/bulk_extractor/](https://github.com/simsong/bulk_extractor/)\
**Author**: [https://github.com/simsong/bulk_extractor/blob/master/AUTHORS](https://github.com/simsong/bulk_extractor/blob/master/AUTHORS)\
**License**: Portions Public Domain, portions MIT License: [https://github.com/simsong/bulk_extractor/blob/master/LICENSE.md](https://github.com/simsong/bulk_extractor/blob/master/LICENSE.md)\
**State File**: [remnux.packages.bulk-extractor](https://github.com/REMnux/salt-states/blob/master/remnux/packages/bulk-extractor.sls)

## thefuzz

Fuzzy String Matching in Python.

**Website**: [https://github.com/seatgeek/thefuzz](https://github.com/seatgeek/thefuzz)\
**Author**: SeatGeek\
**License**: MIT License ([https://github.com/seatgeek/thefuzz/blob/master/LICENSE.txt)](https://github.com/seatgeek/thefuzz/blob/master/LICENSE.txt))\
**Notes**: Updated implementation of fuzzywuzzy\
**State File**: [remnux.python3-packages.thefuzz](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/thefuzz.sls)


## strings.py

Extract ASCII and Unicode strings from binary files with length sorting and filtering.

**Website**: [https://blog.didierstevens.com/2020/12/19/update-strings-py-version-0-0-6/](https://blog.didierstevens.com/2020/12/19/update-strings-py-version-0-0-6/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.didier-stevens-scripts](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/didier-stevens-scripts.sls)

## file-magic.py

Identify file types using the Python magic module.

**Website**: [https://blog.didierstevens.com/2018/07/11/new-tool-file-magic-py/](https://blog.didierstevens.com/2018/07/11/new-tool-file-magic-py/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.didier-stevens-scripts](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/didier-stevens-scripts.sls)

## YARA-Forge Rules

Scan files with curated YARA rules from 45+ sources for malware family identification.

**Website**: [https://yarahq.github.io/](https://yarahq.github.io/)\
**Author**: Florian Roth: [https://x.com/cyb3rops](https://x.com/cyb3rops)\
**License**: Various (see individual rules); Elastic rules excluded\
**Notes**: Run `yara-forge FILE` to identify malware families.\
**State File**: [remnux.tools.yara-forge](https://github.com/REMnux/salt-states/blob/master/remnux/tools/yara-forge.sls)

