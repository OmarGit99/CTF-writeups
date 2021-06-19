# DEFCON 2018 DIGITAL FORENSICS 100 QUALS CTF

Ok this was my third CTF walkthrough and this is how it went

The initial file was http://stalkr.net/files/defcon/2010/quals/forensics100/f100_6db079ca91c4860f.bin.gz
so I ran `wget` and `gzip -d` on it

Once extracted from the gzip file I could clearly see a binary file for the taking. Running `file` on it gave the output that it was a bootable file
`with 1 partition`

THE MOST EFFECTIVE TOOL in this was SLEUTH-KIT and AUTOPSY

When I ran `mmls` I could finally see all the partitions in the boot media along with their start values, end values and length

I could now extract these partitions as seperate files using the `dd` command with the arguments, input file, output file, starting address value and count up till the partition
Doing this individually for each of the partitions gave four files

Now I had to search all for the key.

When I scalpel on some of the files, it brough images which were all red herrings and dead ends. So I decided to use another tool to dive deeper and search the partitions

Finding deleted files using Autopsy was a popular way so I considered using it... However ended up with the wrong version and found a blank metadata table

Using the correct version and way of Autopsy(sudo apt-get autopsy and then running it from terminal on your localhost) had a feature of analyzing MTFs

# What are MFTs and NTFS

"NT file system (NTFS), which is also sometimes called the New Technology File System, is a process that the Windows NT operating system uses for storing, organizing, and finding files on a hard disk efficiently. .."
So basically a way all the files and directories are stored on the hard drive

What interface I was looking at on Autopsy was a simplified way of seeing all the files on the hard drive(deleted or not)

An MFT is a master file table which stores indexes(?) of files on the NTFS
"Each file on an NTFS volume is represented by a record in a special file called the master file table (MFT). NTFS reserves the first 16 records of the table for special information."

Exploring around on the NTFS of partition 2 would lead to finding a key.jpg file which unfortunately was removed :(
But wait! You can retrieve deleted data from autopsy if the file wasnt overriden in the memory right?

So what I did was find the addresses from the data cluster in the $MFT file and went through all of them...

One that caught my eye was a file with the vague text in it saying: THE.KEY.WAS.NOT.DELETED NEVER EXISTED

Thus the truth was found!


