# hack-lu-ctf-2011 Cryptography

The starting point is a txt file which apparently contains base64 text

Once we decode it, we get a binary file which is locked with xor encryption according to the the ctf intro.

In order to bruteforce it to find the key we use the tool, xortool

Using xortool on the binary file reveals the length of the key 16
however since the tool limits itself upto 32 bit only, we should use the flag -m to change the max bit-value to 257

Now the length is shown to be 64-bit, so we can bruteforce it using `xortool -c 20 -m 257 output.bin`

and voila it works so we can assume the key outputted was the flag
