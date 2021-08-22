<h3 align="center"> FIND THE CAT (FORENSICS CTF) WRITEUP </h3>

For this CTF we must find the location(city) where the perpetrators have kidnapped the cat

We start with a gzip file we must check the integrity with an md5sum hash

Once done we can extract the data file from gzip compression
Now we can use foremost software to extract the data from the data dump

we can go through analyzing each image's metadata etc but you will eventually find gps coodinates in a zip compressed

now reverse search the gps data and you will find the city in France!







