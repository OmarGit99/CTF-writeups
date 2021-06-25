# PRAGYAN CTF 2015  FORENSICS/STEGANOGRAPHY

The initial file is a jpeg on which if we run exiftool we dont get anything valuable
Binwalk tool reveals a hex header of a zip file which we can then extract using flag -e

Unzipping the file reveals an ASCII file called usethis which reads a steghide link

This is a clue that we must run steghide on the original image

However there is a PASSPHRASE!

You can either bruteforce it or search for it

I went through the hexdump of the image and found an odd text at the bottom
`Delta_Force\m/`

Looking obviously like the passphrase i added(tried without \m/ few times first lol) it.

The output was saved to a key file which when read gave the key!
