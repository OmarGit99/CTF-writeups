# CSAW-CTF-205(NETWORKING)

For this CTF we started with a pcap file which is basically packets captured over a networking for a period of time

We can go two ways with this CTF:
1) Open wireshark and search through the packets for anything with a string "flag" in it using the `contains` keyword
2) Use `strings` command on the pcap file and grep through it for anything with a flag in it

Either way you will find a packet which you can analyse and follow the TCP stream to a .py file

The py file contains the encoding functions which you must reverse engineer to get the flag.
