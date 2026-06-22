# Scripts

## JS Beautifier

Reformat JavaScript scripts for easier analysis.

**Website**: [https://beautifier.io/](https://beautifier.io/)\
**Author**: Einar Lielmanis, Liam Newman, and contributors\
**License**: MIT License: [https://github.com/beautify-web/js-beautify/blob/master/LICENSE](https://github.com/beautify-web/js-beautify/blob/master/LICENSE)\
**Notes**: js-beautify\
**State File**: [remnux.python3-packages.jsbeautifier](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/jsbeautifier.sls)

## decode-vbe.py

Decode encoded VBS scripts (VBE).

**Website**: [https://blog.didierstevens.com/2016/03/29/decoding-vbe/](https://blog.didierstevens.com/2016/03/29/decoding-vbe/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.didier-stevens-scripts](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/didier-stevens-scripts.sls)

## AutoIt-Ripper

Extract AutoIt scripts embedded in PE binaries.

**Website**: [https://github.com/nazywam/AutoIt-Ripper](https://github.com/nazywam/AutoIt-Ripper)\
**Author**: Michał Praszmo: [https://x.com/nazywam](https://x.com/nazywam)\
**License**: MIT License: [https://github.com/nazywam/AutoIt-Ripper/blob/master/LICENSE](https://github.com/nazywam/AutoIt-Ripper/blob/master/LICENSE)\
**Notes**: autoit-ripper\
**State File**: [remnux.python3-packages.autoit-ripper](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/autoit-ripper.sls)


## GootLoaderAutoJsDecode.py

Statically deobfuscate GootLoader (GOOTLOADER) malicious JScript to recover the payload and extract C2 domains.

**Website**: [https://github.com/mandiant/gootloader](https://github.com/mandiant/gootloader)\
**Author**: Mandiant: [https://github.com/mandiant](https://github.com/mandiant)\
**License**: Apache License 2.0: [https://github.com/mandiant/gootloader/blob/main/LICENSE.txt](https://github.com/mandiant/gootloader/blob/main/LICENSE.txt)\
**Notes**: gootloader-decode. Run `gootloader-decode malicious.js`; it writes DecodedJsPayload.js_ and FileAndTaskData.txt to the working directory and prints extracted domains. Only the safe static decoder is packaged; the repo's dynamic and manual scripts execute malware code and are intentionally excluded.\
**State File**: [remnux.scripts.gootloader](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/gootloader.sls)
