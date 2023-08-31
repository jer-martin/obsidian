![[Pasted image 20230826101137.png]]

I used nvim to create a file called "somefile.txt". I then used gzip to compress the file, and gunzip to decompress it, leaving me with the original file.

![[Pasted image 20230826101338.png]]

I created "other.txt." I then used "tar -cvf myfiles.tar somefile.txt other.txt" to compress both of these files into "myfiles.tar."

![[Pasted image 20230826102554.png]]

I used nvim to create somefile2.txt. I then used "tar -zcvf foo2.tar.gz other.txt somefile.txt somefile2.txt" to create "foo2.tar.gz" which contains the three text files.

![[Pasted image 20230826102753.png]]

I then extracted the compressed file using "tar -xzvf foo2.tar.gz." This gave me the three original text files.

![[Pasted image 20230826102853.png]]

Next part of the assignment. I cd'ed into /home/reptilian and then used mkdir to create the name directory.

I then navigated back to the reptilian kernel source and ran grep -lr to find the phrase "android_dev." I did the arguments -lr so that it would just show me file names rather than the actual lines where the phrase was used. This took a little while.

For clarity's sake, the screenshot contains both -r and -lr for step (2).

![[Pasted image 20230826103347.png]]

Next, I piped the output into a file called "ex1.txt." There's a screenshot of the ls listing and the file itself in nvim.

![[Pasted image 20230826103420.png]]

![[Pasted image 20230826103446.png]]

