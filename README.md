#PDF Analysis

>Several PDF analysis has already been done, I reassembled a lot of them with additional tips & tools here


- [PDF format](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#pdf-format-page_facing_up)<br />
- [Tools list](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#tools-list-wrench)<br />
- [Quick Analysis](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#quick-analysis-rocket)<br />
- [Complete Analysis](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#complete-analysis-mag_right)<br />
	- [Basic informations](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#basic-informations-1)<br />
	- [Metadata](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#metadata)<br />
	- [Search for older version](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#search-for-older-versions)<br />
	- [Online Analysis](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#online-analysis-1)<br />
	- [Statistics](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#statistics)<br />
	- [Visual analysis](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#visual-analysis)<br />
	- [Go deeper in the analysis](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#go-deeper-in-the-analysis)<br />
	- [Displaying objects and actions structure](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#displaying-objects-and-actions-structure-1)<br />
	- [Map of the objects flows](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#map-of-the-objects-flows)<br />
	- [Actions](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#actions)<br />
	- [Compression](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#compression)<br />
	- [Embeded files](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#embeded-files)<br />
	- [Extract files / scripts / objects](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#extract-files--scripts--objects-1)<br />
	- [Conversions](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#conversion)<br />
	- [Encryption](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#encryption)<br />
	- [Javascript](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#javascript)<br />
	- [Flash](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#flash)<br />
- [Sources](https://github.com/zbetcheckin/PDF_analysis/blob/master/README.md#sources-information_source)<br />



<br />
## PDF Format :page_facing_up:

<p align="center">
  <img src="https://github.com/zbetcheckin/PDF_analysis/blob/master/pdf_ange_albertini.png" alt="alt text" width="580" height="403">
</p>



<br />
https://www.adobe.com/devnet/pdf/pdf_reference.html <br />
https://blog.didierstevens.com/2008/04/09/quickpost-about-the-physical-and-logical-structure-of-pdf-files/ <br />
https://web.archive.org/web/20141010035745/http://gnupdf.org/Introduction_to_PDF <br />
<br />


<br />
## Tools list :wrench:

Tool | URL
------------------------------------ | ---------------------------------------------
AnalyzePDF.py | https://github.com/hiddenillusion/AnalyzePDF
ByteForce | https://github.com/weaknetlabs/ByteForce
Caradoc | https://github.com/ANSSI-FR/caradoc
Didier Stevens suite | https://github.com/DidierStevens/DidierStevensSuite
dumppdf | https://packages.debian.org/jessie/python-pdfminer
forensics-all | https://packages.debian.org/jessie-backports/forensics-all
Origami | https://code.google.com/archive/p/origami-pdf/
ParanoiDF | https://github.com/patrickdw123/ParanoiDF
peepdf | https://github.com/jesparza/peepdf
PDF Xray | https://github.com/9b/pdfxray_public
pdf-parser | http://didierstevens.com/files/software/pdf-parser_V0_6_4.zip
pdf2jhon.py | https://github.com/magnumripper/JohnTheRipper/blob/unstable-jumbo/run/pdf2john.py
pdfcrack | https://packages.debian.org/jessie/pdfcrack
pdfextract | https://github.com/CrossRef/pdfextract
pdfobjflow.py | https://bitbucket.org/sebastiendamaye/pdfobjflow
pdfresurrect | https://packages.debian.org/jessie/pdfresurrect
PdfStreamDumper.exe | http://sandsprite.com/CodeStuff/PDFStreamDumper_Setup.exe
pdftk | https://packages.debian.org/en/jessie/pdftk
pdfxray_lite.py | https://github.com/9b/pdfxray_lite
poppler-utils | https://packages.debian.org/en/jessie/poppler-utils (pdftotext, pdfimages, pdftohtml, pdftops, pdfinfo, pdffonts, pdfdetach, pdfseparate, pdfsig, pdftocairo, pdftoppm, pdfunite)
pyew | https://packages.debian.org/en/jessie/pyew
qpdf | https://packages.debian.org/jessie/qpdf
swf_mastah.py | https://github.com/9b/pdfxray_public/blob/master/builder/swf_mastah.py


#### Existing list
http://blog.didierstevens.com/programs/pdf-tools/ <br />
https://github.com/sans-dfir/sift-files/tree/master/pdf-tools



<br />
<br />
## Quick Analysis :rocket:


####Basic informations
```
$ file file.pdf
$ pdfinfo -box -meta -js -rawdates file.pdf
```


####Displaying objects and actions structure 
```
$ python pdfdid.py -aefv file.pdf
```


####Search for /OpenAction /AA /Launch /GoTo /GoToR /SubmitForm /Richmedia (for Flash) /JS /JavaScript /URI - Encode - Cipher - Shell code - Obfuscation...
Automatically with ParanoiDF
```
$ python paranoiDF.py -fl file.pdf
```
Or with pdf-parser
```
$ python pdf-parser.py -v file.pdf
```
With an hexadecimal analyser
```
$ bless file.pdf
```


####Extract files / scripts / Objects
pdf-parser to extract a js object for example
```
$ pdf-parser --object 32 --raw > extractedObject.js
```
pdfextract from Origami
```
$ pdfextract file.pdf
```


####Online analysis<br />
*Beware to don't leak any important/professional/personnal data or to expose your research*<br />
https://www.hybrid-analysis.com/










<br />
<br />
## Complete Analysis :mag_right:



### Basic informations
```
$ file file.pdf
$ pdfinfo file.pdf
$ pdfinfo -box -meta -js -rawdates file.pdf
```


### Powerfull Python tool to analyze PDF and exploit
```
$ pyew file.pdf 	
```


### Other Python tool to explore PDF
```
$ peepdf -fl file.pdf
$ peepdf --interactive file.pdf
```


#### Analysis under Windows
PDF Stream Dumper<br />
https://github.com/dzzie/pdfstreamdumper



### Metadata
Get metadata
```
$ exiftool -a -u -g2 file.pdf
```

Get metadata recursivly from current directory
```
$ exiftool -r -ext pdf .
```

Change an element
```
$ exiftool -Title="New title" file.pdf
```

3 ways to remove metadata
```
$ mat file.pdf
$ exiftool -all= file.pdf
$ exiftool -all:all= file.pdf
```



### Search for older versions
Search for older "hidden" versions
```
$ pdfresurrect file.pdf -i
```


### Online Analysis 
Name | URL
------------------------------------ | ---------------------------------------------
Malwr | https://malwr.com/submission/
Hybrid analysis | https://www.hybrid-analysis.com/
Malware Tracker | https://www.malwaretracker.com/pdf.php
VirusTotal | http://www.virustotal.com/
PDF examiner | http://www.pdfexaminer.com/
Document Analyzer | http://www.document-analyzer.net/
Jotti | https://virusscan.jotti.org/
PDF X-ray | http://www.pdfxray.com/
PDF Online | https://www.pdf-online.com/
Extract PDF | http://www.extractpdf.com
Char conversion | https://kt.pe/tools.html#conv/




### Statistics 
Calcul byte statistics, entropy min and max, ASCII count, ... from a PDF
```
$ python byte-stats.py file.pdf
```



### Visual analysis
Visual analysis of a PDF or a binary file<br />
http://binvis.io


<br />
## Go deeper in the analysis

### Displaying objects and actions structure 
```
$ python pdfid.py --all --extra --force --verbose file.pdf
```

### Map of the objects flows
```
$ pdf-parser file.pdf | ./pdfobjflow
$ eog pdfobjflow.png
```


### Actions
Search for : <br />
/OpenAction /AA specifies the script or action to run automatically.<br />
/Names /AcroForm /Action can also specify and launch scripts or actions.<br />
/JavaScript specifies JavaScript to run.<br />
/GoTo changes the view to a specified destination within the PDF or in another PDF file.<br />
/Launch a program or opens a document.<br />
/URI accesses a resource by its URL.<br />
/SubmitForm /GoToR can send data to URL.<br />
/RichMedia can be used to embed Flash in PDF.<br />
/ObjStm can hide objects inside an Object Stream.<br />
/JavaScript > /J#61vaScript Beware on obfuscation technique with hex codes


With ParanoiDF
```
$ python paranoiDF.py -fl file.pdf
```
With pdf-parser
```
$ python pdf-parser.py -v file.pdf
```
With an hexadecimal analyser
```
$ bless file.pdf
```
With dumppdf
```
$ dumppdf -a file.pdf
```







### Compression
Search for compression
```
$ strings file.pdf | grep --color "/Filter"
```

2 ways to decompress a PDF
```
$ pdftk compressed.pdf output uncompressed.pdf uncompress
$ qpdf --stream-data=uncompress compressed.pdf uncompressed.pdf 
```



### Embeded files
4 ways to search for embeded files/scripts inside a PDF
```
$ binwalk file.pdf
$ foremost -a -v file.pdf
$ hachoir-subfile file.pdf
$ scalpel file.pdf
```


### Extract files / scripts / objects
Extract file corresponding to object ID, jpg for example
```
$ dumppdf.py -i 32 -r file.pdf > image.jpg
```
Extract js from an object for example
```
$ pdf-parser --object 32 --raw > extractedObject.js
```
pdfextract from Origami
```
$ pdfextract file.pdf
```



### Conversion
PDF to Postscript
```
$ pdftops file.pdf
```
PDF to TXT
```
$ pdftotext file.pdf
```
PDF to JPG
```
$ convert file.pdf image.jpg
```
Non-exhaustive list of possible conversion 




### LZWDecode filter
Convert a PDF to Postscript without the LZWDecode filter
```
$ qpdf --stream-data=uncompress original.pdf decoded.pdf # Decompress it
$ pdftops decoded.pdf decoded.ps # Convert it
```


### Encryption
PDF supports RC4 encryption (40 to 128 bits keys) and AES (128 to 256 with the Extension Level 3). <br />
Beware with empty password.


#### Password recovering
Brute force a PDF with pdfcrack
```
$ pdfcrack -w yourDictionnary.txt file.pdf
```
With john
```
$ pdf2john.py file.pdf > x.hash
$ john --wordlist=yourDictionnary.txt x.hash
```













### Javascript

2 ways to search for Javascript
```
$ pdf-parser --search=JavaScript file.pdf 
$ pdfinfo -js file.pdf
```


Extract an object
With jsunpack
```
$ jsunpack-extractjs file.pdf
```
With pdf-parser
```
$ pdf-parser --object 32 --raw file.pdf > file.js
```
With pdfextract from Origami
```
$ pdfextract --js file.pdf
```


#### De-obfuscate
https://github.com/urule99/jsunpack-n <br />

Online :<br />
http://jsunpack.jeek.org/java/ <br />

Malzilla and SpiderMonkey can also help deobfuscate JavaScript.<br />
Malzilla : <br />
http://www.malzilla.org/downloads.html <br />
SpiderMonkey : <br />
http://www.didierstevens.com/files/software/js-1.7.0-mod.tar.gz <br />
More details coming soon.




#### Add Javascript to PDF
https://didierstevens.com/files/software/make-pdf_V0_1_6.zip <br />
https://neonprimetime.blogspot.fr/2015/03/how-to-add-javascript-to-pdf.html <br />



#### Disarming a PDF
```
$ python pdfid.py --disarm file.pdf
```




### Flash

Search for flash
```
$ python pdf-parser.py --search flash file.pdf
```

Extract flash with swf_mastah
```
$ python swf_mastah.py -f file.pdf -o ./
$ file *.swf
```
With pdf-parser
```
$ pdf-parser.py --object 32 --filter --raw file.pdf > flashFile.swf
$ file flashFile.swf
```

Analysing flash program
```
$ swfdump -Ddu flashFile.swf > flashFile.txt
```
More details coming soon.








<br />
## Sources :information_source:

https://blog.didierstevens.com/category/pdf/ <br />
http://www.decalage.info/file_formats_security/pdf <br />
https://zeltser.com/analyzing-malicious-documents/ <br />
https://code.google.com/archive/p/corkami/wikis/PDFTricks.wiki <br />
https://www.sans.org/reading-room/whitepapers/malicious/owned-malicious-pdf-analysis-33443 <br />
https://digital-forensics.sans.org/blog/2009/12/14/pdf-malware-analysis/ <br />
http://fileformats.archiveteam.org/wiki/PDF <br />

