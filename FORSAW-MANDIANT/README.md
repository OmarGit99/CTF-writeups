# FORSAW-MANDIANT-CTF

I ended up with a Mandiant pdf file... the file was strange and some person told me there was a flag in it.. somehow?? 
Looking at it, it just looked like an ordinary ole pdf file with a bunch of words too smart for me.

Now since this was forensics, it had to do something with the structure of the PDF file a.k.a headers footers magic bits etc


For that there were a few options, first of which was pdf-parser by adleid 
Although for some reasons I ended up downloading it in the wrong place and couldn't execute the python command on it
/bin/python3 was not executable or reachable.

Next option was qpdf, a lightweight pdf tool with minimal dependencies..... perfect!

`$ qpdf --qdf --object-streams=disable Mandiant.pdf out.pdf`

Now I said, "Fine, done. Let's `cat` the out"

Then I had to scroll through 200000 lines of gibberish to find something weird
😶  200000

Fortunately base64 text was easily recognizable on line 195000 or so...
Using vim to clear out the rest of the file and saving it, I then had to get rid of all the pesky '\n' s

cat then `tr -d '\n'` pow  `tr -d '\n'` pow

base64 and --decode to decode(duh) the output
annddd file command................ A PNG. It's a fossil meme from the Jurassic period but eh, whatever

Binwalk... binwalk... binwalk :/
At first I thought all had to do was `sudo apt get` it,
but then due to weird dependency issues and missing file types i got a very weird binary description of the PDF

After a day I realized that I had installed the tool without all it's dependencies.. followed the steps on the official GitHub repo anndd I got something when I ran it and extracted using -e flag which outputted a zlib file

Ran binwalk again

A 7ZIP FILE was hidden within the zlib!
the whole 7z file was stored header to footer within the zlib outputstream
So...  now we had to perform a surgery in order to extract it... "Nurse pass the scalpel"

The scalpel tool is used to extract specific file types from a file by detecting headers, magic numbers and footers of a file type that helps to uniquely identify it !!
Damn cool but uh why was I getting this error??? thonk... something something scalpel.conf file

I wen and open up the scalpel conf file in vim editor and see a bunch of filetypes along with their hex headers.. maybe to help scalpel detect a file type..
Tried searching for 7zip(cause binwalk detected it)... nope. So do I have to add it? Luckily for everyone theres a identifying line for almost any file type on https://asecuritysite.com/scalpel.conf.txt 

Copied out the 7zip line.. pasted, saved and ran it again after clearing the rest of the folder. Have to sterilise before a surgery right?

Got a secret.txt file which on cat'ing it seems to be another base64 
so I trimmed the newlines and decoded it.
A jpeg prehistoric meme great

Lets try binwalk on it... nothing, maybe xxd?
There are some weird Base64-like strings but we cant do anything with them

The CTF owners then landed a hint about free file software which could only be run on Windows. So I installed it and de camouflauged it... 
Running `file` on the output gave out and ELF executable file 
So chmod 421 the permissions on the file and run it

Bingo! The flag




