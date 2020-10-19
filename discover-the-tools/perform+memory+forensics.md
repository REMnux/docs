---
description: Discover the Tools
---

# Perform Memory Forensics

## Volatility 3

Memory forensics tool and framework

**Website**: [https://github.com/volatilityfoundation/volatility3](https://github.com/volatilityfoundation/volatility3)  
**Author**: The Volatility Foundation  
**License**: Volatility Software License: [https://github.com/volatilityfoundation/volatility3/blob/master/LICENSE.txt](https://github.com/volatilityfoundation/volatility3/blob/master/LICENSE.txt)  
**Notes**: Invoke using: vol3, volshell3. Before using, download symbols by following the links from [https://github.com/volatilityfoundation/volatility3\#symbol-tables](https://github.com/volatilityfoundation/volatility3#symbol-tables) and place them in `/usr/local/lib/python3.6/dist-packages/volatility/symbols`.  
**State File**: [remnux.python3-packages.volatility3](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/volatility3.sls)

## Volatility Framework

Memory forensics tool and framework

**Website**: [https://github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)  
**Author**: [https://github.com/volatilityfoundation/volatility/blob/2.6.1/AUTHORS.txt](https://github.com/volatilityfoundation/volatility/blob/2.6.1/AUTHORS.txt)  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/volatilityfoundation/volatility/blob/2.6.1/LICENSE.txt](https://github.com/volatilityfoundation/volatility/blob/2.6.1/LICENSE.txt)  
**Notes**: vol.py  
**This file is based directly on https**: //github.com/teamdfir/sift-saltstack/blob/master/sift/python-packages/volatility.sls  
**State File**: [remnux.python-packages.volatility](https://github.com/REMnux/salt-states/blob/master/remnux/python-packages/volatility.sls)

## linux\_mem\_diff\_tool

Compare two memory images of Linux systems by using Volatility.

**Website**: [https://github.com/monnappa22/linux\_mem\_diff\_tool](https://github.com/monnappa22/linux_mem_diff_tool)  
**Author**: Monnappa K A  
**License**: Free, unknown license  
**Notes**: linux\_mem\_diff.py  
**State File**: [remnux.scripts.linuxmemdiff](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/linuxmemdiff.sls)

## AESKeyFinder

Find 128-bit and 256-bit AES keys in a memory image.

**Website**: [https://citp.princeton.edu/our-work/memory/](https://citp.princeton.edu/our-work/memory/)  
**Author**: Nadia Heninger, Alex Halderman  
**License**: Free, unknown license  
**Notes**: aeskeyfind  
**State File**: [remnux.packages.aeskeyfind](https://github.com/REMnux/salt-states/blob/master/remnux/packages/aeskeyfind.sls)

## bulk\_extractor

Extract interesting strings from binary files.

**Website**: [https://github.com/simsong/bulk\_extractor/](https://github.com/simsong/bulk_extractor/)  
**Author**: [https://github.com/simsong/bulk\_extractor/blob/master/AUTHORS](https://github.com/simsong/bulk_extractor/blob/master/AUTHORS)  
**License**: Portions Public Domain, portions MIT License: [https://github.com/simsong/bulk\_extractor/blob/master/LICENSE.md](https://github.com/simsong/bulk_extractor/blob/master/LICENSE.md)  
**State File**: [remnux.packages.bulk-extractor](https://github.com/REMnux/salt-states/blob/master/remnux/packages/bulk-extractor.sls)

## RSAKeyFinder

Find BER-encoded RSA private keys in a memory image.

**Website**: [https://citp.princeton.edu/our-work/memory/](https://citp.princeton.edu/our-work/memory/)  
**Author**: Nadia Heninger, Alex Halderman  
**License**: Free, unknown license  
**Notes**: rsakeyfind  
**State File**: [remnux.packages.rsakeyfind](https://github.com/REMnux/salt-states/blob/master/remnux/packages/rsakeyfind.sls)

