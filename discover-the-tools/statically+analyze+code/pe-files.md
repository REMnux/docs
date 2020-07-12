# PE Files

## binee \(Binary Emulation Environment\)

Analyze I/O operations of a suspicious PE file by emulating its execution.

**Website**: [https://github.com/carbonblack/binee](https://github.com/carbonblack/binee)  
**Author**: Carbon Black, Kyle Gwinnup, John Holowczak  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/carbonblack/binee/blob/master/LICENSE](https://github.com/carbonblack/binee/blob/master/LICENSE)  
**Notes**: Before using this tool, place Windows 32-bit DLLs that your file requires in /opt/binee-files/system32; check which DLLs you might need by examining the import table using the "-i" parameter.  
**State File**: [remnux.packages.binee](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binee.sls)

