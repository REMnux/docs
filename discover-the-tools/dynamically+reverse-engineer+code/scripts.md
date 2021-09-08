---
description: Dynamically Reverse-Engineer Code
---

# Scripts

## SpiderMonkey \(Patched\)

Execute and deobfuscate JavaScript using a patched version of Mozilla's standalone JavaScript engine.

**Website**: [https://blog.didierstevens.com/2018/04/19/update-patched-spidermonkey/](https://blog.didierstevens.com/2018/04/19/update-patched-spidermonkey/)  
**Author**: SpiderMonkey by Mozilla Foundation, patched by Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Mozilla Public License 2.0: [https://github.com/mozilla/treeherder/blob/master/LICENSE.txt](https://github.com/mozilla/treeherder/blob/master/LICENSE.txt)  
**Notes**: js-ascii, js-file  
**State File**: [remnux.tools.js-patched](https://github.com/REMnux/salt-states/blob/master/remnux/tools/js-patched.sls)

## objects.js

Emulate common browser and PDF viewer objects, methods, and properties when deobfuscating JavaScript.

**Website**: [https://github.com/REMnux/salt-states/blob/master/remnux/config/objects/objects.js](https://github.com/REMnux/salt-states/blob/master/remnux/config/objects/objects.js)  
**Author**: Lenny Zeltser  
**License**: Public Domain  
**Notes**: The file is in /usr/local/share/remnux  
**State File**: [remnux.config.objects.init](https://github.com/REMnux/salt-states/blob/master/remnux/config/objects/init.sls)

## STPyV8

Python3 and JavaScript interop engine, fork of the original PyV8 project

**Website**: [https://github.com/area1/stpyv8](https://github.com/area1/stpyv8)  
**Author**: Area1 Security  
**License**: Apache License 2.0: [https://github.com/area1/stpyv8/blob/master/LICENSE.txt](https://github.com/area1/stpyv8/blob/master/LICENSE.txt)  
**State File**: [remnux.python3-packages.stpyv8](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/stpyv8.sls)

## JStillery

Deobfuscate JavaScript scripts using AST and Partial Evaluation techniques.

**Website**: [https://github.com/mindedsecurity/jstillery](https://github.com/mindedsecurity/jstillery)  
**Author**: Stefano Di Paola, Minded Security: [http://www.mindedsecurity.com](http://www.mindedsecurity.com)  
**License**: GNU General Public License \(GPL\) v3: [https://github.com/mindedsecurity/JStillery/blob/master/LICENSE](https://github.com/mindedsecurity/JStillery/blob/master/LICENSE)  
**Notes**: jstillery  
**State File**: [remnux.node-packages.jstillery](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/jstillery.sls)

## box-js

Analyze suspicious JavaScript scripts.

**Website**: [https://github.com/CapacitorSet/box-js](https://github.com/CapacitorSet/box-js)  
**Author**: CapacitorSet  
**License**: MIT License: [https://github.com/CapacitorSet/box-js/blob/master/LICENSE](https://github.com/CapacitorSet/box-js/blob/master/LICENSE)  
**Notes**: box-js, box-export  
**State File**: [remnux.node-packages.box-js](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/box-js.sls)

## SpiderMonkey

Execute and deobfuscate JavaScript using Mozilla's standalone JavaScript engine.

**Website**: [https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)  
**Author**: Mozilla Foundation  
**License**: Mozilla Public License 2.0: [https://github.com/mozilla/treeherder/blob/master/LICENSE.txt](https://github.com/mozilla/treeherder/blob/master/LICENSE.txt)  
**Notes**: js  
**State File**: [remnux.packages.spidermonkey](https://github.com/REMnux/salt-states/blob/master/remnux/packages/spidermonkey.sls)

## Rhino Debugger

GUI JavaScript debugger

**Website**: [https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Debugger](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/Debugger)  
**Author**: Mozilla Project  
**License**: Mozilla Public License v2.0: [https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/License](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Rhino/License)  
**Notes**: rhino-debugger  
**State File**: [remnux.packages.rhino](https://github.com/REMnux/salt-states/blob/master/remnux/packages/rhino.sls)

## PowerShell Core

Run PowerShell scripts and commands.

**Website**: [https://github.com/powershell/powershell](https://github.com/powershell/powershell)  
**Author**: Microsoft Corporation  
**License**: MIT License: [https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt](https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt)  
**Notes**: pwsh  
**State File**: [remnux.packages.powershell](https://github.com/REMnux/salt-states/blob/master/remnux/packages/powershell.sls)

