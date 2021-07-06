# CTFLEARN CRYPTO CHALLENGE 120 (CRYPTOGRAPHY)

RSA encryption works with a private key and a public key on both sides of a communication

They both consist of public key - (n,e) and private key(n,d)

n is the modulus, e is the public exponent and d is the private exponent


let p and q be the numbers that when multiplied equals to n (pq = n)

Let the message to be encrypted be m and encrypted message be c

(m**e)**d ≡ m * (mod n)

AND

c = m**e mod n


Also we can use RSActftool to decrypt using the given values

The values given in this problem were:
e(public exponent): 1
c(ciphertext):9327565722767258308650643213344542404592011161659991421
n(modulus): 245841236512478852752909734912575581815967630033049838269083

using it with the tool we get the output:
b3tter_up_y0ur_e

which on entering gives us the correct result
