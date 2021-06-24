# FOR250 CSAW QUALS 2016 WATCHWORD CTF

The starting point for this CTF was an mp4 video called powpow.mp4

Using exiftool gives us 2 clues leading to steghide 
<li> The author name</li>
<li> base64 text in the title</li>

binwalk/scalpel/foremost on the mp4 leads to an image

Of course running steghide on this file leads to nothing because it's a .png file

Running stegsolve however shows us that a file is really hidden in it and the hexdump further proves that
Using the .py script I included in this repo creates a steghide-able .jpeg

Steghide requires a password that you can pipe from a bruteforcer 
Once done you will find a BASE64 text...
except it's not
but a BASE85 text
`W^7?+dsk&3VRB_4W^-?2X=QYIEFgDfAYpQ4AZBT9VQg%9AZBu9Wh@|fWgua4Wgup0ZeeU}c_3kTVQXa}eE` 

decoding that finally gives us the flag
