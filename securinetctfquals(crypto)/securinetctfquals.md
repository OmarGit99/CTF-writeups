# SECURINETS CTF QUALS 2019

The starting point of the CTF was a cipher.json file which consisted of 11 ciphertexts all encrypted using XOR using the same key

With this formulae we could derive the key from the hex ciphers given (Using a crib drag script)

text1 XOR key = encrypted1    (OR)    text1 XOR encrypted1 = key 
(AND)
text2 XOR key = encrypted2    (OR)    text2 XOR encrypted2 = key

Hence,

text1 XOR encrypted1 = text2 XOR encrypted2      (OR)     text1 XOR text2 = encrypted1 XOR encrypted2

Hence with XORing two ciphertexts we can find patterns between them using a method called "crib-dragging"

A bruteforce script(solution.py) to find patterns between similarly XOR encrypted is then used to decrypt the message and finally the key

Solved
