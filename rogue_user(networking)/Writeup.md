<h3> NETWORKING ANALYSIS... FINDING A ROGUE USER </h3>

Starting with a packet capture file which I opened in wireshark..
you can go two ways about it

-) Add a stream index column with type custom and field tcp.strean
-) Use the filter `tcp contains user` (because we are searching for users)

Either way you should analyze and follow a couple of packets before you see a conversation of a seemingly remote shell access

If you follow the commands you will see that some user who adduser Marcelle has root access (was able to cat /etc/shadow)

Hence we found the rogue user
