#forensics #steganography
![[Pasted image 20250610163536.png]]
![[Pasted image 20250610163548.png]]

---

This challenge was rather challenging and took me awhile (fortunately I was on the right path most of the time)
We are given a .jpg and little extra information
Given this, we can assume the challenge to be a steganography problem

### My Approach in Order
Due to the nature of steganography problems (which I tend to consider a strongsuit of mine) you tend to keep throwing techniques at it until it pops.  This is what I tried:
- Strings, head, less (looking for anything unusual)
- binwalk (only JFIF data), binwalk -e (nothing)
- steghide extract (no password)
- steghide extract with passwords: graph, nickelback, Nickelback, Cybergames, photograph
- Ran it through tools on [Aperisolve.com](https://www.aperisolve.com/) (Nothing visually or extracted there)
- Cropped out the image and aligned it in GIMP and reverse image searched, investigating related social medias
- zsteg, other random tools

At this point I was starting to run out of things I could think to do, so I decided to run a steghide brute forcer with a big wordlist... Just incase...
I found [[stegcracker]] and ran it on rockyou.txt, however this was VERY slow and was estimated to take 5 hours.  That's when I read the output of the tool: 

![[Pasted image 20250610164614.png]]

Stegcracker was retired for StegSeek, a tool that claimed it could run through rockyou.txt in 2 seconds.  So I looked up how to install it and then ran StegSeek on rockyou.txt.
It hit almost instantly:
![[Pasted image 20250610164738.png]]
Opening the .out image we find our flag
![[Pasted image 20250610164819.png]]

Flag: `SVUSCG{l00k_4t_th1s_gr44444444444ph}`