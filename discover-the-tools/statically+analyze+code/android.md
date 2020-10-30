---
description: Statically Analyze Code
---

# Android

## JADX

Generate Java source code from Dalvik Executable \(dex\) and Android APK files

**Website**: [https://github.com/skylot/jadx](https://github.com/skylot/jadx)  
**Author**: Skylot  
**License**: Apache License 2.0: [https://github.com/skylot/jadx/blob/master/LICENSE](https://github.com/skylot/jadx/blob/master/LICENSE), also see [https://github.com/skylot/jadx/blob/master/NOTICE](https://github.com/skylot/jadx/blob/master/NOTICE)  
**Notes**: jadx, jadx-gui  
**State File**: [remnux.tools.jadx](https://github.com/REMnux/salt-states/blob/master/remnux/tools/jadx.sls)

## apktool

Reverse-engineer Android APK files.

**Website**: [https://ibotpeaches.github.io/Apktool/](https://ibotpeaches.github.io/Apktool/)  
**Author**: Connor Tumbleson, Ryszard Wisniewski  
**License**: Apache License 2.0: [https://github.com/iBotPeaches/Apktool/blob/master/LICENSE](https://github.com/iBotPeaches/Apktool/blob/master/LICENSE)  
**State File**: [remnux.tools.apktool](https://github.com/REMnux/salt-states/blob/master/remnux/tools/apktool.sls)

## DroidLysis

Perform static analysis of Android applications.

**Website**: [https://github.com/cryptax/droidlysis](https://github.com/cryptax/droidlysis)  
**Author**: cryptax  
**License**: MIT License: [https://github.com/cryptax/droidlysis/blob/master/LICENSE](https://github.com/cryptax/droidlysis/blob/master/LICENSE)  
**Notes**: droidlysis  
**State File**: [remnux.python3-packages.droidlysis](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/droidlysis.sls)

## androguard

Examine Android files.

**Website**: [https://github.com/androguard/androguard](https://github.com/androguard/androguard)  
**Author**: Anthony Desnos, Geoffroy GueGuen  
**License**: Apache License 2.0: [https://github.com/androguard/androguard/blob/master/LICENCE-2.0](https://github.com/androguard/androguard/blob/master/LICENCE-2.0)  
**Notes**: androarsc.py, androauto.py, androaxml.py, androcg.py, androdd.py, androdis.py, androguard, androgui.py, androlyze.py, androsign.py  
**State File**: [remnux.python3-packages.androguard](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/androguard.sls)

## AndroidProjectCreator

Convert an Android APK application file into an Android Studio project for easier analysis.

**Website**: [https://maxkersten.nl/projects/androidprojectcreator](https://maxkersten.nl/projects/androidprojectcreator)  
**Author**: Max Kersten: [https://twitter.com/LibraAnalysis](https://twitter.com/LibraAnalysis)  
**License**: GNU General Public License \(GPL\) v3: [https://github.com/ThisIsLibra/AndroidProjectCreator/blob/master/LICENSE](https://github.com/ThisIsLibra/AndroidProjectCreator/blob/master/LICENSE)  
**Notes**: Use AndroidProjectCreator to run the tool. Before running it for the first time, execute `AndroidProjectCreator -compactInstall` to download the latest depenencies. Use Android Studio to examine the output of the tool.  
**State File**: [remnux.packages.android-project-creator](https://github.com/REMnux/salt-states/blob/master/remnux/packages/android-project-creator.sls)

## baksmali

Disassembler for the dex format used by Dalvik, Android's Java VM implementation.

**Website**: [https://bitbucket.org/JesusFreke/smali](https://bitbucket.org/JesusFreke/smali)  
**Author**: Ben Gruver  
**License**: Free, unknown license  
**State File**: [remnux.packages.baksmali](https://github.com/REMnux/salt-states/blob/master/remnux/packages/baksmali.sls)

## dex2jar

Examine Dalvik Executable \(dex\) files.

**Website**: [https://github.com/pxb1988/dex2jar](https://github.com/pxb1988/dex2jar)  
**Author**: Panxiaobo  
**License**: Apache License 2.0: [https://github.com/pxb1988/dex2jar/blob/2.x/LICENSE.txt](https://github.com/pxb1988/dex2jar/blob/2.x/LICENSE.txt)  
**Notes**: dex-tools  
**State File**: [remnux.packages.dex2jar](https://github.com/REMnux/salt-states/blob/master/remnux/packages/dex2jar.sls)

