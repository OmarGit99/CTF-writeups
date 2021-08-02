# FORENSIC COMMAND AND CONTROL 2 - VOLATILITY TOOL

For this challenge we get a volatile memory dump compressed in the form of tbz2

So first we need to extract the .dmp file by using the command `tar -xf`

Now install the tool volatility and find out the profile of the dmp file using the plugins imageinfo and kdbgscan

Once you find out the profile run basic plugins to find anything interesting...
At first since the challenge mentioned "hostname", I figured I should check `netscan` to see all the established connections

When i found the listening and host IPs in netscan i decided to resolve them one by one using reverse DNS lookup
None of them worked...

Now doing a bit of google, we find a value `COMPUTERNAME` which fits our description, now we need to search for it in the registries/hives

use hivescan and hivelist with the --profile and -f flags set 

Now worst case we would have to go through all the hives, however lets start with the most likely hive with computername

running `hivedump -o` with the virtual offset of the System hive and *maybe* grep it with `COMPUTERNAME`
If you search through the entire list you will find `\ControlSet001\Control\ComputerName\ComputerName`

Now all you have to do is printkey -K it to find the computer name!

*Red Herring*

Using hashdump will give you a couple of users and passwords however they dont do anything to solve the challenge
