#INSOMNI-HACK-CTF2015 (FORENSICS)

Another forensics CTF...

The first clue is an image.. specifically https://raw.githubusercontent.com/ctfs/write-ups-2015/master/insomni-hack-ctf-2015/forensic/zoom-in/zoomIn_3a3f6e35934021eca75b0abde70333a6.jpg
So the first thing we do is use wget to download it
Then let's run all our basic tools on it.

Its an image so we can:
<li> Check it's metadata </li>
<li> Use binwalk(or a hexeditor) to go through it's hexdump for multiple headers </li>
  
Depending on which path you choose

<li> You check it's metadata.. find a thumbnail embedded and extract it using `exiftool -binary -ThumbnailImage` and redirecting the STDOUT to another jpg file. This file will in turn consist of ANOTHER thumbnail which can be extracted the same way </li>
<li> Using binwalk and scalpel you can extract the files by uncommenting and adding the filetypes into the scalpel configuration file</li>

Either way you'll end up with a mirrored image which you can flip using imagemagick convert and -flop

What you are looking at will be the final flag : D
