<h3 align="center">Ugly duckling (forensics) writeup</h3>

The problem gives us a binary file to work with.. which after binwalk, xxd, and multiple analyzing tools doesn't seem to decode or crack open.
Looking back at the challenge's description we can gather that the infected USB was, in fact a Rubber Ducky.

So we can assume the binary file must be the injected and encoded malware, hence we can search online for a tool to decode rubber ducky binary files. Fortunately for us there are multiple...

After decoding the binary file we get 3 possible paths, first of which is an image, however running steg and metadata would not produce any results.
The second path might be a seeming local file.. however since we are not on the victim's machine the local image is not available.

Which leave us with the final clue which looks like base64 encoding... Cracking it gives a link to install an exe file.

Downloading and running the exe file gives the flag!

