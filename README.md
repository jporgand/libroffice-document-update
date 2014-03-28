Libreoffice Document Update
===========================
This is just a dumb little macro designed to update the indexes (TOC, page numbering, etc.) of a libreoffice document from the commandline - good for fixing up documents if you've been hacking around in the XML. It will run the "update all indexes" command, save the document then close libreoffice.

Installation
------------
Document bound macros can't be invoked from the commandline, so you need to set up this macro into your libreoffice install. Copy the files into $libreoffice/share/basic/UpdateDocument (or wherever you want, but you will need to update the paths below).

Modify $libreoffice/share/basic/script.xlc with the following line:
```
<library:library library:name="TEST" xlink:href="$(INST)/share/basic/UpdateDocument/script.xlb/" xlink:type="simple" library:link="true" library:readonly="false"/>
```
Modify $libreoffice/share/basic/dialog.xlc with the following line:
```
<library:library library:name="TEST" xlink:href="$(INST)/share/basic/UpdateDocument/dialog.xlb/" xlink:type="simple" library:link="true" library:readonly="false"/>
```
Execution
---------
Invoke Libreoffice headlessly & call the macro on your document like so:
```
swriter --headless --norestore "macro:///TEST.UpdateDocument.updateindexesandsave" document
```
Licence
-------
Public Domain - do with it what you will.